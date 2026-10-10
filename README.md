<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IVK PARFUME</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: #202020;
  color: #f5f5f5;
  font-family: Arial, sans-serif;
}

header {
  background: #171717;
  padding: 20px 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #383838;
  position: sticky;
  top: 0;
  z-index: 10;
}

.logo {
  font-size: 21px;
  font-weight: bold;
  letter-spacing: 2px;
}

nav button {
  background: none;
  color: white;
  border: 0;
  font-size: 14px;
  margin-left: 10px;
  cursor: pointer;
}

.hero {
  padding: 65px 20px;
  text-align: center;
  background: linear-gradient(140deg, #303030, #181818);
}

.hero h1 {
  font-size: 34px;
  margin-bottom: 15px;
}

.hero p {
  color: #c2c2c2;
  line-height: 1.6;
}

.section {
  padding: 30px 16px;
  max-width: 1000px;
  margin: auto;
}

.section h2 {
  margin-bottom: 22px;
  font-size: 25px;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(145px, 1fr));
  gap: 15px;
}

.product {
  background: #292929;
  border: 1px solid #404040;
  border-radius: 12px;
  overflow: hidden;
  padding-bottom: 16px;
}

.bottle {
  height: 165px;
  background: #242424;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 15px;
}

.bottle svg {
  width: 100px;
  height: 130px;
}

.product h3 {
  font-size: 16px;
  padding: 14px 12px 8px;
}

.product p {
  color: #bdbdbd;
  font-size: 13px;
  padding: 0 12px;
  line-height: 1.5;
}

.price {
  display: block;
  padding: 12px;
  font-size: 19px;
  font-weight: bold;
}

.btn {
  display: block;
  background: #eeeeee;
  color: #171717;
  border: none;
  border-radius: 7px;
  padding: 12px;
  margin: 0 12px;
  width: calc(100% - 24px);
  font-weight: bold;
  cursor: pointer;
}

.btn:active {
  opacity: 0.7;
}

.panel {
  display: none;
  padding: 25px 16px;
  max-width: 700px;
  margin: auto;
}

.panel h2 {
  margin-bottom: 18px;
}

.panel p {
  line-height: 1.8;
  color: #d0d0d0;
}

.item {
  background: #2c2c2c;
  padding: 15px;
  border-radius: 8px;
  margin: 10px 0;
  line-height: 1.7;
}

.item button {
  padding: 7px 10px;
  margin-top: 8px;
  margin-right: 5px;
  cursor: pointer;
}

a {
  color: white;
}

footer {
  border-top: 1px solid #383838;
  background: #171717;
  text-align: center;
  padding: 25px 15px;
  margin-top: 35px;
  color: #aaa;
  line-height: 2;
}

footer a {
  margin: 0 7px;
}

.empty {
  color: #aaa;
  margin: 15px 0;
}

@media (max-width: 380px) {
  .logo { font-size: 17px; }
  nav button { font-size: 12px; margin-left: 5px; }
  .hero h1 { font-size: 28px; }
}
</style>
</head>

<body>

<header>
  <div class="logo">IVK PARFUME</div>
  <nav>
    <button onclick="showPage('shop')">Каталог</button>
    <button onclick="showPage('cart')">Кошик (<span id="count">0</span>)</button>
    <button onclick="showPage('profile')">Профіль</button>
  </nav>
</header>

<div id="shop">
  <section class="hero">
    <h1>Знайди свій аромат</h1>
    <p>Парфуми та відливи 5 мл</p>
    <p>Твій аромат. Твій стиль.</p>
  </section>

  <section class="section">
    <h2>Наш каталог</h2>
    <div class="products" id="products"></div>
  </section>
</div>

<section class="panel" id="cart">
  <h2>Кошик</h2>
  <div id="cartItems"></div>
  <h3 id="total">Разом: 0 грн</h3>
  <br>
  <button class="btn" onclick="order()">Оформити замовлення</button>
</section>

<section class="panel" id="profile">
  <h2>Мій профіль</h2>
  <p>Ласкаво просимо до IVK PARFUME.</p>
  <br>
  <label for="customerName">Твоє ім'я:</label>
  <input id="customerName" placeholder="Введи ім'я"
    style="width:100%;padding:12px;margin:10px 0;background:#303030;color:white;border:1px solid #555;border-radius:6px">
  <label for="customerPhone">Номер телефону:</label>
  <input id="customerPhone" type="tel" placeholder="+380..."
    style="width:100%;padding:12px;margin:10px 0;background:#303030;color:white;border:1px solid #555;border-radius:6px">
  <button class="btn" onclick="saveProfile()">Зберегти дані</button>
  <p id="profileMessage" style="margin-top:12px"></p>
</section>

<section class="panel" id="about">
  <h2>Про нас</h2>
  <p>IVK PARFUME — магазин ароматів та парфумерних відливів об'ємом 5 мл.</p>
  <p>Обирай аромат, додавай до кошика та оформлюй замовлення.</p>
</section>

<footer>
  <strong>IVK PARFUME</strong>
  <p>Парфуми та відливи 5 мл</p>
  <p>
    <a href="https://www.instagram.com/ivk_parfumes/" target="_blank">Instagram</a>
    <a href="https://t.me/prechep" target="_blank">Telegram</a>
  </p>
  <p>© 2026 IVK PARFUME</p>
  <p><a href="#" onclick="showPage('about');return false;">Про нас</a></p>
</footer>

<script>
const perfumes = [
  {
    id: 1,
    name: "Creed Aventus",
    description: "Свіжий, деревний і впевнений аромат.",
    price: 150
  },
  {
    id: 2,
    name: "Armani Stronger With You Intensely",
    description: "Теплий, солодкий і пряний аромат.",
    price: 100
  },
  {
    id: 3,
    name: "Versace Dylan Blue",
    description: "Свіжий, насичений чоловічий аромат.",
    price: 100
  }
];

let cart = [];

function bottleSVG(id) {
  const colors = {
    1: "#c5b18a",
    2: "#8a6547",
    3: "#245b82"
  };
  return `
  <svg viewBox="0 0 100 130" aria-label="Ілюстрація флакона">
    <rect x="38" y="5" width="24" height="19" rx="3"
      fill="#777"/>
    <rect x="31" y="23" width="38" height="10" rx="3"
      fill="#555"/>
    <rect x="19" y="31" width="62" height="88" rx="10"
      fill="${colors[id]}" stroke="#aaa" stroke-width="2"/>
    <rect x="25" y="39" width="50" height="70" rx="6"
      fill="#181818" opacity="0.9"/>
    <text x="50" y="65" text-anchor="middle"
      fill="#eee" font-size="7">IVK</text>
    <line x1="32" y1="72" x2="68" y2="72"
      stroke="#aaa" stroke-width="0.7"/>
    <text x="50" y="83" text-anchor="middle"
      fill="#eee" font-size="5">PARFUME</text>
    <text x="50" y="94" text-anchor="middle"
      fill="#ccc" font-size="4">5 ML</text>
  </svg>`;
}

function renderProducts() {
  document.getElementById("products").innerHTML = perfumes.map(p => `
    <article class="product">
      <div class="bottle">${bottleSVG(p.id)}</div>
      <h3>${p.name}</h3>
      <p>${p.description}</p>
      <span class="price">${p.price} грн / 5 мл</span>
      <button class="btn" onclick="addToCart(${p.id})">
        Додати в кошик
      </button>
    </article>
  `).join("");
}

function addToCart(id) {
  const perfume = perfumes.find(p => p.id === id);
  const existing = cart.find(p => p.id === id);

  if (existing) {
    existing.quantity++;
  } else {
    cart.push({...perfume, quantity: 1});
  }

  renderCart();
  document.getElementById("count").textContent =
    cart.reduce((sum, p) => sum + p.quantity, 0);
}

function changeQuantity(id, amount) {
  const item = cart.find(p => p.id === id);
  if (!item) return;

  item.quantity += amount;
  if (item.quantity <= 0) {
    cart = cart.filter(p => p.id !== id);
  }
  renderCart();
  document.getElementById("count").textContent =
    cart.reduce((sum, p) => sum + p.quantity, 0);
}

function renderCart() {
  const container = document.getElementById("cartItems");

  if (cart.length === 0) {
    container.innerHTML = '<p class="empty">Кошик поки порожній.</p>';
  } else {
    container.innerHTML = cart.map(p => `
      <div class="item">
        <strong>${p.name}</strong><br>
        ${p.price} грн × ${p.quantity} = ${p.price * p.quantity} грн<br>
        <button onclick="changeQuantity(${p.id}, -1)">−</button>
        <button onclick="changeQuantity(${p.id}, 1)">+</button>
      </div>
    `).join("");
  }

  const sum = cart.reduce((total, p) =>
    total + p.price * p.quantity, 0);

  document.getElementById("total").textContent = "Разом: " + sum + " грн";
}

function showPage(page) {
  document.getElementById("shop").style.display =
    page === "shop" ? "block" : "none";

  ["cart", "profile", "about"].forEach(id => {
    document.getElementById(id).style.display =
      id === page ? "block" : "none";
  });

  if (page === "cart") renderCart();
  window.scrollTo(0, 0);
}

function saveProfile() {
  const name = document.getElementById("customerName").value.trim();
  const phone = document.getElementById("customerPhone").value.trim();

  if (!name || !phone) {
    document.getElementById("profileMessage").textContent =
      "Заповни ім'я та номер телефону.";
    return;
  }

  try {
    localStorage.setItem("ivkName", name);
    localStorage.setItem("ivkPhone", phone);
    document.getElementById("profileMessage").textContent =
      "Дані збережено на цьому пристрої.";
  } catch (e) {
    document.getElementById("profileMessage").textContent =
      "Не вдалося зберегти дані.";
  }
}

function order() {
  if (cart.length === 0) {
    alert("Спочатку додай аромат до кошика.");
    return;
  }

  const name = document.getElementById("customerName").value.trim()
    || localStorage.getItem("ivkName") || "";
  const phone = document.getElementById("customerPhone").value.trim()
    || localStorage.getItem("ivkPhone") || "";

  const lines = cart.map(p =>
    `${p.name} — ${p.quantity} шт. × ${p.price} грн`
  ).join("\n");

  const sum = cart.reduce((total, p) =>
    total + p.price * p.quantity, 0);

  const message =
    `Замовлення IVK PARFUME\n` +
    `Ім'я: ${name || "не вказано"}\n` +
    `Телефон: ${phone || "не вказано"}\n\n` +
    `${lines}\n\nРазом: ${sum} грн`;

  window.open(
    "https://t.me/share/url?url=" +
    encodeURIComponent("https://t.me/prechep") +
    "&text=" + encodeURIComponent(message),
    "_blank"
  );
}

try {
  document.getElementById("customerName").value =
    localStorage.getItem("ivkName") || "";
  document.getElementById("customerPhone").value =
    localStorage.getItem("ivkPhone") || "";
} catch (e) {}

renderProducts();
renderCart();
showPage("shop");
</script>

</body>
</html>
