<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Wonderslapp S&R Monay</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f9ff;
      color: #0d47a1;
      text-align: center;
      padding: 20px;
    }
    input, button {
      margin: 10px;
      padding: 10px;
      width: 80%;
      border: 1px solid #90caf9;
      border-radius: 5px;
      font-size: 16px;
    }
    button {
      background: #ffca28;
      color: #000;
      border: none;
      cursor: pointer;
      font-weight: bold;
    }
    .top-bar {
      background: #0d47a1;
      color: white;
      display: flex;
      justify-content: space-between;
      padding: 10px;
      margin-bottom: 20px;
      border-radius: 5px;
    }
  </style>
</head>
<body>

  <!-- ✅ Registration -->
  <div id="register-section">
    <h2>Lembetsani</h2>
    <input type="text" placeholder="Zina Loyamba" id="firstName" />
    <input type="text" placeholder="Zina Lachiwiri" id="lastName" />
    <input type="text" placeholder="Phone Number" id="regPhone" />
    <input type="password" placeholder="Password" id="regPass" />
    <button onclick="register()">Lembetsani</button>
  </div>

  <!-- 🔐 Login -->
  <div id="login-section" style="display:none;">
    <h2>Lowani</h2>
    <input type="text" placeholder="Phone Number" id="loginPhone" />
    <input type="password" placeholder="Password" id="loginPass" />
    <button onclick="login()">Lowani</button>
  </div>

  <!-- 💼 Dashboard -->
  <div id="dashboard" style="display:none;">
    <div class="top-bar">
      <span id="balance">💰 Balance: MK 10,000</span>
      <span class="notify">🔔 Mauthenga</span>
    </div>
    <h3>Tumizani Ndalama</h3>
    <input type="text" placeholder="Phone ya olandila" id="sendPhone" />
    <input type="number" placeholder="Ndalama zoti mutumize" id="sendAmount" />
    <button onclick="sendMoney()">Tumizani</button>
    <div id="message"></div>
  </div>

  <script>
    let userBalance = 10000;

    function register() {
      alert("Lembetsa bwino! Tsopano muyenera kulowa.");
      document.getElementById('register-section').style.display = "none";
      document.getElementById('login-section').style.display = "block";
    }

    function login() {
      alert("Mwalandira bwino! Welcome ku Monay.");
      document.getElementById('login-section').style.display = "none";
      document.getElementById('dashboard').style.display = "block";
    }

    function sendMoney() {
      let phone = document.getElementById("sendPhone").value;
      let amount = parseInt(document.getElementById("sendAmount").value);
      let messageBox = document.getElementById("message");

      if (isNaN(amount) || amount <= 0) {
        messageBox.innerText = "Lowetsani ndalama zomveka!";
        return;
      }

      if (amount > userBalance) {
        messageBox.innerText = "💥 Ndalama zikukwana ayi!";
        return;
      }

      userBalance -= amount;
      document.getElementById("balance").innerText = "💰 Balance: MK " + userBalance;
      messageBox.innerText = "✅ Mwatumiza MK" + amount + " kwa " + phone + ". Notification yatumizidwa.";
    }
  </script>

</body>
</html>