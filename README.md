<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Goa Star Lottery Result</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #8b0000;
      color: white;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 700px;
      margin: auto;
      padding: 20px;
      background: #fff;
      color: #000;
      position: relative;
    }
    .logo {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 120px;
      height: auto;
      max-width: 100%;
    }
    .header {
      background: #b30000;
      padding: 15px;
      text-align: center;
      color: yellow;
      font-size: 20px;
      font-weight: bold;
    }
    .info {
      margin: 15px 0;
      font-size: 16px;
    }
    .info label {
      font-weight: bold;
    }
    .box-row {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
      flex-wrap: wrap;
    }
    .box {
      background: red;
      color: white;
      padding: 10px;
      text-align: center;
      font-weight: bold;
      flex: 1 1 24%;
      margin: 5px;
      box-sizing: border-box;
    }
    .scroll-box {
      font-size: 22px;
      height: 35px;
      background: #fff;
      color: #000;
      border: none;
      text-align: center;
      width: 100%;
      font-weight: bold;
      letter-spacing: 3px;
      transition: all 0.4s ease-in-out;
    }
    .scroll-input {
      margin-top: 5px;
      width: 60%;
      text-align: center;
      font-size: 14px;
      padding: 2px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      table-layout: fixed;
      word-wrap: break-word;
    }
    th, td {
      border: 1px solid black;
      padding: 10px;
      text-align: center;
      white-space: nowrap;
    }
    th {
      background: #b30000;
      color: white;
    }
    .note {
      color: red;
      font-weight: bold;
      background: #ffeeee;
      border: 1px solid red;
      padding: 8px;
      border-radius: 6px;
      text-align: center;
      font-size: 13px;
    }
    @media (max-width: 600px) {
      .box-row {
        flex-direction: column;
        align-items: stretch;
      }
      .box {
        flex: 1 1 100%;
      }
      .logo {
        width: 90px;
        top: 5px;
        right: 5px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <!-- ✅ নতুন লোগো ঠিক ভাবে বসানো -->
    <img class="logo" src="52d2a524-ecba-4dc2-bdd9-5da061869d4b.png" alt="Goa Lottery Logo" />

    <div class="header">GOA STAR RESULT DRAW</div>
    <div class="info">
      <p><label>Result Draw:</label> <span id="lastDrawTime"></span> &nbsp;&nbsp;&nbsp;
      <label>Date:</label> <span id="currentDate"></span></p>
      <p><label>Next Draw Time:</label> <span id="nextDrawTime"></span> &nbsp;&nbsp;&nbsp;
      <label>Time Remaining:</label> <span id="countdown">--:--</span></p>
      <p><label>Current Time:</label> <span id="currentTime"></span></p>
    </div>

    <div class="box-row">
      <div class="box">GA
        <div id="gaScroll" class="scroll-box">---</div>
        <input class="scroll-input" id="gaInput" maxlength="3" placeholder="Enter GA" />
      </div>
      <div class="box">SA
        <div id="saScroll" class="scroll-box">---</div>
        <input class="scroll-input" id="saInput" maxlength="3" placeholder="Enter SA" />
      </div>
      <div class="box">RA
        <div id="raScroll" class="scroll-box">---</div>
        <input class="scroll-input" id="raInput" maxlength="3" placeholder="Enter RA" />
      </div>
      <div class="box">GOA STAR
        <div id="goaScroll" class="scroll-box">-</div>
        <input class="scroll-input" id="goaInput" maxlength="1" placeholder="Enter GOA" />
      </div>
    </div>

    <table id="resultTable">
      <thead>
        <tr>
          <th>Result Slot</th>
          <th>GA</th>
          <th>SA</th>
          <th>RA</th>
          <th>Goa Star</th>
        </tr>
      </thead>
      <tbody id="resultBody"></tbody>
    </table>

    <p class="note">
      🎮 Game Time: <strong>8:00 AM</strong> to <strong>12:00 AM (midnight)</strong> — Only active during this time.
    </p>
  </div>

  <script>
    let lastDrawTimeStr = "";

    function isWithinActiveHours() {
      const now = new Date();
      const hours = now.getHours();
      return hours >= 8 || hours === 0;
    }

    function flickerScroll(id, value, onDone) {
      let counter = 0;
      const el = document.getElementById(id);
      const len = value.length;
      const interval = setInterval(() => {
        if (counter >= 30) {
          clearInterval(interval);
          el.textContent = value;
          if (onDone) onDone();
        } else {
          let temp = "";
          for (let i = 0; i < len; i++) {
            temp += Math.floor(Math.random() * 10);
          }
          el.textContent = temp;
          counter++;
        }
      }, 60);
    }

    function updateTimeDisplays() {
      const now = new Date();
      let hours = now.getHours();
      let minutes = now.getMinutes();
      let seconds = now.getSeconds();

      let ampm = hours >= 12 ? 'PM' : 'AM';
      let h12 = hours % 12;
      h12 = h12 ? h12 : 12;
      let h = String(h12).padStart(2, '0');
      let m = String(minutes).padStart(2, '0');
      let s = String(seconds).padStart(2, '0');
      document.getElementById("currentTime").textContent = `${h}:${m}:${s} ${ampm}`;

      let d = String(now.getDate()).padStart(2, '0');
      let mo = String(now.getMonth() + 1).padStart(2, '0');
      let y = now.getFullYear();
      document.getElementById("currentDate").textContent = `${d}-${mo}-${y}`;

      const isActive = isWithinActiveHours();

      if (isActive) {
        let next = new Date(now.getTime() + 60000);
        let nextHours = next.getHours();
        let nextMinutes = next.getMinutes();
        let nextAMPM = nextHours >= 12 ? 'PM' : 'AM';
        let nextH12 = nextHours % 12;
        nextH12 = nextH12 ? nextH12 : 12;
        let nextH = String(nextH12).padStart(2, '0');
        let nextM = String(nextMinutes).padStart(2, '0');
        document.getElementById("nextDrawTime").textContent = `${nextH}:${nextM} ${nextAMPM}`;

        let diff = 60 - seconds;
        let cdMin = String(Math.floor(diff / 60)).padStart(2, '0');
        let cdSec = String(diff % 60).padStart(2, '0');
        document.getElementById("countdown").textContent = `${cdMin}:${cdSec}`;

        if (seconds === 0) {
          const ga = document.getElementById("gaInput").value || "---";
          const sa = document.getElementById("saInput").value || "---";
          const ra = document.getElementById("raInput").value || "---";
          const goa = document.getElementById("goaInput").value || "-";

          flickerScroll("gaScroll", ga);
          flickerScroll("saScroll", sa);
          flickerScroll("raScroll", ra);
          flickerScroll("goaScroll", goa, () => {
            let rowTime = `${h}:${m} ${ampm}`;
            document.getElementById("lastDrawTime").textContent = rowTime;
            if (rowTime !== lastDrawTimeStr) {
              lastDrawTimeStr = rowTime;
              addNewResultRow(rowTime, ga, sa, ra, goa);
              document.getElementById("gaInput").value = "";
              document.getElementById("saInput").value = "";
              document.getElementById("raInput").value = "";
              document.getElementById("goaInput").value = "";
            }
          });
        }
      } else {
        document.getElementById("nextDrawTime").textContent = `--`;
        document.getElementById("countdown").textContent = `⏸ Paused till 8 AM`;
      }
    }

    function addNewResultRow(timeStr, ga, sa, ra, goa) {
      const tbody = document.getElementById("resultBody");
      const newRow = document.createElement("tr");
      newRow.innerHTML = `
        <td>${timeStr}</td>
        <td>${ga}</td>
        <td>${sa}</td>
        <td>${ra}</td>
        <td>${goa}</td>
      `;
      tbody.prepend(newRow);
    }

    setInterval(updateTimeDisplays, 1000);
    updateTimeDisplays();
  </script>
</body>
</html>
