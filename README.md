

<html lang="en">

<head>
  <title>SCIENTIFIC CALCULATOR</title>
  <style>
    * {
      box-sizing: border-box;
    }
    .Calculator-body {
      height: 400px; /* Increased height for dual display */
      width: 280px;
      background: linear-gradient(rgba(0, 157, 255, 0.781),rgba(14, 43, 105, 0.725),rgba(162, 34, 20, 0.911));
      margin: 20px auto;
      border-radius: 10px;
      padding: 20px;
    }

    /* Container for the dual screen */
    .screen-wrapper {
      background-color: #86994c;
      border: 3.5px solid #0c0505;
      margin-bottom: 15px;
      padding: 5px;
      height: 100px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    /* Small top line for the input equation */
    #history {
      font-size: 14px;
      color: #f00707;
      text-align: right;
      height: 20px;
      overflow: hidden;
      background-color: #86994c;
       
    }

    /* Main bottom line for the result */
    .screen {
      background: transparent;
      text-align: right;
      width: 100%;
      border: none;
      font-size: 30px;
      outline: none;
    }

    .button-container {
      background-image: url(   https://scontent.fktm20-1.fna.fbcdn.net/v/t39.30808-6/577532479_1823292988315891_1926417523176076930_n.jpg?stp=dst-jpg_tt6&cstp=mx960x1280&ctp=s960x1280&_nc_cat=108&ccb=1-7&_nc_sid=6ee11a&_nc_ohc=EGcPyGmP2MYQ7kNvwEVY9kN&_nc_oc=AdpP2Mn-w-XvwipQbC23MWRdpEZnZK4WeC5s74RejRsF-_Y5FbGi2Mg_NYAk3KE1Lc0ZyFVoj8LxTAOuXAKAz88b&_nc_zt=23&_nc_ht=scontent.fktm20-1.fna&_nc_gid=5oWu9fdPzUpmK7CLwwH_TA&_nc_ss=7b2a8&oh=00_Af8OGF-lCAx_oVL1_AquWgG23mZMgoLc1Qpt65G1tZ_wnA&oe=6A419FE1 );
      height: 240px;
      background-size: cover;
      background-repeat: no-repeat;
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;
      justify-content: flex-start;
      align-items: center;
      border-radius: 10px;
      padding: 5px;
    }
    .btn {
      width: 50px;
      height: 40px;
      text-align: center;
      font-size: 18px;
      margin: 3px;
      border: 0.5px solid black;
      cursor: pointer;
      border-radius: 9px;
      background-color: #fafafa;
    }
    .btn:hover {
      box-shadow: 0 0 20px #ff0000;
      background-color: #eaff04;
    }
    .btn-equals {
      background-color: rgb(237, 103, 14);
      height: 86px;
    }
  </style>
</head>
<body>
  <div class="Calculator-body">
    
    <!-- Dual Display Section -->
    <div class="screen-wrapper">
      <div id="history"> </div> <!-- SHOWS INPUT (e.g., 5+5=) -->
      <input type="text" id="result" class="screen" readonly placeholder="0000000000000" /> <!-- SHOWS OUTPUT (e.g., 10) -->
    </div>

    <div class="button-container">
      <button class="btn" onclick="clr()">AC</button>
      <button class="btn" onclick="dis('7')">7</button>
      <button class="btn" onclick="dis('4')">4</button>
      <button class="btn" onclick="dis('1')">1</button>
      <button class="btn" onclick="dis('0')">0</button>

      <button class="btn" onclick="dis('-')">+/-</button>
      <button class="btn" onclick="dis('8')">8</button>
      <button class="btn" onclick="dis('5')">5</button>
      <button class="btn" onclick="dis('2')">2</button>
      <button class="btn" onclick="dis('00')">00</button>

      <button class="btn" onclick="dis('/')">/</button>
      <button class="btn" onclick="dis('9')">9</button>
      <button class="btn" onclick="dis('6')">6</button>
      <button class="btn" onclick="dis('3')">3</button>
      <button class="btn" onclick="dis('.')">.</button>

      <button class="btn" onclick="dis('*')">*</button>
      <button class="btn" onclick="dis('-')">-</button>
      <button class="btn" onclick="dis('+')">+</button>
      <button class="btn btn-equals" onclick="solve()">=</button>
    </div>
  </div>

  <script>
    function dis(val) {
      document.getElementById("result").value += val;
    }

    function solve() {
      try {
        let input = document.getElementById("result").value;
        if (input === "") return;

        // Show the equation in the small top history line
        document.getElementById("history").innerText = input + " =";
        
        // Calculate result
        let output = eval(input);
        
        // Show the answer in the main big screen
        document.getElementById("result").value = output;
      } catch (e) {
        document.getElementById("result").value = "Error";
      }
    }

    function clr() {
      document.getElementById("result").value = "";
      document.getElementById("history").innerText = "";
    }

    // Support for keyboard
    window.onkeydown = function (event) {
      if ((event.key >= '0' && event.key <= '9') || ['+', '-', '*', '/', '.'].includes(event.key)) {
        dis(event.key);
      } else if (event.key === 'Enter') {
        solve();
      } else if (event.key === 'Backspace') {
        let str = document.getElementById("result").value;
        document.getElementById("result").value = str.substring(0, str.length - 1);
      }
    };
  </script>
</body>
</html>
