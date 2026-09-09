<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>AuraMetrics — Marketing Intelligence AI</title>
  <meta name="description" content="Plataforma de inteligencia de marketing impulsada por IA para detectar tendencias, analizar competidores y descubrir oportunidades.">

  <style>
    :root {
      --bg: #070b14;
      --bg-2: #0b1120;
      --card: rgba(16, 24, 40, 0.78);
      --card-hover: rgba(24, 34, 56, 0.9);
      --text: #f8fafc;
      --muted: #94a3b8;
      --line: rgba(148, 163, 184, 0.15);
      --blue: #5b8cff;
      --purple: #8b5cf6;
      --cyan: #22d3ee;
      --green: #34d399;
      --yellow: #fbbf24;
      --red: #fb7185;
      --radius: 20px;
      --max: 1180px;
      --font: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
        "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      background:
        radial-gradient(circle at 15% 10%, rgba(91,140,255,.12), transparent 30%),
        radial-gradient(circle at 85% 20%, rgba(139,92,246,.10), transparent 30%),
        var(--bg);
      color: var(--text);
      font-family: var(--font);
      line-height: 1.6;
      min-height: 100vh;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    button,
    input,
    select {
      font: inherit;
    }

    button {
      cursor: pointer;
    }

    .container {
      width: min(var(--max), calc(100% - 40px));
      margin: auto;
    }

    /* NAVBAR */

    header {
      position: sticky;
      top: 0;
      z-index: 1000;
      backdrop-filter: blur(18px);
      background: rgba(7, 11, 20, .78);
      border-bottom: 1px solid var(--line);
    }

    .nav {
      height: 76px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 800;
      font-size: 20px;
      letter-spacing: -.5px;
    }

    .logo-icon {
      width: 36px;
      height: 36px;
      border-radius: 11px;
      display: grid;
      place-items: center;
      background: linear-gradient(135deg, var(--blue), var(--purple));
      box-shadow: 0 0 30px rgba(91,140,255,.25);
    }

    .logo-icon svg {
      width: 21px;
      height: 21px;
    }

    nav {
      display: flex;
      gap: 28px;
      align-items: center;
    }

    nav a {
      color: var(--muted);
      font-size: 14px;
      transition: .2s;
    }

    nav a:hover {
      color: white;
    }

    .nav-actions {
      display: flex;
      gap: 10px;
      align-items: center;
    }

    .btn {
      border: 0;
      border-radius: 11px;
      padding: 11px 18px;
      font-weight: 700;
      color: white;
      background: rgba(255,255,255,.07);
      border: 1px solid var(--line);
      transition: .2s;
    }

    .btn:hover {
      transform: translateY(-1px);
      background: rgba(255,255,255,.12);
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--blue), var(--purple));
      border: 0;
      box-shadow: 0 10px 30px rgba(91,140,255,.2);
    }

    .btn-primary:hover {
      box-shadow: 0 14px 38px rgba(91,140,255,.3);
    }

    .mobile-menu {
      display: none;
      background: transparent;
      border: 0;
      color: white;
      font-size: 25px;
    }

    /* HERO */

    .hero {
      padding: 110px 0 80px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .hero::before {
      content: "";
      position: absolute;
      width: 500px;
      height: 500px;
      background: rgba(91,140,255,.10);
      filter: blur(100px);
      border-radius: 50%;
      left: 50%;
      top: 0;
      transform: translateX(-50%);
      pointer-events: none;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 7px 12px;
      border: 1px solid rgba(91,140,255,.25);
      background: rgba(91,140,255,.08);
      border-radius: 999px;
      color: #b9caff;
      font-size: 12px;
      font-weight: 800;
      letter-spacing: .7px;
      position: relative;
    }

    .pulse {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: var(--green);
      box-shadow: 0 0 12px var(--green);
    }

    h1 {
      font-size: clamp(48px, 7vw, 86px);
      line-height: .98;
      letter-spacing: -4px;
      max-width: 900px;
      margin: 28px auto;
      position: relative;
    }

    .gradient {
      background: linear-gradient(100deg, #fff, #a9c4ff 40%, #a78bfa 75%, #67e8f9);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .hero p {
      max-width: 690px;
      margin: auto;
      color: var(--muted);
      font-size: 18px;
    }

    .hero-buttons {
      display: flex;
      justify-content: center;
      gap: 12px;
      margin-top: 30px;
    }

    .hero-buttons .btn {
      padding: 14px 22px;
    }

    /* DASHBOARD */

    .dashboard-wrap {
      margin-top: 65px;
      position: relative;
    }

    .dashboard {
      background: rgba(10, 16, 29, .9);
      border: 1px solid rgba(148,163,184,.18);
      border-radius: 24px;
      box-shadow: 0 40px 100px rgba(0,0,0,.45);
      overflow: hidden;
      text-align: left;
    }

    .dashboard-top {
      height: 52px;
      display: flex;
      align-items: center;
      gap: 7px;
      padding: 0 18px;
      border-bottom: 1px solid var(--line);
    }

    .dot {
      width: 9px;
      height: 9px;
      border-radius: 50%;
      background: #475569;
    }

    .dashboard-body {
      display: grid;
      grid-template-columns: 210px 1fr;
      min-height: 500px;
    }

    .sidebar {
      border-right: 1px solid var(--line);
      padding: 22px 14px;
    }

    .side-title {
      color: #64748b;
      font-size: 10px;
      font-weight: 800;
      text-transform: uppercase;
      margin: 0 10px 12px;
      letter-spacing: 1px;
    }

    .side-link {
      padding: 10px;
      border-radius: 9px;
      color: var(--muted);
      font-size: 13px;
      margin-bottom: 3px;
    }

    .side-link.active {
      background: rgba(91,140,255,.12);
      color: #dbe7ff;
    }

    .main-dashboard {
      padding: 25px;
    }

    .dashboard-heading {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .dashboard-heading h3 {
      font-size: 20px;
    }

    .demo-label {
      color: var(--yellow);
      font-size: 10px;
      border: 1px solid rgba(251,191,36,.25);
      background: rgba(251,191,36,.07);
      border-radius: 999px;
      padding: 5px 9px;
      font-weight: 800;
    }

    .metric-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 13px;
    }

    .metric {
      border: 1px solid var(--line);
      background: rgba(255,255,255,.025);
      border-radius: 14px;
      padding: 17px;
    }

    .metric small {
      color: var(--muted);
      font-size: 11px;
    }

    .metric strong {
      display: block;
      font-size: 25px;
      margin-top: 3px;
    }

    .up {
      color: var(--green);
      font-size: 11px;
    }

    .dashboard-grid {
      display: grid;
      grid-template-columns: 1.4fr 1fr;
      gap: 14px;
      margin-top: 14px;
    }

    .panel {
      border: 1px solid var(--line);
      background: rgba(255,255,255,.025);
      border-radius: 15px;
      padding: 18px;
    }

    .panel h4 {
      margin-bottom: 15px;
      font-size: 14px;
    }

    .trend-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 11px 0;
      border-bottom: 1px solid var(--line);
      font-size: 12px;
    }

    .trend-row:last-child {
      border: 0;
    }

    .trend-score {
      color: var(--green);
      font-weight: 800;
    }

    .chart {
      height: 150px;
      display: flex;
      align-items: end;
      gap: 8px;
      padding-top: 20px;
    }

    .chart-bar {
      flex: 1;
      border-radius: 6px 6px 0 0;
      background: linear-gradient(to top, var(--blue), var(--purple));
      min-width: 8px;
      opacity: .9;
    }

    /* SECTIONS */

    section {
      padding: 100px 0;
    }

    .section-heading {
      max-width: 700px;
      margin-bottom: 45px;
    }

    .section-heading span {
      color: #8fb0ff;
      font-size: 12px;
      font-weight: 800;
      letter-spacing: 1px;
      text-transform: uppercase;
    }

    .section-heading h2 {
      font-size: clamp(34px, 5vw, 58px);
      line-height: 1.05;
      letter-spacing: -2px;
      margin: 12px 0;
    }

    .section-heading p {
      color: var(--muted);
      font-size: 16px;
    }

    .features {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
    }

    .feature {
      padding: 25px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--card);
      transition: .25s;
    }

    .feature:hover {
      transform: translateY(-5px);
      background: var(--card-hover);
      border-color: rgba(91,140,255,.3);
    }

    .feature-icon {
      width: 45px;
      height: 45px;
      border-radius: 13px;
      display: grid;
      place-items: center;
      background: rgba(91,140,255,.11);
      color: #9db8ff;
      margin-bottom: 20px;
    }

    .feature h3 {
      font-size: 18px;
      margin-bottom: 8px;
    }

    .feature p {
      color: var(--muted);
      font-size: 14px;
    }

    /* RADAR */

    .radar-box {
      border: 1px solid var(--line);
      border-radius: 24px;
      background: var(--card);
      padding: 24px;
    }

    .filters {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-bottom: 25px;
    }

    .filter {
      border: 1px solid var(--line);
      background: transparent;
      color: var(--muted);
      padding: 8px 13px;
      border-radius: 999px;
      font-size: 12px;
    }

    .filter.active,
    .filter:hover {
      color: white;
      background: rgba(91,140,255,.12);
      border-color: rgba(91,140,255,.3);
    }

    .radar-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 13px;
    }

    .signal {
      padding: 20px;
      border: 1px solid var(--line);
      border-radius: 16px;
      background: rgba(255,255,255,.025);
    }

    .signal-top {
      display: flex;
      justify-content: space-between;
      gap: 10px;
    }

    .signal h3 {
      font-size: 16px;
    }

    .signal .category {
      color: var(--muted);
      font-size: 11px;
      margin: 5px 0 16px;
    }

    .signal-score {
      font-size: 26px;
      font-weight: 800;
    }

    .signal-bar {
      height: 5px;
      background: #1e293b;
      border-radius: 99px;
      overflow: hidden;
      margin-top: 12px;
    }

    .signal-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--blue), var(--cyan));
      border-radius: inherit;
    }

    /* AI ANALYST */

    .analyst {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      align-items: stretch;
    }

    .analyst-copy {
      padding: 25px 0;
    }

    .analyst-copy ul {
      list-style: none;
      margin-top: 25px;
    }

    .analyst-copy li {
      color: var(--muted);
      margin: 12px 0;
      font-size: 14px;
    }

    .analyst-copy li::before {
      content: "✓";
      color: var(--green);
      margin-right: 10px;
      font-weight: 900;
    }

    .chat {
      border: 1px solid var(--line);
      background: var(--card);
      border-radius: 22px;
      padding: 20px;
    }

    .chat-head {
      display: flex;
      align-items: center;
      gap: 10px;
      padding-bottom: 15px;
      border-bottom: 1px solid var(--line);
    }

    .ai-avatar {
      width: 38px;
      height: 38px;
      display: grid;
      place-items: center;
      border-radius: 11px;
      background: linear-gradient(135deg, var(--blue), var(--purple));
      font-weight: 900;
    }

    .chat-head small {
      color: var(--muted);
      display: block;
    }

    .messages {
      height: 260px;
      overflow-y: auto;
      padding: 18px 0;
    }

    .message {
      max-width: 88%;
      padding: 12px 14px;
      border-radius: 13px;
      font-size: 13px;
      margin-bottom: 12px;
    }

    .message.ai {
      background: rgba(255,255,255,.05);
      color: #dce4f2;
    }

    .message.user {
      background: rgba(91,140,255,.15);
      margin-left: auto;
      color: #dbe7ff;
    }

    .chat-input {
      display: flex;
      gap: 8px;
    }

    .chat-input input {
      flex: 1;
      min-width: 0;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.04);
      color: white;
      outline: none;
      border-radius: 11px;
      padding: 11px 13px;
    }

    .chat-input button {
      border: 0;
      background: var(--blue);
      color: white;
      border-radius: 11px;
      padding: 0 15px;
      font-weight: 800;
    }

    /* COMPETITORS */

    .competitor-table {
      border: 1px solid var(--line);
      border-radius: 20px;
      overflow: hidden;
      background: var(--card);
    }

    .comp-row {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr 1fr;
      padding: 17px 20px;
      border-bottom: 1px solid var(--line);
      font-size: 13px;
      align-items: center;
    }

    .comp-row:last-child {
      border-bottom: 0;
    }

    .comp-head {
      color: var(--muted);
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: .7px;
    }

    .positive {
      color: var(--green);
    }

    /* CAMPAIGN */

    .generator {
      border: 1px solid var(--line);
      background: var(--card);
      border-radius: 24px;
      padding: 25px;
    }

    .generator-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
    }

    .field label {
      display: block;
      color: var(--muted);
      font-size: 12px;
      margin-bottom: 7px;
    }

    .field input,
    .field select,
    .field textarea {
      width: 100%;
      border: 1px solid var(--line);
      border-radius: 11px;
      background: rgba(255,255,255,.035);
      color: white;
      padding: 12px;
      outline: none;
    }

    .field select option {
      background: #0b1120;
    }

    .field textarea {
      min-height: 100px;
      resize: vertical;
    }

    .full {
      grid-column: 1 / -1;
    }

    .generator-result {
      display: none;
      margin-top: 20px;
      border: 1px solid rgba(52,211,153,.2);
      background: rgba(52,211,153,.05);
      border-radius: 15px;
      padding: 18px;
    }

    .generator-result.show {
      display: block;
    }

    /* PRICING */

    .pricing {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
    }

    .price-card {
      border: 1px solid var(--line);
      background: var(--card);
      border-radius: 22px;
      padding: 28px;
      position: relative;
    }

    .price-card.featured {
      border-color: rgba(91,140,255,.45);
      box-shadow: 0 20px 60px rgba(91,140,255,.08);
    }

    .popular {
      position: absolute;
      top: 17px;
      right: 17px;
      font-size: 10px;
      font-weight: 900;
      color: #bcd0ff;
      background: rgba(91,140,255,.12);
      border: 1px solid rgba(91,140,255,.25);
      padding: 5px 8px;
      border-radius: 99px;
    }

    .price-card h3 {
      font-size: 18px;
    }

    .price {
      font-size: 40px;
      font-weight: 900;
      margin: 13px 0 3px;
    }

    .price small {
      color: var(--muted);
      font-size: 13px;
      font-weight: 500;
    }

    .price-card p {
      color: var(--muted);
      font-size: 13px;
    }

    .price-card ul {
      list-style: none;
      margin: 22px 0;
    }

    .price-card li {
      font-size: 13px;
      color: #cbd5e1;
      margin: 10px 0;
    }

    .price-card li::before {
      content: "✓";
      color: var(--green);
      margin-right: 9px;
    }

    .price-card .btn {
      width: 100%;
    }

    /* CTA */

    .final-cta {
      text-align: center;
      padding: 110px 20px;
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      background:
        radial-gradient(circle at center, rgba(91,140,255,.10), transparent 50%);
    }

    .final-cta h2 {
      font-size: clamp(38px, 6vw, 65px);
      letter-spacing: -3px;
      line-height: 1;
      max-width: 800px;
      margin: auto;
    }

    .final-cta p {
      color: var(--muted);
      margin: 20px auto 28px;
      max-width: 600px;
    }

    /* LEGAL */

    .legal {
      padding: 55px 0;
    }

    .legal-box {
      border: 1px solid rgba(251,191,36,.2);
      background: rgba(251,191,36,.04);
      border-radius: 15px;
      padding: 20px;
      color: #d7dce5;
      font-size: 13px;
    }

    .legal-box strong {
      color: var(--yellow);
    }

    /* FOOTER */

    footer {
      padding: 35px 0;
      color: var(--muted);
      font-size: 12px;
    }

    .footer-inner {
      display: flex;
      justify-content: space-between;
      gap: 20px;
      align-items: center;
    }

    .footer-links {
      display: flex;
      gap: 20px;
    }

    .footer-links a:hover {
      color: white;
    }

    /* RESPONSIVE */

    @media (max-width: 900px) {
      nav {
        display: none;
      }

      .mobile-menu {
        display: block;
      }

      .dashboard-body {
        grid-template-columns: 1fr;
      }

      .sidebar {
        display: none;
      }

      .features,
      .radar-grid,
      .pricing {
        grid-template-columns: 1fr 1fr;
      }

      .analyst {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 650px) {
      .container {
        width: min(100% - 24px, var(--max));
      }

      .hero {
        padding-top: 75px;
      }

      h1 {
        font-size: 47px;
        letter-spacing: -2.5px;
      }

      .hero p {
        font-size: 16px;
      }

      .hero-buttons {
        flex-direction: column;
      }

      .hero-buttons .btn {
        width: 100%;
      }

      .metric-grid,
      .dashboard-grid,
      .features,
      .radar-grid,
      .pricing,
      .generator-grid {
        grid-template-columns: 1fr;
      }

      .full {
        grid-column: auto;
      }

      .comp-row {
        grid-template-columns: 1.7fr 1fr 1fr;
      }

      .comp-row div:nth-child(4) {
        display: none;
      }

      .footer-inner {
        flex-direction: column;
        text-align: center;
      }

      .dashboard-heading {
        align-items: flex-start;
        gap: 10px;
        flex-direction: column;
      }
    }
  </style>
</head>

<body>

<header>
  <div class="container nav">

    <a href="#inicio" class="logo">
      <span class="logo-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M4 17l6-6 4 4 6-8"/>
          <path d="M17 7h3v3"/>
        </svg>
      </span>
      AuraMetrics
    </a>

    <nav>
      <a href="#radar">Trend Radar</a>
      <a href="#analyst">AI Analyst</a>
      <a href="#competitors">Competidores</a>
      <a href="#campaigns">Campaign AI</a>
      <a href="#pricing">Precios</a>
    </nav>

    <div class="nav-actions">
      <a href="#pricing" class="btn btn-primary">Empezar</a>
      <button class="mobile-menu" onclick="alert('Usa el menú de secciones desplazándote por la página.')">☰</button>
    </div>

  </div>
</header>

<main>

  <!-- HERO -->

  <section class="hero" id="inicio">
    <div class="container">

      <span class="eyebrow">
        <span class="pulse"></span>
        MARKETING INTELLIGENCE AI
      </span>

      <h1>
        Know what's next.
        <span class="gradient">Before everyone else.</span>
      </h1>

      <p>
        Detecta señales emergentes, descubre tendencias, analiza competidores
        y convierte datos en oportunidades de marketing antes de que se vuelvan mainstream.
      </p>

      <div class="hero-buttons">
        <a href="#radar" class="btn btn-primary">Explorar Trend Radar →</a>
        <a href="#analyst" class="btn">Ver cómo funciona</a>
      </div>

      <div class="dashboard-wrap">

        <div class="dashboard">

          <div class="dashboard-top">
            <span class="dot"></span>
            <span class="dot"></span>
            <span class="dot"></span>
          </div>

          <div class="dashboard-body">

            <aside class="sidebar">

              <div class="side-title">Intelligence</div>

              <div class="side-link active">◈ Overview</div>
              <div class="side-link">◉ Trend Radar</div>
              <div class="side-link">⌁ Consumer Signals</div>
              <div class="side-link">◌ Competitors</div>
              <div class="side-link">◎ Markets</div>

              <br>

              <div class="side-title">AI Tools</div>

              <div class="side-link">✦ AI Analyst</div>
              <div class="side-link">✦ Campaign AI</div>

            </aside>

            <div class="main-dashboard">

              <div class="dashboard-heading">
                <div>
                  <h3>Intelligence Overview</h3>
                  <small style="color:#64748b;">Vista de demostración</small>
                </div>

                <span class="demo-label">DEMO DATA</span>
              </div>

              <div class="metric-grid">

                <div class="metric">
                  <small>Emerging Signals</small>
                  <strong>1,284</strong>
                  <span class="up">↑ 18.4%</span>
                </div>

                <div class="metric">
                  <small>Trend Momentum</small>
                  <strong>87.6</strong>
                  <span class="up">↑ 12.8%</span>
                </div>

                <div class="metric">
                  <small>Opportunities</small>
                  <strong>342</strong>
                  <span class="up">↑ 24.1%</span>
                </div>

              </div>

              <div class="dashboard-grid">

                <div class="panel">

                  <h4>Trending Signals</h4>

                  <div class="trend-row">
                    <span>AI Shopping Assistants</span>
                    <span class="trend-score">+94%</span>
                  </div>

                  <div class="trend-row">
                    <span>Micro Communities</span>
                    <span class="trend-score">+82%</span>
                  </div>

                  <div class="trend-row">
                    <span>Creator Commerce</span>
                    <span class="trend-score">+76%</span>
                  </div>

                  <div class="trend-row">
                    <span>Smart Travel</span>
                    <span class="trend-score">+69%</span>
                  </div>

                </div>

                <div class="panel">

                  <h4>Momentum — SAMPLE</h4>

                  <div class="chart">
                    <span class="chart-bar" style="height:35%"></span>
                    <span class="chart-bar" style="height:42%"></span>
                    <span class="chart-bar" style="height:48%"></span>
                    <span class="chart-bar" style="height:45%"></span>
                    <span class="chart-bar" style="height:61%"></span>
                    <span class="chart-bar" style="height:70%"></span>
                    <span class="chart-bar" style="height:84%"></span>
                    <span class="chart-bar" style="height:94%"></span>
                  </div>

                </div>

              </div>

            </div>

          </div>

        </div>

      </div>

    </div>
  </section>


  <!-- FEATURES -->

  <section>
    <div class="container">

      <div class="section-heading">
        <span>One intelligence layer</span>
        <h2>De señales dispersas a decisiones inteligentes.</h2>
        <p>
          AuraMetrics está diseñado para transformar señales de mercado
          en acciones concretas para equipos de marketing.
        </p>
      </div>

      <div class="features">

        <div class="feature">
          <div class="feature-icon">◈</div>
          <h3>Detect</h3>
          <p>
            Encuentra señales que están empezando a crecer antes de que
            alcancen una audiencia masiva.
          </p>
        </div>

        <div class="feature">
          <div class="feature-icon">◉</div>
          <h3>Understand</h3>
          <p>
            Analiza comportamiento, audiencia, contexto y velocidad de crecimiento.
          </p>
        </div>

        <div class="feature">
          <div class="feature-icon">✦</div>
          <h3>Act</h3>
          <p>
            Convierte las señales detectadas en ideas de contenido,
            campañas y oportunidades.
          </p>
        </div>

      </div>

    </div>
  </section>


  <!-- TREND RADAR -->

  <section id="radar">

    <div class="container">

      <div class="section-heading">
        <span>Trend Radar</span>
        <h2>Descubre qué está empezando a importar.</h2>
        <p>
          Un radar conceptual de tendencias para marcas y equipos de marketing.
          Todos los datos de esta demo son ficticios.
        </p>
      </div>

      <div class="radar-box">

        <div class="filters">

          <button class="filter active" onclick="filterTrends('all', this)">
            Todos
          </button>

          <button class="filter" onclick="filterTrends('technology', this)">
            Tecnología
          </button>

          <button class="filter" onclick="filterTrends('social', this)">
            Social
          </button>

          <button class="filter" onclick="filterTrends('commerce', this)">
            Commerce
          </button>

          <button class="filter" onclick="filterTrends('lifestyle', this)">
            Lifestyle
          </button>

        </div>

        <div class="radar-grid" id="radarGrid">

          <article class="signal" data-category="technology">
            <div class="signal-top">
              <h3>AI Shopping</h3>
              <span>🔥</span>
            </div>
            <div class="category">TECHNOLOGY · DEMO</div>
            <div class="signal-score">94</div>
            <small style="color:#64748b;">Momentum score</small>
            <div class="signal-bar">
              <div class="signal-fill" style="width:94%"></div>
            </div>
          </article>

          <article class="signal" data-category="social">
            <div class="signal-top">
              <h3>Micro Communities</h3>
              <span>◉</span>
            </div>
            <div class="category">SOCIAL · DEMO</div>
            <div class="signal-score">82</div>
            <small style="color:#64748b;">Momentum score</small>
            <div class="signal-bar">
              <div class="signal-fill" style="width:82%"></div>
            </div>
          </article>

          <article class="signal" data-category="commerce">
            <div class="signal-top">
              <h3>Creator Commerce</h3>
              <span>✦</span>
            </div>
            <div class="category">COMMERCE · DEMO</div>
            <div class="signal-score">76</div>
            <small style="color:#64748b;">Momentum score</small>
            <div class="signal-bar">
              <div class="signal-fill" style="width:76%"></div>
            </div>
          </article>

          <article class="signal" data-category="lifestyle">
            <div class="signal-top">
              <h3>Smart Travel</h3>
              <span>✈</span>
            </div>
            <div class="category">LIFESTYLE · DEMO</div>
            <div class="signal-score">69</div>
            <small style="color:#64748b;">Momentum score</small>
            <div class="signal-bar">
              <div class="signal-fill" style="width:69%"></div>
            </div>
          </article>

          <article class="signal" data-category="technology">
            <div class="signal-top">
              <h3>Wearable AI</h3>
              <span>◎</span>
            </div>
            <div class="category">TECHNOLOGY · DEMO</div>
            <div class="signal-score">73</div>
            <small style="color:#64748b;">Momentum score</small>
            <div class="signal-bar">
              <div class="signal-fill" style="width:73%"></div>
            </div>
          </article>

          <article class="signal" data-category="social">
            <div class="signal-top">
              <h3>Short-form Search</h3>
              <span>⌕</span>
            </div>
            <div class="category">SOCIAL · DEMO</div>
            <div class="signal-score">88</div>
            <small style="color:#64748b;">Momentum score</small>
            <div class="signal-bar">
              <div class="signal-fill" style="width:88%"></div>
            </div>
          </article>

        </div>

      </div>

    </div>

  </section>


  <!-- AI ANALYST -->

  <section id="analyst">

    <div class="container">

      <div class="analyst">

        <div class="analyst-copy">

          <div class="section-heading">
            <span>AI Marketing Analyst</span>
            <h2>Pregunta al mercado.</h2>
            <p>
              Un asistente conceptual que convierte inteligencia de mercado
              en respuestas útiles para marketing.
            </p>
          </div>

          <ul>
            <li>Analiza tendencias emergentes.</li>
            <li>Propone oportunidades para una marca.</li>
            <li>Genera hipótesis de campañas.</li>
            <li>Resume señales complejas en lenguaje sencillo.</li>
          </ul>

        </div>

        <div class="chat">

          <div class="chat-head">

            <div class="ai-avatar">✦</div>

            <div>
              <strong>Aura AI Analyst</strong>
              <small>Marketing Intelligence · DEMO</small>
            </div>

          </div>

          <div class="messages" id="messages">

            <div class="message ai">
              Hola. Soy el AI Marketing Analyst de esta demo.
              Pregúntame algo sobre tendencias, contenido o marketing.
            </div>

          </div>

          <div class="chat-input">

            <input
              id="chatInput"
              type="text"
              placeholder="Ej: ¿Qué tendencia debería vigilar?"
            >

            <button onclick="askAI()">Enviar</button>

          </div>

        </div>

      </div>

    </div>

  </section>


  <!-- COMPETITORS -->

  <section id="competitors">

    <div class="container">

      <div class="section-heading">
        <span>Competitor Intelligence</span>
        <h2>Observa el movimiento del mercado.</h2>
        <p>
          Comparativa conceptual de competidores. Los nombres y datos mostrados
          son exclusivamente ejemplos ficticios.
        </p>
      </div>

      <div class="competitor-table">

        <div class="comp-row comp-head">
          <div>Marca</div>
          <div>Momentum</div>
          <div>Social</div>
          <div>Señal</div>
        </div>

        <div class="comp-row">
          <div>Brand Alpha <small style="color:#64748b;">DEMO</small></div>
          <div class="positive">+82%</div>
          <div>+67%</div>
          <div>High</div>
        </div>

        <div class="comp-row">
          <div>Brand Nova <small style="color:#64748b;">DEMO</small></div>
          <div class="positive">+74%</div>
          <div>+58%</div>
          <div>Rising</div>
        </div>

        <div class="comp-row">
          <div>Brand Orbit <small style="color:#64748b;">DEMO</small></div>
          <div class="positive">+61%</div>
          <div>+49%</div>
          <div>Stable</div>
        </div>

        <div class="comp-row">
          <div>Brand Pulse <small style="color:#64748b;">DEMO</small></div>
          <div class="positive">+53%</div>
          <div>+42%</div>
          <div>Emerging</div>
        </div>

      </div>

    </div>

  </section>


  <!-- CAMPAIGN GENERATOR -->

  <section id="campaigns">

    <div class="container">

      <div class="section-heading">
        <span>Campaign AI</span>
        <h2>Convierte una señal en una campaña.</h2>
        <p>
          Generador conceptual para transformar una tendencia en una idea
          de marketing accionable.
        </p>
      </div>

      <div class="generator">

        <div class="generator-grid">

          <div class="field">
            <label>Marca</label>
            <input id="brandInput" placeholder="Ej: Mi marca">
          </div>

          <div class="field">
            <label>Objetivo</label>
            <select id="goalInput">
              <option>Awareness</option>
              <option>Engagement</option>
              <option>Ventas</option>
              <option>Lanzamiento</option>
            </select>
          </div>

          <div class="field">
            <label>Plataforma</label>
            <select id="platformInput">
              <option>TikTok</option>
              <option>Instagram</option>
              <option>YouTube</option>
              <option>Multi-platform</option>
            </select>
          </div>

          <div class="field">
            <label>Tendencia</label>
            <input id="trendInput" placeholder="Ej: AI Shopping">
          </div>

          <div class="field full">
            <label>Contexto adicional</label>
            <textarea id="contextInput" placeholder="Describe brevemente tu producto, público o campaña..."></textarea>
          </div>

          <div class="full">
            <button class="btn btn-primary" onclick="generateCampaign()">
              ✦ Generar concepto de campaña
            </button>
          </div>

        </div>

        <div class="generator-result" id="campaignResult">

          <strong>Concepto generado · DEMO</strong>

          <p id="campaignText" style="margin-top:8px;color:#cbd5e1;"></p>

        </div>

      </div>

    </div>

  </section>


  <!-- PRICING -->

  <section id="pricing">

    <div class="container">

      <div class="section-heading">
        <span>Pricing</span>
        <h2>Empieza pequeño. Escala con inteligencia.</h2>
        <p>
          Precios conceptuales para la demo. No representan una oferta comercial real.
        </p>
      </div>

      <div class="pricing">

        <div class="price-card">

          <h3>Starter</h3>

          <div class="price">
            €49 <small>/mes</small>
          </div>

          <p>Para explorar nuevas oportunidades.</p>

          <ul>
            <li>Trend Radar</li>
            <li>Alertas básicas</li>
            <li>AI Analyst limitado</li>
            <li>1 usuario</li>
          </ul>

          <button class="btn" onclick="demoAlert('Starter')">
            Empezar
          </button>

        </div>


        <div class="price-card featured">

          <span class="popular">POPULAR</span>

          <h3>Pro</h3>

          <div class="price">
            €199 <small>/mes</small>
          </div>

          <p>Para equipos de marketing.</p>

          <ul>
            <li>Trend Radar avanzado</li>
            <li>Competitor Intelligence</li>
            <li>AI Marketing Analyst</li>
            <li>Campaign AI</li>
            <li>5 usuarios</li>
          </ul>

          <button class="btn btn-primary" onclick="demoAlert('Pro')">
            Empezar
          </button>

        </div>


        <div class="price-card">

          <h3>Enterprise</h3>

          <div class="price">
            Custom
          </div>

          <p>Para organizaciones con necesidades avanzadas.</p>

          <ul>
            <li>Intelligence personalizada</li>
            <li>Market monitoring</li>
            <li>Equipos ilimitados</li>
            <li>Soporte empresarial</li>
          </ul>

          <button class="btn" onclick="demoAlert('Enterprise')">
            Contactar
          </button>

        </div>

      </div>

    </div>

  </section>


  <!-- FINAL CTA -->

  <section class="final-cta">

    <div class="container">

      <h2>
        Stop reacting to trends.
        <span class="gradient">Start anticipating them.</span>
      </h2>

      <p>
        AuraMetrics convierte señales del mercado en inteligencia
        que puede utilizar un equipo de marketing.
      </p>

      <a href="#radar" class="btn btn-primary">
        Explorar la plataforma →
      </a>

    </div>

  </section>


  <!-- LEGAL -->

  <section class="legal" id="legal">

    <div class="container">

      <div class="legal-box">

        <strong>⚠ BORRADOR LEGAL — REQUIERE REVISIÓN PROFESIONAL</strong>

        <p style="margin-top:10px;">
          Esta página es una demostración/prototipo. Antes de utilizar AuraMetrics
          comercialmente deberán prepararse y revisarse los textos legales,
          política de privacidad, política de cookies, condiciones de uso,
          tratamiento de datos y cualquier otra documentación necesaria.
        </p>

        <p style="margin-top:10px;">
          Esta demo no implementa un backend real ni procesamiento real de
          datos de clientes. Los datos mostrados en la interfaz son ficticios
          y están identificados como DEMO DATA cuando corresponde.
        </p>

      </div>

    </div>

  </section>

</main>


<footer>

  <div class="container footer-inner">

    <div>
      © 2026 AuraMetrics · Proyecto en desarrollo
    </div>

    <div class="footer-links">
      <a href="#legal">Legal</a>
      <a href="#pricing">Pricing</a>
      <a href="#inicio">Inicio</a>
    </div>

  </div>

</footer>


<script>

  /* ================================
     TREND RADAR FILTER
  ================================= */

  function filterTrends(category, button) {

    document.querySelectorAll(".filter").forEach(function(btn) {
      btn.classList.remove("active");
    });

    button.classList.add("active");

    document.querySelectorAll(".signal").forEach(function(card) {

      if (category === "all" || card.dataset.category === category) {
        card.style.display = "block";
      } else {
        card.style.display = "none";
      }

    });

  }


  /* ================================
     AI ANALYST DEMO
  ================================= */

  function askAI() {

    const input = document.getElementById("chatInput");
    const messages = document.getElementById("messages");

    const question = input.value.trim();

    if (!question) return;

    const userMessage = document.createElement("div");

    userMessage.className = "message user";
    userMessage.textContent = question;

    messages.appendChild(userMessage);

    input.value = "";

    const aiMessage = document.createElement("div");

    aiMessage.className = "message ai";
    aiMessage.textContent =
      "DEMO: He detectado una posible oportunidad relacionada con esta consulta. " +
      "En una versión conectada a datos reales, AuraMetrics analizaría señales, " +
      "crecimiento, audiencia y contexto para generar una recomendación.";

    messages.appendChild(aiMessage);

    messages.scrollTop = messages.scrollHeight;

  }


  document.getElementById("chatInput").addEventListener("keydown", function(event) {

    if (event.key === "Enter") {
      askAI();
    }

  });


  /* ================================
     CAMPAIGN GENERATOR DEMO
  ================================= */

  function generateCampaign() {

    const brand =
      document.getElementById("brandInput").value.trim() || "tu marca";

    const goal =
      document.getElementById("goalInput").value;

    const platform =
      document.getElementById("platformInput").value;

    const trend =
      document.getElementById("trendInput").value.trim() || "una tendencia emergente";

    const result =
      document.getElementById("campaignResult");

    const text =
      document.getElementById("campaignText");

    text.textContent =
      `${brand} podría utilizar "${trend}" como concepto creativo para una campaña de ${goal.toLowerCase()} en ${platform}. DEMO: el sistema propondría posteriormente hooks, formatos de contenido, mensajes y variantes creativas basadas en datos reales.`;

    result.classList.add("show");

    result.scrollIntoView({
      behavior: "smooth",
      block: "nearest"
    });

  }


  /* ================================
     PRICING DEMO
  ================================= */

  function demoAlert(plan) {

    alert(
      "DEMO: Has seleccionado el plan " +
      plan +
      ". El sistema de pago todavía no está conectado."
    );

  }

</script>


<!--
=========================================================
AURAMETRICS — PROJECT NOTES
=========================================================

Este archivo es un prototipo front-end.

Actualmente:
- No existe backend.
- No existen APIs conectadas.
- Los datos son ficticios.
- No se almacenan cuentas de usuarios.
- No se implementa un sistema de pago.
- No se incluyen API keys.
- No se incluyen librerías externas.

Para una versión comercial deberán implementarse,
entre otras cosas:

1. Backend seguro.
2. Sistema de autenticación.
3. Base de datos.
4. APIs de datos/trends.
5. Sistema real de IA.
6. Sistema de alertas.
7. Billing/pagos.
8. Política de privacidad.
9. Política de cookies.
10. Términos y condiciones.
11. Revisión de licencias y titularidad.
12. Revisión de marca y dominio.

No introducir API keys o secretos directamente en este archivo.

=========================================================
-->
</body>
</html>
