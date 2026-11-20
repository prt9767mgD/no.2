
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>2028 共通テストまで</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #0b0b0d;
      color: #f5f5f5;
      font-family: -apple-system, BlinkMacSystemFont, sans-serif;
      text-align: center;
    }

    .container {
      width: 90%;
      max-width: 700px;
    }

    .subtitle {
      color: #999;
      font-size: 13px;
      letter-spacing: 4px;
      margin-bottom: 25px;
    }

    h1 {
      font-size: 27px;
      font-weight: 400;
      letter-spacing: 3px;
      margin-bottom: 55px;
    }

    .countdown {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
    }

    .unit {
      min-width: 105px;
    }

    .number {
      font-size: clamp(38px, 9vw, 65px);
      font-weight: 300;
      font-variant-numeric: tabular-nums;
    }

    .label {
      color: #888;
      font-size: 12px;
      letter-spacing: 2px;
      margin-top: 10px;
    }

    .footer {
      margin-top: 65px;
      color: #555;
      font-size: 11px;
      letter-spacing: 2px;
    }
  </style>
</head>

<body>
  <main class="container">
    <p class="subtitle">THE COUNTDOWN</p>

    <h1>2028 共通テストまで</h1>

    <div class="countdown">
      <div class="unit">
        <div class="number" id="days">---</div>
        <div class="label">DAYS</div>
      </div>

      <div class="unit">
        <div class="number" id="hours">--</div>
        <div class="label">HOURS</div>
      </div>

      <div class="unit">
        <div class="number" id="minutes">--</div>
        <div class="label">MINUTES</div>
      </div>

      <div class="unit">
        <div class="number" id="seconds">--</div>
        <div class="label">SECONDS</div>
      </div>
    </div>

    <p class="footer">YOUR FUTURE STARTS HERE</p>
  </main>

  <script>
    // 仮の日程：2028年1月15日 9時30分（日本時間）
    const targetDate = new Date("2028-01-15T09:30:00+09:00");

    function updateCountdown() {
      const now = new Date();
      const difference = targetDate - now;

      if (difference <= 0) {
        document.querySelector(".countdown").innerHTML = "THE DAY HAS COME";
        return;
      }

      const days = Math.floor(difference / (1000 * 60 * 60 * 24));
      const hours = Math.floor((difference / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((difference / (1000 * 60)) % 60);
      const seconds = Math.floor((difference / 1000) % 60);

      document.getElementById("days").textContent = days;
      document.getElementById("hours").textContent = String(hours).padStart(2, "0");
      document.getElementById("minutes").textContent = String(minutes).padStart(2, "0");
      document.getElementById("seconds").textContent = String(seconds).padStart(2, "0");
    }

    updateCountdown();
    setInterval(updateCountdown, 1000);
  </script>
</body>
</html>
