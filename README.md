[index.html](https://github.com/user-attachments/files/21825156/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fashion Store</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">

  <!-- Material Icons + Font Awesome -->
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

  <style>
  /* Loader */
  #loader {
    position: fixed; top:0; left:0; width:100%; height:100%;
    background:#fff; z-index:9999; display:flex;
    align-items:center; justify-content:center;
    transition:opacity 0.6s ease;
  }
  #loader.fade-out { opacity:0; pointer-events:none; }
  .spinner {
    border: 6px solid #eee;
    border-top: 6px solid #ff9800;
    border-radius: 50%;
    width: 60px; height: 60px;
    animation: spin 1s linear infinite;
  }
  @keyframes spin { 0%{transform:rotate(0)} 100%{transform:rotate(360deg)} }

  /* Reset */
  *{margin:0;padding:0;box-sizing:border-box}
  body{font-family:Arial,sans-serif;background:#f4f4f4;color:#333;line-height:1.5}

  /* Header */
  header{
    background:black;color:white;padding:12px 20px;
    display:flex;justify-content:space-between;align-items:center;
    flex-wrap:wrap;
  }
  header h1{
    font-size:60px;color:#ff9800;font-weight:900;
    font-family:'Great Vibes',cursive;
  }
  .logo{display:flex;align-items:center;gap:15px}
  #img{width:80px;height:80px;border-radius:50%;object-fit:cover}
  nav{display:flex;gap:15px;flex-wrap:wrap}
  nav a{
    padding:8px 16px;border-radius:8px;
    font-size:15px;font-weight:bold;text-transform:uppercase;
    color:#fff;text-decoration:none;transition:0.3s;
  }
  nav a i{margin-right:6px}
  nav a:hover{background:#ff9800;color:black}

  /* Hero */
  .hero{
    position:relative;height:600px;
    display:flex;align-items:center;justify-content:center;
    color:white;text-align:center;overflow:hidden;
  }
  .hero::before{
    content:"";position:absolute;top:0;left:0;width:100%;height:100%;
    background:rgba(0,0,0,0.4);z-index:1;
  }
  .hero h2{
    font-size:50px;background:rgba(0,0,0,0.5);
    padding:20px 30px;border-radius:10px;z-index:2;
  }
  .hero.fade-out{opacity:0.6;transition:opacity 1s ease}

  /* Shop */
  .shop{
    padding:40px;display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:20px;
  }
  .product{
    background:#fff;padding:15px;border-radius:10px;
    box-shadow:0 4px 6px rgba(0,0,0,0.1);text-align:center;
    transition:transform 0.3s ease;
  }
  .product:hover{transform:translateY(-5px)}
  .product img{width:100%;height:250px;object-fit:cover;border-radius:8px}
  .product h3{margin:10px 0}
  .product p{color:#777}
  .product button{
    background:#222;color:white;border:none;
    padding:10px 15px;margin-top:10px;cursor:pointer;
    border-radius:5px;font-weight:bold;
    transition:background 0.3s ease;
  }
  .product button:hover{background:#ff9800;color:black}

  /* Cart Modal */
  .cart-modal{
    display:none;position:fixed;top:0;right:0;width:350px;height:100%;
    background:white;box-shadow:-2px 0 8px rgba(0,0,0,0.2);
    padding:20px;overflow-y:auto;z-index:1000;
  }
  .cart-modal h2{margin-bottom:15px}
  .cart-item{display:flex;justify-content:space-between;align-items:center;margin:10px 0}
  .cart-item span{font-size:14px}
  .cart-item button{
    background:transparent;color:#ff9800;border:none;padding:4px 8px;
    border-radius:4px;cursor:pointer
  }
  .close-btn{
    background:#333;color:white;border:none;padding:6px 12px;
    border-radius:5px;cursor:pointer;margin-bottom:15px;
  }

  /* General Modal */
  .modal{
    display:none;position:fixed;top:0;left:0;width:100%;height:100%;
    background:rgba(0,0,0,0.7);justify-content:center;align-items:center;
    z-index:1000;
  }
  .modal-content{
    background:#fff;padding:30px;border-radius:10px;
    width:90%;max-width:450px;position:relative;
    border:6px solid #ff9800;
  }
  .modal-content h2{text-align:center;margin-bottom:15px}
  .modal-content form{display:flex;flex-direction:column}
  .modal-content input,.modal-content textarea{
    margin:10px 0;padding:10px;border:1px solid #ccc;border-radius:5px
  }
  .modal-content button{
    background:#222;color:white;padding:10px;border:none;border-radius:5px;
    cursor:pointer;font-weight:bold;text-transform:uppercase;
    transition:0.3s;
  }
  .modal-content button:hover{background:#ff9800;color:black}
  .modal .close-btn{
    position:absolute;top:10px;right:15px;background:transparent;
    color:#ff9800;font-size:20px;font-weight:bold;cursor:pointer;
  }
  .switch-link{
    color:#ff9800;cursor:pointer;margin-top:10px;display:block;text-align:center
  }

  /* Footer */
  footer{
    background:#222;color:white;text-align:center;
    padding:15px;margin-top:20px
  }
  .social i{margin:0 10px;cursor:pointer}
  .social i:hover{color:#ff9800}

  /* Scroll-to-top */
  #scrollTopBtn{
    position:fixed;bottom:20px;right:20px;display:none;
    padding:10px 15px;border-radius:50%;border:none;
    background:#ff9800;color:black;cursor:pointer;
    z-index:1000;font-size:18px;transition:background 0.3s;
  }
  #scrollTopBtn:hover{background:#333;color:#fff}

  @media(max-width:600px){
    header h1{font-size:40px}
    .hero h2{font-size:28px}
  }
  </style>
</head>
<body>

<!-- Loader -->
<div id="loader"><div class="spinner"></div></div>

<!-- Header -->
<header>
  <div class="logo">
    <img src="https://i.postimg.cc/8CdLZHtZ/a-boutique-2.jpg" alt="Logo" id="img">
    <h1>Fashion Store</h1>
  </div>
  <nav>
    <a href="#"><i class="fas fa-home"></i>Home</a>
    <a href="#shop" id="auth-btn"><i class="fas fa-user-plus"></i>SignUp/Login</a>
    <a href="#" id="cart-btn"><i class="fa fa-shopping-cart"></i> Cart</a>
    <a href="#" id="contact-btn"><i class="fas fa-phone"></i>Contact</a>
  </nav>
</header>

<!-- Hero -->
<section class="hero">
  <h2>New Collection Out Now!</h2>
</section>

<!-- Shop -->
<section id="shop" class="shop">
  <div class="product">
    <img src="https://i.postimg.cc/sgFhKThx/boss.jpg " alt="Shirt">
    <h3>Classic Shirt</h3>
    <p>$25</p>
    <button onclick="addToCart('Classic Shirt',25)">Add to Cart</button>
  </div>
  <div class="product">
    <img src="https://i.postimg.cc/RhNpHy43/a-boutique.jpg " alt="Dress">
    <h3>Elegant Dress</h3>
    <p>$40</p>
    <button onclick="addToCart('Elegant Dress',40)">Add to Cart</button>
  </div>
  <div class="product">
    <img src="https://i.postimg.cc/1RBNnXjN/a-boutique-3.jpg " alt="Jacket">
    <h3>Leather Jacket</h3>
    <p>$60</p>
    <button onclick="addToCart('Leather Jacket',60)">Add to Cart</button>
  </div>
</section>

<!-- Cart Modal -->
<div class="cart-modal" id="cart">
  <button class="close-btn" onclick="closeCart()">✖</button>
  <h2>Your Cart</h2>
  <div id="cart-items"></div>
  <h3>Total: $<span id="cart-total">0</span></h3>
</div>

<!-- Contact Modal -->
<div class="modal" id="contact-modal">
  <div class="modal-content">
    <button class="close-btn" onclick="closeContact()">✖</button>
    <h2>Contact Us</h2>
    <form action="mailto:eyemivictor@gmail.com" method="post" enctype="text/plain">
      <input type="text" placeholder="Your Name" required>
      <input type="email" placeholder="Your Email" required>
      <textarea placeholder="Your Message" rows="4" required></textarea>
      <button type="submit">Send Message</button>
    </form>
  </div>
</div>

<!-- Signup/Login Modal -->
<div class="modal" id="auth-modal">
  <div class="modal-content">
    <button class="close-btn" onclick="closeAuth()">✖</button>
    
    <!-- Signup -->
    <div id="signup-form">
      <h2>Sign Up</h2>
      <form>
        <input type="text" placeholder="Full Name" required>
        <input type="email" placeholder="Email" required>
        <input type="password" placeholder="Password" required>
        <button type="submit">Sign Up</button>
      </form>
      <span class="switch-link" onclick="showLogin()">Already have an account? Login</span>
    </div>

    <!-- Login -->
    <div id="login-form" style="display:none;">
      <h2>Login</h2>
      <form>
        <input type="email" placeholder="Email" required>
        <input type="password" placeholder="Password" required>
        <button type="submit">Login</button>
      </form>
      <span class="switch-link" onclick="showSignup()">Don't have an account? Sign Up</span>
    </div>
  </div>
</div>

<!-- Footer -->
<footer>
  <p>&copy; 2025 Fashion Store. All Rights Reserved.</p>
  <div class="social">
    <i class="fab fa-facebook"></i>
    <i class="fab fa-instagram"></i>
    <i class="fab fa-twitter"></i>
  </div>
</footer>

<!-- Scroll-to-top -->
<button id="scrollTopBtn"><i class="fas fa-arrow-up"></i></button>

<script>
let cart=[];

// Add to cart
function addToCart(product,price){
  let existing=cart.find(item=>item.product===product);
  if(existing){existing.qty++}
  else{cart.push({product,price,qty:1})}
  updateCart();
  alert(product+" added to cart!");
}

// Update cart
function updateCart(){
  let cartItems=document.getElementById("cart-items");
  let cartTotal=document.getElementById("cart-total");
  cartItems.innerHTML=""; let total=0;
  cart.forEach((item,i)=>{
    let div=document.createElement("div");
    div.classList.add("cart-item");
    div.innerHTML=`<span>${item.product} (x${item.qty})</span>
                   <span>$${item.price*item.qty}</span>
                   <button onclick="removeItem(${i})">X</button>`;
    cartItems.appendChild(div);
    total+=item.price*item.qty;
  });
  cartTotal.textContent=total;
}

// Remove from cart
function removeItem(index){
  cart.splice(index,1);
  updateCart();
}

// Cart modal
document.getElementById("cart-btn").addEventListener("click",()=>{document.getElementById("cart").style.display="block"});
function closeCart(){document.getElementById("cart").style.display="none"}

// Contact modal
document.getElementById("contact-btn").addEventListener("click",e=>{
  e.preventDefault();document.getElementById("contact-modal").style.display="flex"});
function closeContact(){document.getElementById("contact-modal").style.display="none"}

// Auth modal
document.getElementById("auth-btn").addEventListener("click",e=>{
  e.preventDefault();document.getElementById("auth-modal").style.display="flex"});
function closeAuth(){document.getElementById("auth-modal").style.display="none"}
function showLogin(){document.getElementById("signup-form").style.display="none";document.getElementById("login-form").style.display="block"}
function showSignup(){document.getElementById("login-form").style.display="none";document.getElementById("signup-form").style.display="block"}

// Hero slideshow
const hero=document.querySelector(".hero");
const heroImages=[
  "https://i.postimg.cc/1RBNnXjN/a-boutique-3.jpg",
  "https://i.postimg.cc/RhNpHy43/a-boutique.jpg",
  "https://i.postimg.cc/1RBNnXjN/a-boutique-3.jpg",
  "https://i.postimg.cc/sgFhKThx/boss.jpg"
];
let heroIndex=0;
function changeHeroBackground(){
  hero.classList.add("fade-out");
  setTimeout(()=>{
    hero.style.background=`url('${heroImages[heroIndex]}') no-repeat center center/cover`;
    hero.classList.remove("fade-out");
  },1000);
}
setInterval(()=>{heroIndex=(heroIndex+1)%heroImages.length;changeHeroBackground()},6000);

// Loader
window.addEventListener("load",()=>{
  setTimeout(()=>{
    document.getElementById("loader").classList.add("fade-out");
  },1000);
});

// Scroll-to-top
const scrollTopBtn=document.getElementById("scrollTopBtn");
window.addEventListener("scroll",()=>{
  if(window.scrollY>300){scrollTopBtn.style.display="block"}
  else{scrollTopBtn.style.display="none"}
});
scrollTopBtn.addEventListener("click",()=>{window.scrollTo({top:0,behavior:"smooth"})});
</script>
</body>
</html>
