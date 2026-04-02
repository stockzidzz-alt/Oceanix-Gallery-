<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Oceanix Gallery | Keindahan Samudera</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        /* --- RESET & VARIABLES --- */
        :root {
            --deep-blue: #021024;
            --ocean-blue: #052659;
            --bright-blue: #00a6fb;
            --soft-blue: #b3e5fc;
            --white: #ffffff;
            --glass: rgba(255, 255, 255, 0.1);
            --transition: all 0.4s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--deep-blue);
            color: var(--white);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* --- NAVBAR --- */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 8%;
            z-index: 1000;
            background: rgba(2, 16, 36, 0.8);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid var(--glass);
        }

        .logo {
            font-size: 1.6rem;
            font-weight: 700;
            color: var(--bright-blue);
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .nav-menu a {
            color: var(--white);
            text-decoration: none;
            margin-left: 25px;
            font-size: 0.9rem;
            transition: var(--transition);
        }

        .nav-menu a:hover {
            color: var(--bright-blue);
        }

        /* --- HERO SECTION --- */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(2, 16, 36, 0.5), rgba(2, 16, 36, 0.8)), 
                        url('https://images.unsplash.com/photo-1505118380757-91f5f5832de0?auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        .hero h1 {
            font-size: clamp(2rem, 8vw, 4rem);
            margin-bottom: 15px;
            text-shadow: 0 5px 15px rgba(0,0,0,0.5);
        }

        .hero p {
            font-size: 1.1rem;
            max-width: 600px;
            margin-bottom: 30px;
            color: var(--soft-blue);
        }

        .btn-view {
            padding: 12px 35px;
            background: var(--bright-blue);
            color: var(--white);
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: var(--transition);
            box-shadow: 0 8px 20px rgba(0, 166, 251, 0.3);
        }

        .btn-view:hover {
            transform: translateY(-5px);
            background: #0084c7;
        }

        /* --- GALLERY SECTION --- */
        .gallery {
            padding: 100px 8%;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title h2 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .underline {
            width: 80px;
            height: 4px;
            background: var(--bright-blue);
            margin: 0 auto;
            border-radius: 2px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
        }

        .card {
            position: relative;
            height: 350px;
            border-radius: 20px;
            overflow: hidden;
            cursor: pointer;
            border: 1px solid var(--glass);
            transform: translateY(20px);
            opacity: 0;
            transition: all 0.6s ease-out;
        }

        .card.reveal {
            transform: translateY(0);
            opacity: 1;
        }

        .card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .card:hover img {
            transform: scale(1.1);
        }

        .overlay {
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(2, 16, 36, 0.9), transparent);
            display: flex;
            align-items: flex-end;
            padding: 25px;
            opacity: 0;
            transition: var(--transition);
        }

        .card:hover .overlay {
            opacity: 1;
        }

        .overlay h3 {
            font-size: 1.2rem;
            color: var(--bright-blue);
        }

        /* --- LIGHTBOX --- */
        #lightbox {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.95);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            padding: 20px;
        }

        #lightbox img {
            max-width: 90%;
            max-height: 85vh;
            border-radius: 10px;
            box-shadow: 0 0 30px rgba(0, 166, 251, 0.3);
        }

        .close-btn {
            position: absolute;
            top: 30px;
            right: 40px;
            font-size: 3rem;
            color: white;
            cursor: pointer;
        }

        /* --- FOOTER --- */
        footer {
            text-align: center;
            padding: 40px;
            background: #010a18;
            border-top: 1px solid var(--glass);
        }

        footer p {
            font-size: 0.85rem;
            opacity: 0.6;
        }

        /* RESPONSIVE */
        @media (max-width: 600px) {
            .nav-menu { display: none; }
            .gallery { padding: 60px 5%; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">Oceanix</div>
        <div class="nav-menu">
            <a href="#">Home</a>
            <a href="#gallery">Gallery</a>
        </div>
    </nav>

    <section class="hero">
        <h1>Explore the Beauty of the Ocean</h1>
        <p>Temukan ketenangan dan keajaiban dunia bawah laut melalui lensa fotografi yang menakjubkan.</p>
        <a href="#gallery" class="btn-view">View Gallery</a>
    </section>

    <section class="gallery" id="gallery">
        <div class="section-title">
            <h2>Gallery</h2>
            <div class="underline"></div>
        </div>

        <div class="grid">
            <div class="card">
                <img src="https://images.unsplash.com/photo-1519046904884-53103b34b206?auto=format&fit=crop&w=800&q=80" alt="Pantai Sore Hari">
                <div class="overlay"><h3>Serene Beach</h3></div>
            </div>

            <div class="card">
                <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=80" alt="Pantai Pasir Putih">
                <div class="overlay"><h3>White Sand Beach</h3></div>
            </div>

            <div class="card">
                <img src="https://images.unsplash.com/photo-1522163182402-834f871fd851?auto=format&fit=crop&w=800&q=80" alt="Peselancar Ombak Besar">
                <div class="overlay"><h3>Big Wave Surfing</h3></div>
            </div>

            <div class="card">
                <img src="https://images.unsplash.com/photo-1518837695005-2083093ee35b?auto=format&fit=crop&w=800&q=80" alt="Sunset Laut">
                <div class="overlay"><h3>Sunset Horizon</h3></div>
            </div>

            <div class="card">
                <img src="https://images.unsplash.com/photo-1544551763-46a013bb70d5?auto=format&fit=crop&w=800&q=80" alt="Penyu Laut">
                <div class="overlay"><h3>Sea Turtle Journey</h3></div>
            </div>

            <div class="card">
                <img src="https://images.unsplash.com/photo-1439405326854-014607f694d7?auto=format&fit=crop&w=800&q=80" alt="Biru Laut">
                <div class="overlay"><h3>Crystal Water</h3></div>
            </div>
        </div>
    </section>

    <div id="lightbox">
        <span class="close-btn">&times;</span>
        <img src="" alt="Full View" id="lightbox-img">
    </div>

    <footer>
        <p>&copy; 2026 Oceanix Gallery | Aesthetic Ocean Portfolio</p>
    </footer>

    <script>
        // Animasi Muncul saat Scroll (Reveal Animation)
        const cards = document.querySelectorAll('.card');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('reveal');
                }
            });
        }, { threshold: 0.1 });

        cards.forEach(card => observer.observe(card));

        // Fitur Lightbox (Klik gambar jadi besar)
        const lightbox = document.getElementById('lightbox');
        const lightboxImg = document.getElementById('lightbox-img');
        const closeBtn = document.querySelector('.close-btn');

        cards.forEach(card => {
            card.addEventListener('click', () => {
                const src = card.querySelector('img').src;
                lightboxImg.src = src;
                lightbox.style.display = 'flex';
                document.body.style.overflow = 'hidden'; // Kunci scroll
            });
        });

        closeBtn.addEventListener('click', () => {
            lightbox.style.display = 'none';
            document.body.style.overflow = 'auto'; // Aktifkan scroll lagi
        });

        // Klik di mana saja untuk tutup lightbox
        lightbox.addEventListener('click', (e) => {
            if (e.target !== lightboxImg) {
                lightbox.style.display = 'none';
                document.body.style.overflow = 'auto';
            }
        });
    </script>
</body>
</html>
