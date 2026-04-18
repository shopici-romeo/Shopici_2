<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ShopiCI — Crée ta boutique en ligne</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --blue: #1E3A8A;
      --blue-light: #3B82F6;
      --blue-pale: #EFF6FF;
      --green: #00C853;
      --green-light: #F0FDF4;
      --rose: #F43F5E;
      --rose-light: #FFF1F2;
      --white: #FFFFFF;
      --gray: #F8FAFC;
      --text: #0F172A;
      --muted: #64748B;
      --border: #E2E8F0;
    }

    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--white);
      color: var(--text);
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 16px 6%;
      background: rgba(255,255,255,0.95);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      box-shadow: 0 1px 20px rgba(0,0,0,0.06);
    }
    .logo {
      font-family: 'Syne', sans-serif;
      font-size: 1.6rem;
      font-weight: 800;
      color: var(--blue);
    }
    .logo span { color: var(--green); }
    .nav-links {
      display: flex;
      gap: 32px;
      list-style: none;
    }
    .nav-links a {
      text-decoration: none;
      color: var(--muted);
      font-size: 0.9rem;
      font-weight: 500;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--blue); }
    .nav-right { display: flex; gap: 12px; align-items: center; }
    .btn-login {
      padding: 9px 20px;
      border-radius: 8px;
      border: 1.5px solid var(--border);
      background: transparent;
      color: var(--text);
      font-size: 0.88rem;
      font-weight: 500;
      cursor: pointer;
      font-family: 'DM Sans', sans-serif;
      transition: all 0.2s;
    }
    .btn-login:hover { border-color: var(--blue); color: var(--blue); }
    .btn-nav {
      padding: 10px 22px;
      border-radius: 8px;
      border: none;
      background: var(--blue);
      color: white;
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 0.88rem;
      cursor: pointer;
      transition: background 0.2s;
    }
    .btn-nav:hover { background: var(--blue-light); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      padding: 120px 6% 80px;
      background: linear-gradient(135deg, #EFF6FF 0%, #F0FDF4 50%, #FFF1F2 100%);
      position: relative;
      overflow: hidden;
    }
    .hero::before {
      content: '';
      position: absolute;
      top: -100px; right: -100px;
      width: 500px; height: 500px;
      background: radial-gradient(circle, rgba(59,130,246,0.1) 0%, transparent 70%);
    }
    .hero::after {
      content: '';
      position: absolute;
      bottom: -50px; left: -50px;
      width: 400px; height: 400px;
      background: radial-gradient(circle, rgba(0,200,83,0.08) 0%, transparent 70%);
    }
    .hero-content {
      max-width: 580px;
      position: relative;
      z-index: 1;
    }
    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 6px 16px;
      border-radius: 100px;
      background: white;
      border: 1.5px solid var(--blue-light);
      font-size: 0.8rem;
      color: var(--blue);
      font-weight: 600;
      margin-bottom: 28px;
      box-shadow: 0 2px 12px rgba(59,130,246,0.1);
    }
    .badge-dot {
      width: 7px; height: 7px;
      border-radius: 50%;
      background: var(--green);
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.5; transform: scale(1.4); }
    }
    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2.5rem, 5vw, 4rem);
      font-weight: 800;
      line-height: 1.1;
      letter-spacing: -1.5px;
      color: var(--text);
      margin-bottom: 20px;
    }
    .hero h1 .blue { color: var(--blue); }
    .hero h1 .green { color: var(--green); }
    .hero h1 .rose { color: var(--rose); }
    .hero p {
      font-size: 1.1rem;
      color: var(--muted);
      line-height: 1.7;
      margin-bottom: 36px;
      max-width: 480px;
    }
    .hero-btns {
      display: flex;
      gap: 14px;
      align-items: center;
      margin-bottom: 48px;
      flex-wrap: wrap;
    }
    .btn-primary {
      padding: 14px 32px;
      border-radius: 10px;
      border: none;
      background: var(--blue);
      color: white;
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 1rem;
      cursor: pointer;
      box-shadow: 0 4px 20px rgba(30,58,138,0.3);
      transition: all 0.2s;
    }
    .btn-primary:hover {
      background: var(--blue-light);
      transform: translateY(-2px);
      box-shadow: 0 8px 30px rgba(30,58,138,0.3);
    }
    .btn-secondary {
      padding: 14px 28px;
      border-radius: 10px;
      border: 1.5px solid var(--border);
      background: white;
      color: var(--text);
      font-size: 1rem;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.2s;
    }
    .btn-secondary:hover {
      border-color: var(--blue);
      color: var(--blue);
    }
    .hero-stats {
      display: flex;
      gap: 32px;
      flex-wrap: wrap;
    }
    .stat-item {
      display: flex;
      flex-direction: column;
    }
    .stat-num {
      font-family: 'Syne', sans-serif;
      font-size: 1.6rem;
      font-weight: 800;
      color: var(--blue);
    }
    .stat-label {
      font-size: 0.78rem;
      color: var(--muted);
      margin-top: 2px;
    }
    .hero-image {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      z-index: 1;
    }
    .hero-card {
      background: white;
      border-radius: 20px;
      padding: 28px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.1);
      width: 320px;
      border: 1px solid var(--border);
    }
    .hero-card-header {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 20px;
    }
    .shop-avatar {
      width: 44px; height: 44px;
      border-radius: 11px;
      background: linear-gradient(135deg, var(--rose), #FB7185);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.3rem;
    }
    .shop-name {
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      color: var(--text);
      font-size: 0.95rem;
    }
    .shop-status {
      font-size: 0.72rem;
      color: var(--green);
      font-weight: 600;
    }
    .card-stat {
      background: var(--gray);
      border-radius: 10px;
      padding: 14px 16px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .card-stat-label {
      font-size: 0.78rem;
      color: var(--muted);
    }
    .card-stat-value {
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      color: var(--text);
      font-size: 0.95rem;
    }
    .card-stat-value.green { color: var(--green); }
    .card-stat-value.blue { color: var(--blue); }
    .card-stat-value.rose { color: var(--rose); }
    .card-btn {
      width: 100%;
      padding: 12px;
      border-radius: 10px;
      border: none;
      background: var(--blue);
      color: white;
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 0.88rem;
      cursor: pointer;
      margin-top: 4px;
    }

    /* SECTION TAG */
    .section-tag {
      display: inline-block;
      padding: 5px 16px;
      border-radius: 100px;
      font-size: 0.75rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 14px;
    }
    .tag-blue { background: var(--blue-pale); color: var(--blue); }
    .tag-green { background: var(--green-light); color: #15803D; }
    .tag-rose { background: var(--rose-light); color: var(--rose); }

    .section-title {
      font-family: 'Syne', sans-serif;
      font-size: clamp(1.8rem, 4vw, 2.8rem);
      font-weight: 800;
      letter-spacing: -1px;
      color: var(--text);
      margin-bottom: 12px;
    }
    .section-sub {
      color: var(--muted);
      font-size: 1rem;
      max-width: 500px;
      margin: 0 auto;
      line-height: 1.6;
    }

    /* PAIEMENTS */
    .payments {
      padding: 90px 6%;
      background: var(--blue-pale);
      text-align: center;
    }
    .pay-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      max-width: 900px;
      margin: 48px auto 0;
    }
    .pay-card {
      background: white;
      border: 1.5px solid var(--border);
      border-radius: 14px;
      padding: 24px 16px;
      text-align: center;
      transition: all 0.2s;
      box-shadow: 0 2px 8px rgba(0,0,0,0.04);
    }
    .pay-card:hover {
      border-color: var(--blue-light);
      transform: translateY(-4px);
      box-shadow: 0 8px 24px rgba(59,130,246,0.15);
    }
    .pay-emoji { font-size: 2rem; margin-bottom: 10px; }
    .pay-name {
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 0.9rem;
      color: var(--text);
      margin-bottom: 4px;
    }
    .pay-desc { font-size: 0.75rem; color: var(--muted); }

    /* FEATURES */
    .features {
      padding: 90px 6%;
      text-align: center;
    }
    .features-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      max-width: 1000px;
      margin: 48px auto 0;
    }
    .feature-card {
      background: white;
      border: 1.5px solid var(--border);
      border-radius: 16px;
      padding: 28px 24px;
      text-align: left;
      transition: all 0.2s;
      box-shadow: 0 2px 8px rgba(0,0,0,0.04);
    }
    .feature-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 32px rgba(0,0,0,0.08);
    }
    .feature-card.blue-card { border-top: 3px solid var(--blue); }
    .feature-card.green-card { border-top: 3px solid var(--green); }
    .feature-card.rose-card { border-top: 3px solid var(--rose); }
    .feature-icon {
      width: 48px; height: 48px;
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.4rem;
      margin-bottom: 16px;
    }
    .icon-blue { background: var(--blue-pale); }
    .icon-green { background: var(--green-light); }
    .icon-rose { background: var(--rose-light); }
    .feature-card h3 {
      font-family: 'Syne', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 8px;
    }
    .feature-card p {
      font-size: 0.85rem;
      color: var(--muted);
      line-height: 1.6;
    }

    /* ENTREPOTS */
    .entrepots {
      padding: 90px 6%;
      background: linear-gradient(135deg, var(--blue) 0%, #1D4ED8 100%);
      text-align: center;
      color: white;
    }
    .entrepots .section-title { color: white; }
    .entrepots .section-sub { color: rgba(255,255,255,0.7); }
    .villes-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
      margin: 48px auto 0;
      max-width: 700px;
    }
    .ville-badge {
      padding: 10px 20px;
      background: rgba(255,255,255,0.15);
      border: 1.5px solid rgba(255,255,255,0.25);
      border-radius: 100px;
      font-size: 0.88rem;
      font-weight: 600;
      color: white;
      backdrop-filter: blur(10px);
      transition: all 0.2s;
    }
    .ville-badge:hover {
      background: rgba(255,255,255,0.25);
      transform: scale(1.05);
    }
    .ville-badge.active {
      background: white;
      color: var(--blue);
      border-color: white;
    }

    /* TARIFS */
    .pricing {
      padding: 90px 6%;
      text-align: center;
      background: var(--gray);
    }
    .pricing-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      max-width: 960px;
      margin: 48px auto 0;
    }
    .price-card {
      background: white;
      border: 1.5px solid var(--border);
      border-radius: 20px;
      padding: 36px 28px;
      text-align: left;
      position: relative;
      box-shadow: 0 2px 8px rgba(0,0,0,0.04);
      transition: all 0.2s;
    }
    .price-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 32px rgba(0,0,0,0.08);
    }
    .price-card.popular {
      border-color: var(--blue);
      border-width: 2px;
      box-shadow: 0 8px 32px rgba(30,58,138,0.15);
    }
    .popular-badge {
      position: absolute;
      top: -14px; left: 50%;
      transform: translateX(-50%);
      background: var(--blue);
      color: white;
      font-family: 'Syne', sans-serif;
      font-size: 0.72rem;
      font-weight: 700;
      padding: 5px 18px;
      border-radius: 100px;
      white-space: nowrap;
    }
    .plan-name {
      font-size: 0.8rem;
      font-weight: 700;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 12px;
    }
    .plan-price {
      font-family: 'Syne', sans-serif;
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--text);
    }
    .plan-price span {
      font-size: 0.9rem;
      font-weight: 400;
      color: var(--muted);
    }
    .plan-desc {
      font-size: 0.85rem;
      color: var(--muted);
      margin: 10px 0 24px;
    }
    .plan-features { list-style: none; margin-bottom: 28px; }
    .plan-features li {
      font-size: 0.85rem;
      color: var(--text);
      padding: 8px 0;
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .plan-features li::before {
      content: '✓';
      color: var(--green);
      font-weight: 700;
    }
    .btn-plan {
      width: 100%;
      padding: 13px;
      border-radius: 10px;
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 0.9rem;
      cursor: pointer;
      transition: all 0.2s;
    }
    .btn-plan-outline {
      background: white;
      border: 1.5px solid var(--border);
      color: var(--text);
    }
    .btn-plan-outline:hover {
      border-color: var(--blue);
      color: var(--blue);
    }
    .btn-plan-blue {
      background: var(--blue);
      border: none;
      color: white;
    }
    .btn-plan-blue:hover { background: var(--blue-light); }

    /* CTA */
    .cta {
      padding: 100px 6%;
      text-align: center;
      background: linear-gradient(135deg, #FFF1F2 0%, #EFF6FF 50%, #F0FDF4 100%);
    }
    .cta h2 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2rem, 5vw, 3.2rem);
      font-weight: 800;
      letter-spacing: -1px;
      color: var(--text);
      max-width: 600px;
      margin: 0 auto 16px;
    }
    .cta p {
      color: var(--muted);
      font-size: 1rem;
      margin-bottom: 36px;
    }

    /* FOOTER */
    footer {
      padding: 40px 6%;
      border-top: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
    }
    .footer-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.3rem;
      color: var(--blue);
    }
    .footer-logo span { color: var(--green); }
    .footer-links {
      display: flex;
      gap: 24px;
    }
    .footer-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.85rem;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: var(--blue); }
    .footer-right {
      font-size: 0.78rem;
      color: var(--muted);
    }

    /* MOBILE */
    @media (max-width: 768px) {
      .nav-links { display: none; }
      .hero { flex-direction: column; text-align: center; }
      .hero-image { display: none; }
      .hero-stats { justify-content: center; }
      .pay-grid { grid-template-columns: repeat(2, 1fr); }
      .features-grid { grid-template-columns: 1fr; }
      .pricing-grid { grid-template-columns: 1fr; }
      .footer-links { display: none; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="logo">Shopi<span>CI</span></div>
    <ul class="nav-links">
      <li><a href="#">Fonctionnalités</a></li>
      <li><a href="#">Tarifs</a></li>
      <li><a href="#">Entrepôts</a></li>
      <li><a href="#">Blog</a></li>
    </ul>
    <div class="nav-right">
      <button class="btn-login">Se connecter</button>
      <button class="btn-nav">Essai gratuit →</button>
    </div>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-content">
      <div class="hero-badge">
        <span class="badge-dot"></span>
        Lancé en Côte d'Ivoire · Bientôt dans toute l'UEMOA
      </div>
      <h1>
        Vends partout<br>
        en <span class="blue">Côte d'Ivoire</span><br>
        sans <span class="rose">magasin.</span>
      </h1>
      <p>La plateforme e-commerce made in Côte d'Ivoire. Orange Money, MTN, Wave et livraison locale — tout est inclus dès le départ.</p>
      <div class="hero-btns">
        <button class="btn-primary">Créer ma boutique gratuitement</button>
        <button class="btn-secondary">Voir une démo →</button>
      </div>
      <div class="hero-stats">
        <div class="stat-item">
          <span class="stat-num">500K+</span>
          <span class="stat-label">Entrepreneurs cibles</span>
        </div>
        <div class="stat-item">
          <span class="stat-num">0 FCFA</span>
          <span class="stat-label">Pour commencer</span>
        </div>
        <div class="stat-item">
          <span class="stat-num">10 min</span>
          <span class="stat-label">Pour lancer</span>
        </div>
      </div>
    </div>
    <div class="hero-image">
      <div class="hero-card">
        <div class="hero-card-header">
          <div class="shop-avatar">👗</div>
          <div>
            <div class="shop-name">Awa Fashion</div>
            <div class="shop-status">● Boutique active</div>
          </div>
        </div>
        <div class="card-stat">
          <span class="card-stat-label">💰 Ventes ce mois</span>
          <span class="card-stat-value green">312 500 FCFA</span>
        </div>
        <div class="card-stat">
          <span class="card-stat-label">🛍️ Commandes</span>
          <span class="card-stat-value blue">47 commandes</span>
        </div>
        <div class="card-stat">
          <span class="card-stat-label">🌍 Villes couvertes</span>
          <span class="card-stat-value rose">4 villes</span>
        </div>
        <div class="card-stat">
          <span class="card-stat-label">💸 Retrait lundi</span>
          <span class="card-stat-value green">312 500 FCFA</span>
        </div>
        <button class="card-btn">Voir ma boutique →</button>
      </div>
    </div>
  </section>

  <!-- PAIEMENTS -->
  <section class="payments">
    <div class="section-tag tag-blue">Paiements</div>
    <h2 class="section-title">Tous les paiements<br>africains intégrés</h2>
    <p class="section-sub">Tes clients paient comme ils veulent — Mobile Money, Wave ou carte bancaire.</p>
    <div class="pay-grid">
      <div class="pay-card">
        <div class="pay-emoji">🟠</div>
        <div class="pay-name">Orange Money</div>
        <div class="pay-desc">Paiement instantané</div>
      </div>
      <div class="pay-card">
        <div class="pay-emoji">🟡</div>
        <div class="pay-name">MTN MoMo</div>
        <div class="pay-desc">Paiement instantané</div>
      </div>
      <div class="pay-card">
        <div class="pay-emoji">🔵</div>
        <div class="pay-name">Wave</div>
        <div class="pay-desc">0% de frais Wave</div>
      </div>
      <div class="pay-card">
        <div class="pay-emoji">💳</div>
        <div class="pay-name">Carte bancaire</div>
        <div class="pay-desc">Visa & Mastercard</div>
      </div>
    </div>
  </section>

  <!-- FEATURES -->
  <section class="features">
    <div class="section-tag tag-green">Fonctionnalités</div>
    <h2 class="section-title">Tout ce dont tu as besoin<br>pour vendre en ligne</h2>
    <p class="section-sub">Des outils pensés pour la réalité des entrepreneurs ivoiriens.</p>
    <div class="features-grid">
      <div class="feature-card blue-card">
        <div class="feature-icon icon-blue">🏪</div>
        <h3>Boutique en 10 minutes</h3>
        <p>Crée ta boutique sans coder. Logo automatique, nom de boutique par IA — tout est prêt.</p>
      </div>
      <div class="feature-card green-card">
        <div class="feature-icon icon-green">📦</div>
        <h3>Entrepôts dans toute la CI</h3>
        <p>Stocke tes produits à Bouaké, Divo, Korhogo et vends partout sans ouvrir un magasin.</p>
      </div>
      <div class="feature-card rose-card">
        <div class="feature-icon icon-rose">🚚</div>
        <h3>Livraison en 24h</h3>
        <p>Nos partenaires Yango livrent partout en Côte d'Ivoire. Suivi en temps réel sur carte.</p>
      </div>
      <div class="feature-card blue-card">
        <div class="feature-icon icon-blue">📊</div>
        <h3>Dashboard complet</h3>
        <p>Ventes en ligne ET en boutique physique — tout au même endroit en temps réel.</p>
      </div>
      <div class="feature-card green-card">
        <div class="feature-icon icon-green">🤖</div>
        <h3>Intelligence artificielle</h3>
        <p>IA qui analyse tes photos, génère tes descriptions et te conseille pour vendre plus.</p>
      </div>
      <div class="feature-card rose-card">
        <div class="feature-icon icon-rose">🛡️</div>
        <h3>Zéro arnaque</h3>
        <p>Vérification CNI et vidéo obligatoire — chaque vendeur est certifié et identifié.</p>
      </div>
    </div>
  </section>

  <!-- ENTREPOTS -->
  <section class="entrepots">
    <div class="section-tag" style="background:rgba(255,255,255,0.15);color:white;">Réseau National</div>
    <h2 class="section-title">Vends dans toute<br>la Côte d'Ivoire</h2>
    <p class="section-sub">Nos entrepôts dans les grandes villes te permettent de livrer partout sans magasin physique.</p>
    <div class="villes-grid">
      <div class="ville-badge active">📍 Abidjan</div>
      <div class="ville-badge">📍 Bouaké</div>
      <div class="ville-badge">📍 Yamoussoukro</div>
      <div class="ville-badge">📍 San-Pédro</div>
      <div class="ville-badge">📍 Divo</div>
      <div class="ville-badge">📍 Daloa</div>
      <div class="ville-badge">📍 Korhogo</div>
      <div class="ville-badge">📍 Béoumi</div>
      <div class="ville-badge">📍 Tiassalé</div>
      <div class="ville-badge">📍 Gagnoa</div>
    </div>
  </section>

  <!-- TARIFS -->
  <section class="pricing">
    <div class="section-tag tag-blue">Tarifs</div>
    <h2 class="section-title">Simple et transparent</h2>
    <p class="section-sub">Commence gratuitement. Évolue quand tu grandis.</p>
    <div class="pricing-grid">
      <div class="price-card">
        <div class="plan-name">Gratuit</div>
        <div class="plan-price">0 <span>FCFA/mois</span></div>
        <div class="plan-desc">Pour démarrer et tester ShopiCI</div>
        <ul class="plan-features">
          <li>5 produits max</li>
          <li>Sous-domaine ShopiCI</li>
          <li>Paiements Mobile Money</li>
          <li>9 extensions incluses</li>
        </ul>
        <button class="btn-plan btn-plan-outline">Commencer gratuitement</button>
      </div>
      <div class="price-card popular">
        <div class="popular-badge">⭐ Le plus populaire</div>
        <div class="plan-name">Standard</div>
        <div class="plan-price">5 000 <span>FCFA/mois</span></div>
        <div class="plan-desc">Pour les entrepreneurs sérieux</div>
        <ul class="plan-features">
          <li>Produits illimités</li>
          <li>Domaine personnalisé</li>
          <li>Tous les paiements</li>
          <li>23 extensions incluses</li>
          <li>Templates pub WhatsApp</li>
        </ul>
        <button class="btn-plan btn-plan-blue">Choisir Standard →</button>
      </div>
      <div class="price-card">
        <div class="plan-name">Pro</div>
        <div class="plan-price">15 000 <span>FCFA/mois</span></div>
        <div class="plan-desc">Pour dominer le marché</div>
        <ul class="plan-features">
          <li>Tout du Standard</li>
          <li>Multi-boutiques</li>
          <li>Entrepôts multi-villes</li>
          <li>34 extensions incluses</li>
          <li>Gestionnaire dédié</li>
        </ul>
        <button class="btn-plan btn-plan-outline">Choisir Pro</button>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <section class="cta">
    <h2>Prêt à vendre partout<br>en Côte d'Ivoire ? 🇨🇮</h2>
    <p>Rejoins les premiers entrepreneurs ivoiriens qui vendent sans frontières.</p>
    <button class="btn-primary" style="font-size:1.05rem; padding:16px 40px;">
      Créer ma boutique gratuitement →
    </button>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">Shopi<span>CI</span></div>
    <div class="footer-links">
      <a href="#">Fonctionnalités</a>
      <a href="#">Tarifs</a>
      <a href="#">Contact</a>
      <a href="#">Blog</a>
    </div>
    <div class="footer-right">© 2025 ShopiCI · Abidjan 🇨🇮</div>
  </footer>

</body>
</html># Shopici_2
