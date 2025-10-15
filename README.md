<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Acek Dewa Balap - Launching Film</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Arial', sans-serif;
    }

    body {
      overflow: hidden;
      background: #0a0a0a;
      color: #fff;
      text-align: center;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    header {
      z-index: 2;
      position: relative;
      margin-bottom: 20px;
    }

    header h1 {
      font-size: 3rem;
      color: #ff0000;
      text-shadow: 2px 2px 15px #000;
    }

    header p {
      font-size: 1.2rem;
      margin-top: 10px;
      color: #ffd700;
      text-shadow: 1px 1px 5px #000;
    }

    .poster {
      width: 300px;
      max-width: 80%;
      border: 5px solid #ff0000;
      border-radius: 10px;
      box-shadow: 0 0 20px #ff0000;
      margin-bottom: 20px;
      transition: transform 0.3s;
      z-index: 2;
      position: relative;
    }

    .poster:hover {
      transform: scale(1.05);
    }

    .info {
      z-index: 2;
      position: relative;
      margin-bottom: 20px;
    }

    .info p {
      margin: 5px 0;
      font-size: 1rem;
    }

    .countdown {
      font-size: 2rem;
      font-weight: bold;
      color: #00ffea;
      margin-bottom: 20px;
      text-shadow: 2px 2px 10px #000;
      z-index: 2;
      position: relative;
    }

    .cta-button {
      background-color: #ff0000;
      color: #fff;
      border: none;
      padding: 15px 30px;
      font-size: 1.2rem;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
      text-decoration: none;
      z-index: 2;
      position: relative;
    }

    .cta-button:hover {
      background-color: #cc0000;
    }

    footer {
      z-index: 2;
      position: relative;
      margin-top: 30px;
      font-size: 0.9rem;
      color: #888;
    }

    /* Background Animation */
    .car-container {
      position: absolute;
      bottom: 50px;
      left: -250px;
      z-index: 1;
      width: 200px;
    }

    .car {
      width: 100%;
      filter: drop-shadow(0 0 10px #ff0000) drop-shadow(0 0 10px #00ffea);
      transition: transform 0.1s;
    }

    .smoke {
      position: absolute;
      width: 60px;
      height: 30px;
      background: radial-gradient(circle, rgba(200,200,200,0.5) 0%, rgba(0,0,0,0) 70%);
      border-radius: 50%;
      opacity: 0.7;
      bottom: 0;
      left: 70px;
      z-index: 0;
      animation: smoke-rise 1s linear infinite;
    }

    @keyframes smoke-rise {
      0% { transform: translateY(0) scale(0.8); opacity: 0.7; }
      50% { transform: translateY(-20px) scale(1); opacity: 0.5; }
      100% { transform: translateY(-40px) scale(1.2); opacity: 0; }
    }
  </style>
</head>
<body>
  <header>
    <h1>Acek Dewa Balap</h1>
    <p>Kecepatan adalah kekuatan. Keluarga adalah segalanya.</p>
  </header>

  <img src="https://art-global.faceai.art/face-swap/848b4c55f4670232c126de2c937d39cc.webp" alt="Poster Acek Dewa Balap" class="poster">

  <div class="info">
    <p><strong>Aktot Utama:</strong> Cek Nelson</p>
    <p><strong>Sutradara:</strong> Martinus</p>
    <p><strong>Produser:</strong> Yoddy Sitanggang</p>
    <p><strong>Rumah Produksi:</strong> Isti Bordir</p>
    <p><strong>Tanggal Rilis:</strong> 28 Oktober 2025</p>
  </div>

  <div class="countdown" id="countdown"></div>

  <a href="#" class="cta-button" onclick="alert('Terima kasih! Tandai kalender Anda untuk 28 Oktober 2025!')">Tandai Tanggal Rilis</a>

  <footer>
    &copy; 2025 Isti Bordir. All Rights Reserved.
  </footer>

  <!-- Car Animation -->
  <div class="car-container" id="carContainer">
    <img src="mobil-drifting.png" alt="" class="car">
    <div class="smoke"></div>
  </div>

  <script>
    // Countdown Timer
    const countdownElement = document.getElementById('countdown');
    const releaseDate = new Date('2025-10-28T00:00:00');

    function updateCountdown() {
      const now = new Date();
      const diff = releaseDate - now;

      if(diff <= 0) {
        countdownElement.textContent = "Film Sudah Rilis!";
        clearInterval(interval);
        return;
      }

      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((diff / (1000 * 60)) % 60);
      const seconds = Math.floor((diff / 1000) % 60);

      countdownElement.textContent = `${days} Hari ${hours} Jam ${minutes} Menit ${seconds} Detik`;
    }

    const interval = setInterval(updateCountdown, 1000);
    updateCountdown();

    // Car drifting animation with slight vertical bounce and neon flicker
    const carContainer = document.getElementById('carContainer');
    let carPos = -250;
    let direction = 1;
    let neonOn = true;

    function animateCar() {
      carPos += 5;
      if(carPos > window.innerWidth + 250) carPos = -250;
      carContainer.style.left = carPos + 'px';

      // slight bounce
      const yOffset = Math.sin(carPos / 50) * 5;
      carContainer.style.transform = `translateY(${yOffset}px)`;

      // neon flicker
      neonOn = !neonOn;
      carContainer.querySelector('.car').style.filter = neonOn 
        ? 'drop-shadow(0 0 15px #ff0000) drop-shadow(0 0 15px #00ffea)' 
        : 'drop-shadow(0 0 8px #ff0000) drop-shadow(0 0 8px #00ffea)';

      requestAnimationFrame(animateCar);
    }
    animateCar();
  </script>
</body>
</html>
