<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Cardápio — Acarajé</title>

  <!-- Fonte (padrão web-safe como fallback) -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg-1: #0f1724;
      --bg-2: #0b1220;
      --accent: #f6b042; /* tom quente do acarajé */
      --muted: #bfc9d6;
      --glass: rgba(255,255,255,0.06);
      --card: rgba(255,255,255,0.03);
      --glass-strong: rgba(255,255,255,0.08);
      --radius: 18px;
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: radial-gradient(1200px 700px at 10% 10%, rgba(246,176,66,0.07), transparent 8%),
                  radial-gradient(800px 500px at 90% 90%, rgba(255,255,255,0.02), transparent 12%),
                  linear-gradient(180deg,var(--bg-1),var(--bg-2));
      color: #e6eef8;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      padding:32px;
      display:flex;
      align-items:center;
      justify-content:center;
    }

    /* Container central */
    .wrap{
      width:100%;
      max-width:1100px;
      display:grid;
      grid-template-columns: 1fr 420px;
      gap:28px;
      align-items:start;
    }

    /* Header / hero */
    .hero{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius: var(--radius);
      padding:28px;
      box-shadow: 0 8px 30px rgba(2,6,23,0.6);
      border: 1px solid rgba(255,255,255,0.04);
      position:relative;
      overflow:hidden;
    }

    .brand{
      display:flex;
      gap:16px;
      align-items:center;
      margin-bottom:18px;
    }

    .logo{
      width:64px;
      height:64px;
      border-radius:14px;
      background: linear-gradient(135deg, var(--accent), #ff6b35);
      box-shadow: 0 6px 20px rgba(255,107,53,0.16), inset 0 -8px 18px rgba(0,0,0,0.15);
      display:flex;
      align-items:center;
      justify-content:center;
      font-family: "Playfair Display", serif;
      font-weight:700;
      font-size:22px;
      color: #081018;
    }

    h1{
      margin:0;
      font-family: "Playfair Display", serif;
      font-size:28px;
      line-height:1.05;
      color: #fff;
    }

    p.lead{
      margin:8px 0 0 0;
      color:var(--muted);
      font-size:14px;
    }

    /* Menu list (left column) */
    .menu-list{
      margin-top:18px;
      display:flex;
      gap:12px;
      flex-direction:column;
    }

    .menu-item{
      display:flex;
      gap:16px;
      align-items:center;
      padding:14px;
      border-radius:12px;
      background: var(--card);
      border:1px solid rgba(255,255,255,0.02);
      transition: transform .18s ease, box-shadow .18s ease;
    }
    .menu-item:hover{ transform:translateY(-6px); box-shadow: 0 12px 40px rgba(2,6,23,0.6); }

    .thumb{
      width:92px;
      height:92px;
      border-radius:10px;
      display:flex;
      align-items:center;
      justify-content:center;
      position:relative;
      flex-shrink:0;
      overflow:hidden;
      background: linear-gradient(135deg, rgba(255,255,255,0.03), rgba(0,0,0,0.08));
      border:1px solid rgba(255,255,255,0.03);
    }

    /* Decorative acarajé-illustration using SVG background */
    .thumb svg{ width:100%; height:100%; display:block; }

    .item-info{
      flex:1;
      min-width:0;
    }

    .item-title{
      font-weight:600;
      font-size:18px;
      margin:0 0 6px 0;
      color:#fff;
    }
    .item-desc{
      margin:0;
      color:var(--muted);
      font-size:13px;
      line-height:1.35;
    }
    .item-meta{
      margin-top:8px;
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:12px;
    }
    .price{
      font-weight:700;
      color:var(--accent);
      font-size:18px;
      font-family: "Playfair Display", serif;
    }

    /* Right column: card de pedido */
    .order-card{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:18px;
      padding:22px;
      border:1px solid rgba(255,255,255,0.04);
      box-shadow: 0 10px 40px rgba(2,6,23,0.6);
      position:sticky;
      top:32px;
      height:fit-content;
    }

    .order-card h2{
      margin:0 0 8px 0;
      font-family:"Playfair Display", serif;
      font-size:20px;
      color:#fff;
    }
    .small{ font-size:13px; color:var(--muted); margin-bottom:14px }

    /* quantity controls */
    .qty{
      display:flex;
      gap:12px;
      align-items:center;
      margin-bottom:14px;
    }
    .qty button{
      width:42px;
      height:42px;
      border-radius:10px;
      border:0;
      background:var(--glass);
      color:var(--muted);
      font-size:20px;
      cursor:pointer;
      transition:transform .12s ease;
    }
    .qty button:active{ transform:scale(.96) }
    .qty .num{
      min-width:68px;
      text-align:center;
      font-weight:600;
      font-size:18px;
      color:#fff;
      padding:8px 10px;
      border-radius:10px;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border:1px solid rgba(255,255,255,0.03);
    }

    .total{
      display:flex;
      justify-content:space-between;
      align-items:center;
      margin-top:12px;
      padding-top:12px;
      border-top:1px dashed rgba(255,255,255,0.04);
    }
    .total .label{ color:var(--muted); font-size:13px }
    .total .value{ font-family:"Playfair Display", serif; font-size:20px; color:var(--accent) }

    .cta{
      margin-top:18px;
      display:flex;
      gap:12px;
      flex-direction:column;
    }
    .btn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      gap:10px;
      padding:12px 16px;
      border-radius:12px;
      font-weight:600;
      cursor:pointer;
      border:0;
    }
    .btn-primary{
      background: linear-gradient(90deg, var(--accent), #ff6b35);
      color:#081018;
      box-shadow: 0 10px 30px rgba(255,107,53,0.12);
    }
    .btn-ghost{
      background:transparent;
      border:1px solid rgba(255,255,255,0.04);
      color:var(--muted);
    }

    footer.note{
      margin-top:18px;
      color:var(--muted);
      font-size:13px;
      text-align:left;
    }

    /* Responsive */
    @media (max-width:980px){
      .wrap{ grid-template-columns: 1fr; padding:0 6px; }
      .order-card{ position:relative; top:auto; }
    }
  </style>
</head>
<body>
  <main class="wrap" role="main" aria-labelledby="title">
    <!-- Left: hero + menu -->
    <section class="hero" aria-label="Cardápio de Acarajé">
      <div class="brand">
        <div class="logo" aria-hidden="true">A</div>
        <div>
          <h1 id="title">Acarajé — Só o melhor</h1>
          <p class="lead">Feito na palma da mão, recheado com vatapá, caruru, camarão seco e pimenta — tradição baiana autêntica.</p>
        </div>
      </div>

      <div class="menu-list" role="list">
        <!-- Único item -->
        <article class="menu-item" role="listitem" aria-labelledby="acaraje-title">
          <div class="thumb" aria-hidden="true">
            <!-- simple SVG ilustrativo -->
            <svg viewBox="0 0 120 120" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
              <defs>
                <linearGradient id="g" x1="0" x2="1">
                  <stop offset="0" stop-color="#ffd89b"/>
                  <stop offset="1" stop-color="#ff7b4b"/>
                </linearGradient>
              </defs>
              <rect x="0" y="0" width="120" height="120" rx="12" fill="url(#g)"/>
              <g transform="translate(12,18)" stroke="#7a2e10" stroke-width="1.8" fill="#fff7ea">
                <ellipse cx="48" cy="42" rx="36" ry="22" fill="#fff7ea" opacity="0.95"/>
                <path d="M14 42c8-12 68-12 78 0" fill="#ffedd6" />
                <circle cx="34" cy="36" r="3" fill="#d36b2f"/>
                <circle cx="54" cy="38" r="3" fill="#d36b2f"/>
              </g>
            </svg>
          </div>

          <div class="item-info">
            <h3 class="item-title" id="acaraje-title">Acarajé tradicional</h3>
            <p class="item-desc">Bolinho de feijão-fradinho frito no dendê, recheado com vatapá, caruru, camarão seco e pimenta.</p>

            <div class="item-meta">
              <div class="price">R$ 14,00</div>
              <div class="meta-note" style="color:var(--muted); font-size:13px">Pronto em 4–6 min • Serve 1</div>
            </div>
          </div>
        </article>
      </div>

      <footer class="note" aria-hidden="true">
        Dica: peça quantos quiser e ajuste a quantidade no cartão de pedido à direita.
      </footer>
    </section>

    <!-- Right: pedido -->
    <aside class="order-card" aria-label="Pedido">
      <h2>Seu pedido</h2>
      <p class="small">Acarajé tradicional — R$ 14,00</p>

      <div class="qty" aria-hidden="false">
        <button id="dec" title="Diminuir quantidade">−</button>
        <div class="num" id="qty" role="status" aria-live="polite">1</div>
        <button id="inc" title="Aumentar quantidade">+</button>
      </div>

      <label style="display:block; font-size:13px; color:var(--muted); margin-bottom:8px">
        Observação (opcional)
      </label>
      <textarea id="note" placeholder="Sem pimenta / retirar camarão..." style="width:100%; min-height:78px; resize:vertical; padding:10px; border-radius:10px; border:1px solid rgba(255,255,255,0.03); background:transparent; color:#eaf1ff"></textarea>

      <div class="total" aria-hidden="false">
        <div class="label">Total</div>
        <div class="value" id="total">R$ 14,00</div>
      </div>

      <div class="cta">
        <!-- Você pode substituir o href por um link real do WhatsApp com número e mensagem -->
        <a id="orderBtn" class="btn btn-primary" href="#" role="button" onclick="handleOrder(event)">
          Pedir via WhatsApp
        </a>
        <button class="btn btn-ghost" onclick="addToCart()">Adicionar ao carrinho</button>
      </div>

      <footer style="margin-top:12px; color:var(--muted); font-size:13px">
        Pagamento na entrega • Retirada disponível
      </footer>
    </aside>
  </main>

  <script>
    // Preços e lógica simples
    const PRICE = 14.00;
    const qtyEl = document.getElementById('qty');
    const totalEl = document.getElementById('total');
    const inc = document.getElementById('inc');
    const dec = document.getElementById('dec');
    const note = document.getElementById('note');

    let qty = 1;
    function formatBRL(v){
      return v.toLocaleString('pt-BR', { style:'currency', currency:'BRL' });
    }

    function update(){
      qtyEl.textContent = qty;
      totalEl.textContent = formatBRL(qty * PRICE);
    }

    inc.addEventListener('click', ()=>{ qty = Math.min(20, qty+1); update(); });
    dec.addEventListener('click', ()=>{ qty = Math.max(1, qty-1); update(); });

    function addToCart(){
      // Simples feedback visual
      const btn = document.querySelector('.btn-ghost');
      btn.textContent = 'Adicionado ✓';
      setTimeout(()=> btn.textContent = 'Adicionar ao carrinho', 1200);
    }

    function handleOrder(e){
      e.preventDefault();
      const mensagem = encodeURIComponent(
        `Olá! Gostaria de pedir ${qty} acarajé(s). Total: ${formatBRL(qty*PRICE)}.` +
        (note.value.trim() ? ` Observação: ${note.value.trim()}` : '')
      );
      // Substitua o número abaixo pelo desejado no formato internacional (ex: 5579981077018)
      const numero = '55XXXXXXXXXXX';
      const url = `https://wa.me/${numero}?text=${mensagem}`;
      // abrir em nova aba
      window.open(url, '_blank');
    }

    // Inicia
    update();
  </script>
</body>
</html>
