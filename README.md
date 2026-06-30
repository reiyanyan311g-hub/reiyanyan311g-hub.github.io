<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>駒澤大学 eスポーツサークル | KOMAZAWA ESPORTS</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+New:wght@400;500;700;900&family=Rajdhani:wght@500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#0B0E14;
    --panel:#141925;
    --panel-2:#1B2230;
    --line:#262F42;
    --crimson:#FF3358;
    --crimson-dim:#7A1B2E;
    --cyan:#4FD8E0;
    --paper:#EDEFF4;
    --muted:#8993A8;

    --font-jp: 'Zen Kaku Gothic New', sans-serif;
    --font-en: 'Rajdhani', sans-serif;
    --font-mono: 'JetBrains Mono', monospace;
  }

  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}

  body{
    background:var(--ink);
    color:var(--paper);
    font-family:var(--font-jp);
    line-height:1.7;
    overflow-x:hidden;
  }

  ::selection{background:var(--crimson);color:var(--ink);}

  a{color:inherit;text-decoration:none;}
  ul{list-style:none;}
  img{max-width:100%;display:block;}

  .eyebrow{
    font-family:var(--font-mono);
    font-size:.75rem;
    letter-spacing:.18em;
    color:var(--cyan);
    text-transform:uppercase;
    display:flex;
    align-items:center;
    gap:.6em;
  }
  .eyebrow::before{
    content:"";
    width:18px;height:2px;
    background:var(--cyan);
    display:inline-block;
  }

  .section-title{
    font-family:var(--font-jp);
    font-weight:900;
    font-size:clamp(1.8rem,4vw,2.6rem);
    margin:.4em 0 .3em;
    letter-spacing:.02em;
  }
  .section-sub{
    color:var(--muted);
    font-size:.95rem;
    max-width:46ch;
    margin-bottom:2.4rem;
  }

  .wrap{
    max-width:1120px;
    margin:0 auto;
    padding:0 6vw;
  }

  /* ---------- Visible focus ---------- */
  a:focus-visible,button:focus-visible,input:focus-visible,textarea:focus-visible,summary:focus-visible{
    outline:2px solid var(--cyan);
    outline-offset:3px;
  }

  /* ===================== HEADER ===================== */
  header{
    position:fixed;
    top:0;left:0;right:0;
    z-index:200;
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:1.1rem 6vw;
    background:rgba(11,14,20,.7);
    backdrop-filter:blur(10px);
    border-bottom:1px solid var(--line);
  }

  .brand{
    display:flex;
    align-items:center;
    gap:.7rem;
  }
  .brand-mark{
    width:34px;height:34px;
    background:var(--crimson);
    clip-path:polygon(0 0,100% 0,82% 100%,0% 100%);
    display:flex;align-items:center;justify-content:center;
    font-family:var(--font-en);
    font-weight:700;
    color:var(--ink);
    font-size:.95rem;
  }
  .brand-text{
    display:flex;
    flex-direction:column;
    line-height:1.15;
  }
  .brand-text .jp{
    font-weight:900;
    font-size:1.05rem;
    letter-spacing:.02em;
  }
  .brand-text .en{
    font-family:var(--font-en);
    font-size:.68rem;
    letter-spacing:.22em;
    color:var(--muted);
  }

  /* hamburger */
  .burger{
    position:relative;
    width:42px;height:42px;
    background:transparent;
    border:1px solid var(--line);
    clip-path:polygon(0 0,100% 0,100% 80%,80% 100%,0 100%);
    cursor:pointer;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    gap:6px;
    z-index:300;
  }
  .burger span{
    width:20px;height:2px;
    background:var(--paper);
    transition:transform .35s ease, opacity .25s ease, background .25s ease;
  }
  .burger[aria-expanded="true"] span{background:var(--paper);}
  .burger[aria-expanded="true"] span:nth-child(1){transform:translateY(8px) rotate(45deg);}
  .burger[aria-expanded="true"] span:nth-child(2){opacity:0;}
  .burger[aria-expanded="true"] span:nth-child(3){transform:translateY(-8px) rotate(-45deg);}

  /* nav panel */
  .nav-panel{
    position:fixed;
    top:0;right:0;
    height:100vh;
    width:min(78vw,360px);
    background:linear-gradient(160deg,var(--panel) 0%,var(--ink) 100%);
    border-left:1px solid var(--line);
    clip-path:polygon(14% 0,100% 0,100% 100%,0 100%);
    transform:translateX(100%);
    transition:transform .5s cubic-bezier(.22,.85,.32,1);
    z-index:250;
    display:flex;
    flex-direction:column;
    justify-content:center;
    padding:0 12vw 0 16vw;
  }
  .nav-panel.open{transform:translateX(0);}

  .nav-panel ol{
    list-style:none;
    display:flex;
    flex-direction:column;
    gap:1.6rem;
    counter-reset:navnum;
  }
  .nav-panel li{
    counter-increment:navnum;
    opacity:0;
    transform:translateX(24px);
    transition:opacity .45s ease, transform .45s ease;
  }
  .nav-panel.open li{opacity:1;transform:translateX(0);}
  .nav-panel.open li:nth-child(1){transition-delay:.12s;}
  .nav-panel.open li:nth-child(2){transition-delay:.19s;}
  .nav-panel.open li:nth-child(3){transition-delay:.26s;}
  .nav-panel.open li:nth-child(4){transition-delay:.33s;}

  .nav-panel a{
    font-family:var(--font-en);
    font-weight:700;
    font-size:1.5rem;
    letter-spacing:.02em;
    display:flex;
    align-items:baseline;
    gap:.7rem;
    color:var(--paper);
    transition:color .2s ease;
  }
  .nav-panel a .jp-label{
    font-family:var(--font-jp);
    font-weight:700;
    font-size:.95rem;
    color:var(--muted);
  }
  .nav-panel a::before{
    content:counter(navnum,decimal-leading-zero);
    font-family:var(--font-mono);
    font-size:.75rem;
    color:var(--crimson);
  }
  .nav-panel a:hover{color:var(--cyan);}

  .nav-overlay{
    position:fixed;inset:0;
    background:rgba(0,0,0,.5);
    z-index:240;
    opacity:0;
    pointer-events:none;
    transition:opacity .4s ease;
  }
  .nav-overlay.open{opacity:1;pointer-events:auto;}

  /* ===================== HERO ===================== */
  .hero{
    position:relative;
    min-height:100vh;
    display:flex;
    align-items:center;
    padding:7rem 6vw 4rem;
    overflow:hidden;
  }
  .hero::before{
    content:"";
    position:absolute;
    top:0;right:-10%;
    width:60%;height:140%;
    background:linear-gradient(135deg,var(--crimson-dim) 0%,transparent 60%);
    clip-path:polygon(30% 0,100% 0,70% 100%,0% 100%);
    opacity:.55;
    z-index:0;
  }
  .hero::after{
    content:"";
    position:absolute;
    bottom:-20%;left:-10%;
    width:45%;height:80%;
    background:radial-gradient(circle,var(--cyan) 0%,transparent 70%);
    opacity:.08;
    z-index:0;
  }
  .hero-inner{
    position:relative;
    z-index:1;
    width:100%;
    display:grid;
    grid-template-columns:1.3fr .9fr;
    gap:3rem;
    align-items:end;
  }
  .hero h1{
    font-family:var(--font-jp);
    font-weight:900;
    font-size:clamp(2.2rem,6vw,4rem);
    line-height:1.25;
    margin:.6rem 0 1.2rem;
  }
  .hero h1 .accent{color:var(--crimson);}
  .hero p{
    color:var(--muted);
    max-width:48ch;
    margin-bottom:2rem;
    font-size:1.02rem;
  }

  .cta-row{display:flex;gap:1rem;flex-wrap:wrap;}
  .btn{
    font-family:var(--font-en);
    font-weight:700;
    font-size:.95rem;
    letter-spacing:.04em;
    padding:.95rem 1.8rem;
    display:inline-flex;
    align-items:center;
    gap:.6rem;
    cursor:pointer;
    border:none;
    transition:transform .25s ease, background .25s ease, color .25s ease;
  }
  .btn-primary{
    background:var(--crimson);
    color:var(--ink);
    clip-path:polygon(0 0,100% 0,90% 100%,0 100%);
  }
  .btn-primary:hover{transform:translateY(-2px);}
  .btn-ghost{
    background:transparent;
    color:var(--paper);
    border:1px solid var(--line);
    clip-path:polygon(0 0,100% 0,90% 100%,0 100%);
  }
  .btn-ghost:hover{border-color:var(--cyan);color:var(--cyan);}

  .scoreboard{
    border:1px solid var(--line);
    background:rgba(20,25,37,.6);
    backdrop-filter:blur(6px);
    padding:1.6rem;
    clip-path:polygon(0 0,100% 0,100% 90%,92% 100%,0 100%);
  }
  .scoreboard .row{
    display:flex;
    justify-content:space-between;
    align-items:baseline;
    padding:.65rem 0;
    border-bottom:1px solid var(--line);
  }
  .scoreboard .row:last-child{border-bottom:none;}
  .scoreboard .label{
    font-family:var(--font-mono);
    font-size:.72rem;
    letter-spacing:.1em;
    color:var(--muted);
    text-transform:uppercase;
  }
  .scoreboard .value{
    font-family:var(--font-en);
    font-weight:700;
    font-size:1.6rem;
    color:var(--paper);
  }
  .scoreboard .value span{color:var(--cyan);font-size:1rem;margin-left:.3em;}

  /* ===================== SECTIONS GENERIC ===================== */
  section{
    padding:6.5rem 0;
    position:relative;
    border-top:1px solid var(--line);
  }

  /* ---- about ---- */
  .about-grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:3rem;
    align-items:start;
  }
  .about-grid p{color:var(--muted);margin-bottom:1.1rem;}
  .stat-strip{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:1px;
    background:var(--line);
    border:1px solid var(--line);
    margin-top:1rem;
  }
  .stat-strip div{
    background:var(--panel);
    padding:1.4rem 1rem;
    text-align:center;
  }
  .stat-strip .num{
    font-family:var(--font-en);
    font-weight:700;
    font-size:1.8rem;
    color:var(--crimson);
  }
  .stat-strip .cap{
    font-family:var(--font-mono);
    font-size:.68rem;
    color:var(--muted);
    letter-spacing:.08em;
    margin-top:.3rem;
  }
  .activity-list{margin-top:1.5rem;}
  .activity-list li{
    display:flex;
    gap:1rem;
    padding:.9rem 0;
    border-bottom:1px solid var(--line);
    font-size:.92rem;
    color:var(--paper);
  }
  .activity-list li b{
    font-family:var(--font-mono);
    color:var(--cyan);
    font-weight:500;
    flex-shrink:0;
  }

  /* ---- games ---- */
  .game-grid{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:1.4rem;
  }
  .game-card{
    background:var(--panel);
    border:1px solid var(--line);
    padding:1.6rem 1.4rem 1.8rem;
    position:relative;
    clip-path:polygon(0 0,100% 0,100% 100%,8% 100%);
    transition:border-color .25s ease, transform .25s ease;
  }
  .game-card:hover{border-color:var(--crimson);transform:translateY(-4px);}
  .game-icon{
    width:44px;height:44px;
    border:1px solid var(--line);
    display:flex;align-items:center;justify-content:center;
    margin-bottom:1rem;
    color:var(--cyan);
  }
  .game-card h3{
    font-size:1.05rem;
    font-weight:700;
    margin-bottom:.4rem;
  }
  .game-card .genre{
    font-family:var(--font-mono);
    font-size:.68rem;
    color:var(--crimson);
    letter-spacing:.08em;
    text-transform:uppercase;
    margin-bottom:.7rem;
    display:block;
  }
  .game-card p{
    color:var(--muted);
    font-size:.86rem;
  }

  /* ---- QA ---- */
  .qa-list{max-width:760px;}
  .qa-item{
    border-bottom:1px solid var(--line);
  }
  .qa-q{
    width:100%;
    text-align:left;
    background:transparent;
    border:none;
    color:var(--paper);
    padding:1.4rem 0;
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:1rem;
    cursor:pointer;
    font-family:var(--font-jp);
    font-weight:700;
    font-size:1rem;
  }
  .qa-q .qmark{
    font-family:var(--font-en);
    color:var(--crimson);
    flex-shrink:0;
  }
  .qa-q .plus{
    font-family:var(--font-en);
    font-size:1.3rem;
    color:var(--muted);
    transition:transform .3s ease;
    flex-shrink:0;
  }
  .qa-item.open .plus{transform:rotate(45deg);color:var(--cyan);}
  .qa-a{
    max-height:0;
    overflow:hidden;
    transition:max-height .4s ease, padding .4s ease;
    color:var(--muted);
    font-size:.9rem;
  }
  .qa-item.open .qa-a{padding-bottom:1.4rem;}

  /* ---- contact ---- */
  .contact-grid{
    display:grid;
    grid-template-columns:.9fr 1.1fr;
    gap:3rem;
  }
  .contact-info .info-row{
    display:flex;
    gap:1rem;
    margin-bottom:1.4rem;
    align-items:flex-start;
  }
  .contact-info .info-row .ic{
    width:36px;height:36px;
    border:1px solid var(--line);
    flex-shrink:0;
    display:flex;align-items:center;justify-content:center;
    color:var(--cyan);
  }
  .contact-info .info-row .lab{
    font-family:var(--font-mono);
    font-size:.68rem;
    color:var(--muted);
    letter-spacing:.08em;
    text-transform:uppercase;
  }
  .contact-info .info-row .val{font-size:.95rem;margin-top:.15rem;}

  form{display:flex;flex-direction:column;gap:1.1rem;}
  .field label{
    font-family:var(--font-mono);
    font-size:.7rem;
    letter-spacing:.08em;
    color:var(--muted);
    text-transform:uppercase;
    display:block;
    margin-bottom:.45rem;
  }
  .field input,.field textarea{
    width:100%;
    background:var(--panel);
    border:1px solid var(--line);
    color:var(--paper);
    padding:.85rem 1rem;
    font-family:var(--font-jp);
    font-size:.92rem;
    transition:border-color .2s ease;
  }
  .field input:focus,.field textarea:focus{border-color:var(--cyan);outline:none;}
  .field textarea{resize:vertical;min-height:120px;}
  .field.error input,.field.error textarea{border-color:var(--crimson);}
  .field .err-msg{
    font-size:.75rem;
    color:var(--crimson);
    margin-top:.4rem;
    display:none;
  }
  .field.error .err-msg{display:block;}

  .submit-row{display:flex;align-items:center;gap:1rem;flex-wrap:wrap;}
  .form-note{
    font-family:var(--font-mono);
    font-size:.72rem;
    color:var(--muted);
  }
  .form-success{
    margin-top:1rem;
    padding:1rem 1.2rem;
    border:1px solid var(--cyan);
    color:var(--cyan);
    font-size:.85rem;
    display:none;
  }
  .form-success.show{display:block;}

  /* ---- footer ---- */
  footer{
    border-top:1px solid var(--line);
    padding:3rem 0 2rem;
  }
  .footer-row{
    display:flex;
    justify-content:space-between;
    align-items:center;
    flex-wrap:wrap;
    gap:1.5rem;
  }
  .footer-row .copy{
    font-family:var(--font-mono);
    font-size:.72rem;
    color:var(--muted);
  }
  .sns{display:flex;gap:.8rem;}
  .sns a{
    width:38px;height:38px;
    border:1px solid var(--line);
    display:flex;align-items:center;justify-content:center;
    color:var(--muted);
    transition:color .2s ease,border-color .2s ease;
  }
  .sns a:hover{color:var(--cyan);border-color:var(--cyan);}

  /* ===================== RESPONSIVE ===================== */
  @media (max-width:880px){
    .hero-inner{grid-template-columns:1fr;}
    .about-grid{grid-template-columns:1fr;}
    .game-grid{grid-template-columns:repeat(2,1fr);}
    .contact-grid{grid-template-columns:1fr;}
  }
  @media (max-width:560px){
    .game-grid{grid-template-columns:1fr;}
    .stat-strip{grid-template-columns:1fr;}
    .footer-row{flex-direction:column;align-items:flex-start;}
  }

  @media (prefers-reduced-motion: reduce){
    *{transition:none !important;animation:none !important;}
    html{scroll-behavior:auto;}
  }
</style>
</head>
<body>

<header>
  <div class="brand">
    <div class="brand-mark">KZ</div>
    <div class="brand-text">
      <span class="jp">駒澤大学eスポーツサークル</span>
      <span class="en">KOMAZAWA ESPORTS CIRCLE</span>
    </div>
  </div>
  <button class="burger" id="burgerBtn" aria-expanded="false" aria-controls="navPanel" aria-label="メニューを開く">
    <span></span><span></span><span></span>
  </button>
</header>

<div class="nav-overlay" id="navOverlay"></div>
<nav class="nav-panel" id="navPanel">
  <ol>
    <li><a href="#about" class="nav-link">ABOUT<span class="jp-label">サークル紹介</span></a></li>
    <li><a href="#games" class="nav-link">GAMES<span class="jp-label">ゲームタイトル</span></a></li>
    <li><a href="#qa" class="nav-link">Q&amp;A<span class="jp-label">よくある質問</span></a></li>
    <li><a href="#contact" class="nav-link">CONTACT<span class="jp-label">お問い合わせ</span></a></li>
  </ol>
</nav>

<!-- ===================== HERO ===================== -->
<section class="hero" style="border-top:none;">
  <div class="hero-inner wrap" style="padding:0;max-width:none;">
    <div>
      <span class="eyebrow">KOMAZAWA ESPORTS CIRCLE</span>
      <h1>勝ちにこだわる。<br>仲間と、<span class="accent">本気で。</span></h1>
      <p>駒澤大学公認のeスポーツサークルです。FPS、格闘ゲームなど多様なタイトルで、初心者から大会経験者まで一緒に練習・対戦しています。経験不問、見学も歓迎です。</p>
      <div class="cta-row">
        <a href="#contact" class="btn btn-primary">参加する →</a>
        <a href="#games" class="btn btn-ghost">対象タイトルを見る</a>
      </div>
    </div>
    <div class="scoreboard">
      <div class="row">
        <span class="label">Founded</span>
        <span class="value">2021<span>年</span></span>
      </div>
      <div class="row">
        <span class="label">Members</span>
        <span class="value">68<span>名</span></span>
      </div>
      <div class="row">
        <span class="label">Titles</span>
        <span class="value">06<span>タイトル</span></span>
      </div>
      <div class="row">
        <span class="label">Status</span>
        <span class="value" style="color:var(--cyan);font-size:1.1rem;">RECRUITING</span>
      </div>
    </div>
  </div>
</section>

<!-- ===================== ABOUT ===================== -->
<section id="about">
  <div class="wrap">
    <span class="eyebrow">About Us</span>
    <h2 class="section-title">サークル紹介</h2>
    <p class="section-sub">オンラインを中心にに活動する、競技志向と初心者歓迎が両立したeスポーツサークルです。</p>

    <div class="about-grid">
      <div>
        <p>2015年設立。eスポーツを通じて仲間を作り活動し、eスポーツの魅力を広め、互いに切磋琢磨しながら成長することを目的とする。普段の交流はオンラインで行っており、それぞれの生活スタイルに合わせて参加できます。
          また、スマブラ部門・格闘ゲーム部門は駒澤キャンパスでも活動しており、実際に集まって対戦や交流を行っています。
        </p>
        <div class="stat-strip">
          <div><div class="num">2015</div><div class="cap">Founded</div></div>
          <div><div class="num">100＋</div><div class="cap">MEMBERS</div></div>
          <div><div class="num">5</div><div class="cap">GAME TITLES</div></div>
        </div>
      </div>
      <div>
        <ul class="activity-list">
          <li><b>1</b>通常の練習・交流</li>
          <li><b>2</b>タイトルごとの部門活動</li>
          <li><b>3</b>オフ会・交流イベントの実施</li>
          <li><b>4</b>学内外の大会への出場</li>
      </div>
    </div>
  </div>
</section>

<!-- ===================== GAMES ===================== -->
<section id="games">
  <div class="wrap">
    <span class="eyebrow">Game Titles</span>
    <h2 class="section-title">ゲームタイトル</h2>
    <p class="section-sub">部員が主に活動している6タイトルです。掛け持ち参加も歓迎しています。</p>

    <div class="game-grid">
      <button class="game-card" type="button" data-game="valorant">
        <div class="game-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><path d="M4 12h16M12 4v16" stroke="currentColor" stroke-width="2"/></svg>
        </div>
        <span class="genre">FPS</span>
        <h3>VALORANT</h3>
        <p>5vs5のタクティカルFPS。学内大会の主力タイトルで、毎週チーム練習を実施。</p>
        <span class="card-more">詳細を見る <i>→</i></span>
      </button>
      <button class="game-card" type="button" data-game="apex">
        <div class="game-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="8" stroke="currentColor" stroke-width="2"/></svg>
        </div>
        <span class="genre">Battle Royale</span>
        <h3>Apex Legends</h3>
        <p>3人チームのバトルロイヤル。初心者向け講座から始めるメンバーが多数。</p>
        <span class="card-more">詳細を見る <i>→</i></span>
      </button>
      <button class="game-card" type="button" data-game="lol">
        <div class="game-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><path d="M3 12l9-9 9 9-9 9z" stroke="currentColor" stroke-width="2"/></svg>
        </div>
        <span class="genre">MOBA</span>
        <h3>League of Legends</h3>
        <p>5vs5のMOBA。ランク戦攻略から大会対策まで、レベル別に練習グループを分けています。</p>
        <span class="card-more">詳細を見る <i>→</i></span>
      </button>
      <button class="game-card" type="button" data-game="smash">
        <div class="game-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><rect x="4" y="4" width="16" height="16" stroke="currentColor" stroke-width="2"/></svg>
        </div>
        <span class="genre">Action</span>
        <h3>大乱闘スマッシュブラザーズSPECIAL</h3>
        <p>オフライン対戦会で特に人気。学内交流戦も毎学期開催しています。</p>
        <span class="card-more">詳細を見る <i>→</i></span>
      </button>
      <button class="game-card" type="button" data-game="splatoon">
        <div class="game-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><path d="M12 3v18M3 12h18" stroke="currentColor" stroke-width="2"/></svg>
        </div>
        <span class="genre">Shooter</span>
        <h3>スプラトゥーン3</h3>
        <p>初心者が一番多いタイトル。ワイワイ楽しく遊びたい人にもおすすめ。</p>
        <span class="card-more">詳細を見る <i>→</i></span>
      </button>
      <button class="game-card" type="button" data-game="sf6">
        <div class="game-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><path d="M5 5l14 14M19 5L5 19" stroke="currentColor" stroke-width="2"/></svg>
        </div>
        <span class="genre">Fighting</span>
        <h3>ストリートファイター6</h3>
        <p>格闘ゲーム勢が集うタイトル。個人戦が中心で、上位プレイヤーも在籍。</p>
        <span class="card-more">詳細を見る <i>→</i></span>
      </button>
    </div>
  </div>
</section>

<!-- ===================== GAME DETAIL MODAL ===================== -->
<div class="modal-overlay" id="gameModalOverlay">
  <div class="modal" id="gameModal" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
    <button class="modal-close" id="modalClose" aria-label="閉じる">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M5 5l14 14M19 5L5 19" stroke="currentColor" stroke-width="2"/></svg>
    </button>
    <span class="eyebrow" id="modalGenre">GENRE</span>
    <h3 id="modalTitle">タイトル名</h3>
    <p id="modalDesc" class="modal-desc"></p>
    <div class="modal-meta">
      <div>
        <span class="lab">練習日</span>
        <span class="val" id="modalSchedule"></span>
      </div>
      <div>
        <span class="lab">レベル目安</span>
        <span class="val" id="modalLevel"></span>
      </div>
      <div>
        <span class="lab">部員数</span>
        <span class="val" id="modalMembers"></span>
      </div>
    </div>
    <ul class="modal-points" id="modalPoints"></ul>
    <a href="#contact" class="btn btn-primary modal-cta" id="modalCta">このタイトルで参加相談する →</a>
  </div>
</div>

<!-- ===================== Q&A ===================== -->
<section id="qa">
  <div class="wrap">
    <span class="eyebrow">Q &amp; A</span>
    <h2 class="section-title">よくある質問</h2>
    <p class="section-sub">入会前によく聞かれる質問をまとめました。</p>

    <div class="qa-list">
      <div class="qa-item">
        <button class="qa-q">
          <span><span class="qmark">Q.</span> ゲーム初心者でも参加できますか？</span>
          <span class="plus">+</span>
        </button>
        <div class="qa-a">もちろん歓迎です。部員の半数以上は入会時初心者でした。上級者と一緒に練習できる機会も多いため、プレイを見たりアドバイスを受けたりしながら成長しやすい環境です。</div>
      </div>
      <div class="qa-item">
        <button class="qa-q">
          <span><span class="qmark">Q.</span> 他サークル・バイトと掛け持ちできますか？</span>
          <span class="plus">+</span>
        </button>
        <div class="qa-a">可能です。実際に、他サークルやアルバイトと両立しながら活動している部員もいます。授業や予定に合わせて参加しやすく、無理のない範囲で活動できるため、自分のペースでサークル活動を楽しめます。
</div>
      </div>
      <div class="qa-item">
        <button class="qa-q">
          <span><span class="qmark">Q.</span> PCやゲーム機材は持っていないとダメですか？</span>
          <span class="plus">+</span>
        </button>
        <div class="qa-a">必須ではありません。ゲームタイトルによっては個人の機材を使用する場合もありますので、必要な環境の詳細については各ゲームタイトルの紹介ページをご確認ください。
</div>
      </div>
      <div class="qa-item">
        <button class="qa-q">
          <span><span class="qmark">Q.</span> 入会費や年会費はかかりますか？</span>
          <span class="plus">+</span>
        </button>
        <div class="qa-a">入会費、年会費は無料です。</div>
      </div>
      <div class="qa-item">
        <button class="qa-q">
          <span><span class="qmark">Q.</span> 見学だけでも大丈夫ですか？</span>
          <span class="plus">+</span>
        </button>
        <div class="qa-a">大歓迎です。お問い合わせフォームまたは公式Xへ「見学希望」とご連絡いただければ、ご案内します。</div>
      </div>
    </div>
  </div>
</section>

<!-- ===================== CONTACT ===================== -->
<section id="contact">
  <div class="wrap">
    <span class="eyebrow">Contact</span>
    <h2 class="section-title">お問い合わせ</h2>
    <p class="section-sub">入会・見学のご希望やご質問は、以下のフォームよりお気軽にご連絡ください。</p>

   

      <form id="contactForm" novalidate>
        <div class="field" id="nameField">
          <label for="name">お名前</label>
          <input type="text" id="name" name="name" placeholder="駒沢 太郎">
          <div class="err-msg">お名前を入力してください。</div>
        </div>
        <div class="field" id="emailField">
          <label for="email">メールアドレス</label>
          <input type="email" id="email" name="email" placeholder="example@komazawa-u.ac.jp">
          <div class="err-msg">正しいメールアドレスを入力してください。</div>
        </div>
        <div class="field" id="messageField">
          <label for="message">お問い合わせ内容</label>
          <textarea id="message" name="message" placeholder="入会希望／見学希望／その他ご質問など"></textarea>
          <div class="err-msg">お問い合わせ内容を入力してください。</div>
        </div>
        <div class="submit-row">
          <button type="submit" class="btn btn-primary">送信する</button>
          <span class="form-note">※本フォームはデモ用です。実際の送信にはサーバー連携が必要です。</span>
        </div>
        <div class="form-success" id="formSuccess">送信内容を受け付けました。担当者より折り返しご連絡いたします。</div>
      </form>
    </div>
  </div>
</section>

<footer>
  <div class="wrap footer-row">
    <span class="copy">© 2026 KOMAZAWA UNIVERSITY ESPORTS CIRCLE</span>
    <div class="sns">
      <a href="#" aria-label="X"><svg width="16" height="16" viewBox="0 0 24 24" fill="none"><path d="M4 4l16 16M20 4L4 20" stroke="currentColor" stroke-width="2"/></svg></a>
      <a href="#" aria-label="Instagram"><svg width="16" height="16" viewBox="0 0 24 24" fill="none"><rect x="4" y="4" width="16" height="16" rx="4" stroke="currentColor" stroke-width="2"/><circle cx="12" cy="12" r="3.5" stroke="currentColor" stroke-width="2"/></svg></a>
      <a href="#" aria-label="Discord"><svg width="16" height="16" viewBox="0 0 24 24" fill="none"><rect x="3" y="7" width="18" height="11" rx="4" stroke="currentColor" stroke-width="2"/><circle cx="9" cy="12.5" r="1.2" fill="currentColor"/><circle cx="15" cy="12.5" r="1.2" fill="currentColor"/></svg></a>
    </div>
  </div>
</footer>

<script>
(function(){
  /* ---------- Hamburger menu ---------- */
  const burger = document.getElementById('burgerBtn');
  const panel = document.getElementById('navPanel');
  const overlay = document.getElementById('navOverlay');

  function openMenu(){
    panel.classList.add('open');
    overlay.classList.add('open');
    burger.setAttribute('aria-expanded','true');
    burger.setAttribute('aria-label','メニューを閉じる');
  }
  function closeMenu(){
    panel.classList.remove('open');
    overlay.classList.remove('open');
    burger.setAttribute('aria-expanded','false');
    burger.setAttribute('aria-label','メニューを開く');
  }

  burger.addEventListener('click', ()=>{
    const isOpen = panel.classList.contains('open');
    isOpen ? closeMenu() : openMenu();
  });
  overlay.addEventListener('click', closeMenu);
  document.querySelectorAll('.nav-link').forEach(link=>{
    link.addEventListener('click', closeMenu);
  });
  document.addEventListener('keydown', (e)=>{
    if(e.key === 'Escape') closeMenu();
  });

  /* ---------- Game detail modal ---------- */
  const gameData = {
    valorant: {
      genre: "FPS",
      title: "VALORANT",
      desc: "5vs5のタクティカルFPS。学内大会の主力タイトルとして、戦術理解とエイム力の両方を鍛える練習を行っています。",
      schedule: "毎週月・木 20:00〜",
      level: "初心者〜上級者",
      members: "約18名",
      points: [
        "レベル別に3チームに分けて練習",
        "学内対抗戦・他大学合同大会に出場",
        "VOD振り返り会を月1回実施"
      ]
    },
    apex: {
      genre: "Battle Royale",
      title: "Apex Legends",
      desc: "3人チームのバトルロイヤル。立ち回りの基礎から学べる講座があり、初めてのFPSとして始める部員が多いタイトルです。",
      schedule: "毎週火 21:00〜",
      level: "初心者歓迎",
      members: "約14名",
      points: [
        "初心者向け基礎講座を毎月開催",
        "ランクマッチ部内ランキングあり",
        "シーズンごとにオフ会を実施"
      ]
    },
    lol: {
      genre: "MOBA",
      title: "League of Legends",
      desc: "5vs5のMOBA。ロール別の役割理解とドラフト戦略を中心に練習しており、大会出場を見据えたチームも編成しています。",
      schedule: "毎週水 20:00〜",
      level: "初心者〜競技志向",
      members: "約16名",
      points: [
        "ロール別練習グループを編成",
        "ドラフトピック練習会を実施",
        "学外大会へのチーム出場実績あり"
      ]
    },
    smash: {
      genre: "Action",
      title: "大乱闘スマッシュブラザーズSPECIAL",
      desc: "オフラインでのタイマン対戦が中心。気軽に参加できる雰囲気で、学内交流戦のたびに大きく盛り上がるタイトルです。",
      schedule: "毎週土 13:00〜（学内オフライン）",
      level: "誰でも歓迎",
      members: "約22名",
      points: [
        "オフライン対戦会を毎週開催",
        "学内交流戦を毎学期実施",
        "キャラ対策の情報共有会あり"
      ]
    },
    splatoon: {
      genre: "Shooter",
      title: "スプラトゥーン3",
      desc: "部内で最も初心者が多いタイトル。勝敗よりも一緒に楽しむことを重視しつつ、ナワバリ・ガチマッチの両方を遊んでいます。",
      schedule: "毎週金 19:30〜",
      level: "初心者中心",
      members: "約12名",
      points: [
        "ナワバリ中心のカジュアル枠あり",
        "ブキ・ステージ別の攻略共有会",
        "新入部員向け体験会を随時開催"
      ]
    },
    sf6: {
      genre: "Fighting",
      title: "ストリートファイター6",
      desc: "格闘ゲーム経験者が集まる個人戦中心のタイトル。上位プレイヤーも在籍しており、本格的に上達を目指せる環境です。",
      schedule: "毎週日 14:00〜",
      level: "経験者中心",
      members: "約8名",
      points: [
        "個人ランクマッチ中心の活動",
        "上級者による個別コーチングあり",
        "学外大会・オフラインイベントへの参加実績"
      ]
    }
  };

  const modalOverlay = document.getElementById('gameModalOverlay');
  const modalGenre = document.getElementById('modalGenre');
  const modalTitle = document.getElementById('modalTitle');
  const modalDesc = document.getElementById('modalDesc');
  const modalSchedule = document.getElementById('modalSchedule');
  const modalLevel = document.getElementById('modalLevel');
  const modalMembers = document.getElementById('modalMembers');
  const modalPoints = document.getElementById('modalPoints');
  const modalClose = document.getElementById('modalClose');
  let lastFocusedCard = null;

  function openGameModal(key){
    const data = gameData[key];
    if(!data) return;
    modalGenre.textContent = data.genre;
    modalTitle.textContent = data.title;
    modalDesc.textContent = data.desc;
    modalSchedule.textContent = data.schedule;
    modalLevel.textContent = data.level;
    modalMembers.textContent = data.members;
    modalPoints.innerHTML = '';
    data.points.forEach(pt=>{
      const li = document.createElement('li');
      li.textContent = pt;
      modalPoints.appendChild(li);
    });
    modalOverlay.classList.add('open');
    modalClose.focus();
    document.body.style.overflow = 'hidden';
  }

  function closeGameModal(){
    modalOverlay.classList.remove('open');
    document.body.style.overflow = '';
    if(lastFocusedCard) lastFocusedCard.focus();
  }

  document.querySelectorAll('.game-card').forEach(card=>{
    card.addEventListener('click', ()=>{
      lastFocusedCard = card;
      openGameModal(card.dataset.game);
    });
  });

  modalClose.addEventListener('click', closeGameModal);
  modalOverlay.addEventListener('click', (e)=>{
    if(e.target === modalOverlay) closeGameModal();
  });
  document.addEventListener('keydown', (e)=>{
    if(e.key === 'Escape' && modalOverlay.classList.contains('open')) closeGameModal();
  });
  document.getElementById('modalCta').addEventListener('click', closeGameModal);

/* ---------- Q&A accordion ---------- */
  document.querySelectorAll('.qa-item').forEach(item=>{
    const btn = item.querySelector('.qa-q');
    const ans = item.querySelector('.qa-a');
    btn.addEventListener('click', ()=>{
      const isOpen = item.classList.contains('open');
      document.querySelectorAll('.qa-item.open').forEach(o=>{
        if(o!==item){
          o.classList.remove('open');
          o.querySelector('.qa-a').style.maxHeight = null;
        }
      });
      if(isOpen){
        item.classList.remove('open');
        ans.style.maxHeight = null;
      }else{
        item.classList.add('open');
        ans.style.maxHeight = ans.scrollHeight + 'px';
      }
    });
  });

  /* ---------- Contact form validation ---------- */
  const form = document.getElementById('contactForm');
  const success = document.getElementById('formSuccess');

  function setError(fieldId, hasError){
    document.getElementById(fieldId).classList.toggle('error', hasError);
  }

  form.addEventListener('submit', (e)=>{
    e.preventDefault();
    const name = document.getElementById('name').value.trim();
    const email = document.getElementById('email').value.trim();
    const message = document.getElementById('message').value.trim();
    const emailOk = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);

    let valid = true;
    if(!name){ setError('nameField', true); valid=false; } else setError('nameField', false);
    if(!emailOk){ setError('emailField', true); valid=false; } else setError('emailField', false);
    if(!message){ setError('messageField', true); valid=false; } else setError('messageField', false);

    if(valid){
      success.classList.add('show');
      form.reset();
      setTimeout(()=> success.scrollIntoView({behavior:'smooth', block:'nearest'}), 50);
    }else{
      success.classList.remove('show');
    }
  });
})();
</script>

</body>
</html>
