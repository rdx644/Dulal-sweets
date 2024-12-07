<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dulal Sweets - Sweetness Redefined</title>
    <style>
        /* General Styling */
        body {
            font-family: 'Garamond', serif;
            margin: 0;
            padding: 0;
            background-color:#69e7fa;
            color: #333;
        }    
        header {
            background: linear-gradient(45deg, #00e8f4, #f8038e);
            color: rgb(243, 243, 249);
            text-align: center;
            padding: 20px 10px;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        header h1 {
            margin: 0;
            font-size: 2.5rem;
        }

        header nav a {
            margin: 0 15px;
            text-decoration: none;
            color: rgb(248, 244, 244);
            font-weight: bold;
            font-size: 1.2rem;
        }

        header nav a:hover {
            text-decoration: underline;
        }
        
        .hero {
            background-image: url('https://source.unsplash.com/1600x400/?sweets,indian');
            background-size: cover;
            background-position: center;
            height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.8);
            text-align: center;
            font-weight: bold;
        }

        .hero h2 {
            font-size: 3rem;
            margin: 0;
        }

        section {
            padding: 20px;
            max-width: 1200px;
            margin: auto;
        }

        #menu {
            background: #f8f4f4;
            border-radius: 10px;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .menu-item {
            background: #c2fafa;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .menu-item h3 {
            margin: 0;
            color: #ff5722;
        }

        .menu-item p {
            margin: 10px 0;
            font-size: 1rem;
            color: #555;
        }

        .menu-item input {
            width: 60px;
            padding: 5px;
            margin-top: 10px;
        }

        .menu-item button {
            margin-top: 10px;
            padding: 10px 20px;
            border: none;
            background: #f4b400;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }

        .menu-item button:hover {
            background: #d69700;
        }

        #total-bill {
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
            margin-top: 20px;
        }

        footer {
            background: #333;
            color: rgb(124, 221, 251);
            text-align: center;
            padding: 10px 20px;
            margin-top: 40px;
        }

        footer a {
            color: #f4b400;
            text-decoration: none;
        }

        footer a:hover {
            text-decoration: underline;
        }
        #qr-code-container {
            text-align: center;
            margin-top: 20px;
        }

        #qr-code {
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>DULAL SWEETS</h1>
        <nav>
            <a href="#" onclick="showPage('home')">Home</a>
            <a href="#" onclick="showPage('Menu')">Menu</a>
            <a href="#" onclick="showPage('Contact')">Contact</a>
            <a href="#" oneclick="showPage('feedback')">Feedback</a>
        </nav>
    </header>

    <div class="hero">
        <!-- Home Section -->
        <section id="home">
        <h2>Welcome to Dulal Sweets</h2>
        <h2>Sweetness Delivered with Love!</h2>
    </div>
    <!-- Menu Section -->
    <section id="Menu">
        <h2>Our Menu</h2>
        <div class="menu-grid">
            <div class="menu-item">
                <h3>Gulab Jamun</h3>
                <p>₹15 each</p>
                <input type="number" id="gulab-jamun" min="0" value="0">
            </div>
            <div class="menu-item">
                <h3>Rasgulla</h3>
                <p>₹20 each</p>
                <input type="number" id="rasgulla" min="0" value="0">
            </div>
            <div class="menu-item">
                <h3>Sandesh</h3>
                <p>₹25 each</p>
                <input type="number" id="sandesh" min="0" value="0">
            </div>
        </div>
        <div style="text-align: center; margin-top: 20px;">
            <button onclick="calculateBill()">Calculate Total</button>
        </div>
        <p id="total-bill">Total: ₹0</p>
        <button id="pay-button" onclick="generateQRCode()" style="display: none;">Proceed to Pay</button>
        <div id="qr-code-container" style="display: none;">
            <h3>Scan to Pay</h3>
            <img id="qr-code" alt="UPI QR Code">
        </div>    
    </section>
    <div class="hero">
        <!-- Contact Section -->
    <section id="Contact" style="display: none;">
        <h2>Contact Us</h2>
        <p><b>Address:</b>4th Lane Netaji Nagar Kantatoli Ranchi-834001 Jharkhand </p>
        <p><b>Phone:</b> +91 9430355778</p>
        <p><b>Email:</b> dulalsweets@gmail.com</p>
    </section>

    <!-- Feedback Section -->
    <section id="feedback" style="display: none;">
        <h2>We Value Your Feedback</h2>
        <form>
            <label for="name">Your Name:</label>
            <input type="text" id="name" required>

            <label for="feedback">Your feedback:</label>
            <textarea id="feedback" rows="5" required></textarea>

            <button type="submit">Submit</button>
        </form>
    </section>
</div>

<footer>
    <p>&copy; 2024 Dulal Sweets. All rights reserved.</p>
</footer>

    <script>
        // JavaScript for Page Navigation
        function showPage(pageId) {
            const sections = document.querySelectorAll("section");
            sections.forEach(section => {
                section.style.display = section.id === pageId ? "block" : "none";
            });
        }
        /* JavaScript */
        function calculateBill() {
            const gulabJamunPrice = 15;
            const rasgullaPrice = 20;
            const sandeshPrice = 25;

            let gulabJamunQty = document.getElementById("gulab-jamun").value || 0;
            let rasgullaQty = document.getElementById("rasgulla").value || 0;
            let sandeshQty = document.getElementById("sandesh").value || 0;

            let total = (gulabJamunQty * gulabJamunPrice) +
                        (rasgullaQty * rasgullaPrice) +
                        (sandeshQty * sandeshPrice);

            document.getElementById("total-bill").innerText = `Total: ₹${total}`;
            if (total > 0) {
                document.getElementById("pay-button").style.display = "block";
            }
        }
        // Generate QR Code for Payment
        function generateQRCode(){
            const totalText = document.getElementById("order-total").innerText;
            const totalAmount = totalText.match(/\d+/)[0]; // Extract amount
            const upiId = "putitundishubham@okhdfcbank"; // Replace with actual UPI ID
            const name = "Dulal Sweets";
            const upiLink = `upi://pay?pa=putitundishubham@okhdfcbank&pn=Dulal Sweets&am=${totalAmount}&cu=INR`;7
            const encodedLink = encodeURIComponent(upiLink);
            const qrCodeUrl = `https://chart.googleapis.com/chart?chs=300x300&cht=qr&chl=${encodeURIComponent(upiLink)}`;
            document.getElementById("qr-code").src = qrCodeUrl;
            document.getElementById("qr-code-container").style.display = "block";
        }
    </script>
</body>
</html>
