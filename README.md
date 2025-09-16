<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WAK INNOV - Étude Mécanique & Conception 3D</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #4facfe;
            --secondary-color: #00f2fe;
            --accent-color: #ff6b6b;
            --dark-color: #333;
            --light-color: #f9f9f9;
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--light-color);
            color: var(--dark-color);
            line-height: 1.6;
            scroll-behavior: smooth;
        }
        
        /* Navigation */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 5%;
            transition: var(--transition);
        }
        
        .navbar.scrolled {
            padding: 10px 5%;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--primary-color);
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin: 0 15px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--dark-color);
            font-weight: 500;
            transition: var(--transition);
            position: relative;
        }
        
        .nav-links a:after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background-color: var(--primary-color);
            transition: var(--transition);
        }
        
        .nav-links a:hover:after {
            width: 100%;
        }
        
        .nav-links a:hover {
            color: var(--primary-color);
        }
        
        .menu-toggle {
            display: none;
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        /* Header */
        header {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 150px 20px 80px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .header-content {
            max-width: 1000px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }
        
        header h1 {
            margin: 0;
            font-size: 3.2em;
            animation: fadeInDown 1s ease;
        }
        
        header p {
            font-size: 1.3em;
            margin: 20px 0 30px;
            animation: fadeInUp 1s ease;
        }
        
        .header-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
            animation: fadeIn 1.5s ease;
        }
        
        /* Sections générales */
        section {
            padding: 80px 20px;
            max-width: 1200px;
            margin: auto;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 50px;
        }
        
        .section-title h2 {
            color: var(--primary-color);
            font-size: 2.5rem;
            margin-bottom: 15px;
            position: relative;
            display: inline-block;
        }
        
        .section-title h2:after {
            content: '';
            position: absolute;
            width: 70px;
            height: 3px;
            background: var(--secondary-color);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .section-title p {
            color: #777;
            max-width: 700px;
            margin: 0 auto;
        }
        
        /* Services */
        .services {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            justify-content: center;
        }
        
        .card {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            flex: 1 1 300px;
            text-align: center;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        
        .card:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            transform: scaleX(0);
            transform-origin: left;
            transition: var(--transition);
        }
        
        .card:hover:before {
            transform: scaleX(1);
        }
        
        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }
        
        .card i {
            font-size: 3rem;
            color: var(--primary-color);
            margin-bottom: 20px;
        }
        
        .card h3 {
            margin: 15px 0;
            color: var(--dark-color);
        }
        
        /* Gallery */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }
        
        .gallery-item {
            position: relative;
            border-radius: 8px;
            overflow: hidden;
            height: 250px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            cursor: pointer;
        }
        
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }
        
        .gallery-item:hover img {
            transform: scale(1.1);
        }
        
        .gallery-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent);
            padding: 20px;
            color: white;
            transform: translateY(100%);
            transition: var(--transition);
        }
        
        .gallery-item:hover .gallery-overlay {
            transform: translateY(0);
        }
        
        /* Testimonials */
        .testimonials {
            background: linear-gradient(to right, #f8f9fa, #e9ecef);
            padding: 80px 20px;
        }
        
        .testimonial-container {
            max-width: 1000px;
            margin: 0 auto;
            position: relative;
        }
        
        .testimonial-slide {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            text-align: center;
            margin: 20px;
        }
        
        .testimonial-slide i {
            font-size: 2rem;
            color: var(--primary-color);
            margin-bottom: 20px;
        }
        
        .testimonial-content {
            font-style: italic;
            margin-bottom: 20px;
        }
        
        .testimonial-author {
            font-weight: bold;
            color: var(--dark-color);
        }
        
        .testimonial-role {
            color: #777;
            font-size: 0.9rem;
        }
        
        /* FAQ */
        .faq-container {
            margin-top: 40px;
        }
        
        .faq-item {
            margin-bottom: 20px;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        .faq-question {
            padding: 20px;
            background: white;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 600;
        }
        
        .faq-answer {
            padding: 0 20px;
            max-height: 0;
            overflow: hidden;
            background: #f8f9fa;
            transition: max-height 0.3s ease, padding 0.3s ease;
        }
        
        .faq-item.active .faq-answer {
            max-height: 200px;
            padding: 20px;
        }
        
        /* Contact */
        .contact-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
            margin-top: 40px;
        }
        
        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .contact-item i {
            font-size: 1.5rem;
            color: var(--primary-color);
            width: 40px;
            height: 40px;
            background: rgba(79, 172, 254, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .contact-form {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-family: inherit;
            font-size: 1rem;
            transition: var(--transition);
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 3px rgba(79, 172, 254, 0.2);
        }
        
        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }
        
        /* Footer */
        footer {
            background: var(--dark-color);
            color: white;
            padding: 60px 20px 30px;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
        }
        
        .footer-column h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }
        
        .footer-column h3:after {
            content: '';
            position: absolute;
            width: 40px;
            height: 2px;
            background: var(--primary-color);
            bottom: 0;
            left: 0;
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 10px;
        }
        
        .footer-links a {
            color: #ccc;
            text-decoration: none;
            transition: var(--transition);
        }
        
        .footer-links a:hover {
            color: var(--primary-color);
            padding-left: 5px;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: white;
            transition: var(--transition);
        }
        
        .social-links a:hover {
            background: var(--primary-color);
            transform: translateY(-5px);
        }
        
        .copyright {
            text-align: center;
            margin-top: 50px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #999;
            font-size: 0.9rem;
        }
        
        /* Back to top */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: var(--primary-color);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
            z-index: 999;
        }
        
        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }
        
        .back-to-top:hover {
            background: var(--secondary-color);
            transform: translateY(-5px);
        }
        
        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            header h1 {
                font-size: 2.5rem;
            }
            
            .nav-links {
                position: fixed;
                top: 70px;
                left: 0;
                width: 100%;
                background: white;
                flex-direction: column;
                align-items: center;
                padding: 20px 0;
                box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
                clip-path: polygon(0 0, 100% 0, 100% 0, 0 0);
                transition: var(--transition);
            }
            
            .nav-links.active {
                clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
            }
            
            .nav-links li {
                margin: 15px 0;
            }
            
            .menu-toggle {
                display: block;
            }
            
            .header-buttons {
                flex-direction: column;
                align-items: center;
            }
        }
        
        @media (max-width: 768px) {
            header {
                padding: 120px 20px 60px;
            }
            
            header h1 {
                font-size: 2rem;
            }
            
            header p {
                font-size: 1.1rem;
            }
            
            .section-title h2 {
                font-size: 2rem;
            }
            
            section {
                padding: 60px 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="logo">
            <i class="fas fa-cogs"></i>
            <span>WAK INNOV</span>
        </div>
        <ul class="nav-links">
            <li><a href="#home">Accueil</a></li>
            <li><a href="#about">À propos</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#portfolio">Portfolio</a></li>
            <li><a href="#testimonials">Témoignages</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="menu-toggle">
            <i class="fas fa-bars"></i>
        </div>
    </nav>

    <!-- Header -->
    <header id="home">
        <div class="header-content">
            <h1>Étude Mécanique - Calcul Conception & Modélisation 3D</h1>
            <p>Solutions sur mesure pour vos projets industriels et créatifs</p>
            <div class="header-buttons">
                <a href="#portfolio" class="button">Voir nos réalisations</a>
                <a href="#contact" class="button secondary">Nous contacter</a>
            </div>
        </div>
    </header>

    <!-- À propos -->
    <section id="about">
        <div class="section-title">
            <h2>À propos de WAK INNOV</h2>
            <p>Votre partenaire pour l'innovation technique et la conception mécanique</p>
        </div>
        <div class="about-content">
            <p>Donner vie à vos projets, c'est notre mission. Nous accompagnons nos clients dans le développement de prototypes, la création de modèles réalistes et la préparation de fichiers pour impression 3D.</p>
            <p>Notre expertise en conception mécanique et en calcul de structure nous permet de vous proposer des solutions techniques innovantes et robustes, adaptées à vos besoins spécifiques.</p>
            <p>Que vous soyez un particulier avec une idée créative ou une entreprise cherchant à optimiser ses processus industriels, notre équipe d'ingénieurs et de designers est à votre service.</p>
        </div>
    </section>

    <!-- Services -->
    <section id="services">
        <div class="section-title">
            <h2>Nos services</h2>
            <p>Une gamme complète de services pour concrétiser vos idées</p>
        </div>
        <div class="services">
            <div class="card">
                <i class="fas fa-cube"></i>
                <h3>Conception 3D</h3>
                <p>Modélisation précise de pièces mécaniques et objets complexes avec les logiciels les plus avancés.</p>
            </div>
            <div class="card">
                <i class="fas fa-print"></i>
                <h3>Prototypage</h3>
                <p>Préparation et optimisation de fichiers pour impression 3D, avec conseils sur les matériaux et techniques.</p>
            </div>
            <div class="card">
                <i class="fas fa-eye"></i>
                <h3>Visualisation</h3>
                <p>Rendus réalistes pour vos projets et présentations incluant les plans et les dessins techniques avec un rapport détaillé.</p>
            </div>
            <div class="card">
                <i class="fas fa-calculator"></i>
                <h3>Calcul de structure</h3>
                <p>Analyses techniques poussées pour valider la résistance et la durabilité de vos conceptions.</p>
            </div>
            <div class="card">
                <i class="fas fa-tools"></i>
                <h3>Optimisation</h3>
                <p>Amélioration de vos designs existants pour une meilleure performance et une réduction des coûts.</p>
            </div>
            <div class="card">
                <i class="fas fa-project-diagram"></i>
                <h3>Gestion de projet</h3>
                <p>Accompagnement complet de votre projet, de l'idée initiale à la réalisation finale.</p>
            </div>
        </div>
    </section>

    <!-- Portfolio -->
    <section id="portfolio">
        <div class="section-title">
            <h2>Nos réalisations</h2>
            <p>Découvrez une sélection de nos projets récents</p>
        </div>
        <div class="gallery">
            <div class="gallery-item">
                <img src="https://placehold.co/600x400/4facfe/ffffff?text=Projet+Mécanique" alt="Projet mécanique">
                <div class="gallery-overlay">
                    <h3>Système d'engrenage</h3>
                    <p>Conception et modélisation 3D</p>
                </div>
            </div>
            <div class="gallery-item">
                <img src="https://placehold.co/600x400/00f2fe/ffffff?text=Prototype+3D" alt="Prototype 3D">
                <div class="gallery-overlay">
                    <h3>Prototype innovant</h3>
                    <p>Impression 3D et finition</p>
                </div>
            </div>
            <div class="gallery-item">
                <img src="https://placehold.co/600x400/ff6b6b/ffffff?text=Visualisation" alt="Visualisation">
                <div class="gallery-overlay">
                    <h3>Rendu architectural</h3>
                    <p>Visualisation réaliste</p>
                </div>
            </div>
            <div class="gallery-item">
                <img src="https://placehold.co/600x400/333/ffffff?text=Calcul+Structure" alt="Calcul de structure">
                <div class="gallery-overlay">
                    <h3>Analyse de contraintes</h3>
                    <p>Simulation et calcul</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Témoignages -->
    <section id="testimonials" class="testimonials">
        <div class="section-title">
            <h2>Ils nous font confiance</h2>
            <p>Retours d'expérience de nos clients satisfaits</p>
        </div>
        <div class="testimonial-container">
            <div class="testimonial-slide">
                <i class="fas fa-quote-left"></i>
                <p class="testimonial-content">WAK INNOV a transformé mon idée en un produit concret. Leur expertise en modélisation 3D et leur professionnalisme ont dépassé mes attentes. Je recommande vivement leurs services !</p>
                <p class="testimonial-author">Pierre Martin</p>
                <p class="testimonial-role">CEO, InnovTech</p>
            </div>
        </div>
    </section>

    <!-- FAQ -->
    <section id="faq">
        <div class="section-title">
            <h2>Questions fréquentes</h2>
            <p>Trouvez les réponses aux questions les plus courantes</p>
        </div>
        <div class="faq-container">
            <div class="faq-item">
                <div class="faq-question">
                    <span>Quels types de fichiers acceptez-vous pour la modélisation 3D ?</span>
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    <p>Nous acceptons la plupart des formats de fichiers courants (STEP, IGES, STL, OBJ, etc.). Si vous avez un format spécifique, n'hésitez pas à nous contacter pour confirmation.</p>
                </div>
            </div>
            <div class="faq-item">
                <div class="faq-question">
                    <span>Quel est le délai moyen pour un projet de conception ?</span>
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    <p>Le délai dépend de la complexité du projet. Un projet simple peut être réalisé en quelques jours, tandis qu'un projet complexe peut nécessiter plusieurs semaines. Nous établissons toujours un calendrier précis en début de projet.</p>
                </div>
            </div>
            <div class="faq-item">
                <div class="faq-question">
                    <span>Proposez-vous des services d'impression 3D ?</span>
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    <p>Oui, nous proposons des services d'impression 3D professionnelle avec une variété de matériaux (PLA, ABS, résine, nylon, etc.). Nous pouvons également vous conseiller sur le choix du matériau le plus adapté à votre projet.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact -->
    <section id="contact">
        <div class="section-title">
            <h2>Contactez-nous</h2>
            <p>Discutons de votre projet ensemble</p>
        </div>
        <div class="contact-container">
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <div>
                        <h3>Adresse</h3>
                        <p>123 Rue de l'Innovation, 75000 Paris</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <div>
                        <h3>Téléphone</h3>
                        <p>+33 1 23 45 67 89</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <div>
                        <h3>Email</h3>
                        <p>contact@wakinnov.com</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <div>
                        <h3>Horaires</h3>
                        <p>Lun-Ven: 9h-18h | Sam: 10h-16h</p>
                    </div>
                </div>
            </div>
            <div class="contact-form">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">Nom complet</label>
                        <input type="text" id="name" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Adresse email</label>
                        <input type="email" id="email" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="subject">Sujet</label>
                        <input type="text" id="subject" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" class="form-control" required></textarea>
                    </div>
                    <button type="submit" class="button">Envoyer le message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-column">
                <h3>WAK INNOV</h3>
                <p>Votre partenaire pour l'innovation technique et la conception mécanique. Donnons vie ensemble à vos projets les plus ambitieux.</p>
                <div class="social-links">
                    <a href="#"><i class="fab fa-facebook-f"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="#"><i class="fab fa-linkedin-in"></i></a>
                </div>
            </div>
            <div class="footer-column">
                <h3>Liens rapides</h3>
                <ul class="footer-links">
                    <li><a href="#home">Accueil</a></li>
                    <li><a href="#about">À propos</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#portfolio">Portfolio</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </div>
            <div class="footer-column">
                <h3>Services</h3>
                <ul class="footer-links">
                    <li><a href="#">Conception 3D</a></li>
                    <li><a href="#">Prototypage</a></li>
                    <li><a href="#">Visualisation</a></li>
                    <li><a href="#">Calcul de structure</a></li>
                    <li><a href="#">Optimisation</a></li>
                </ul>
            </div>
            <div class="footer-column">
                <h3>Newsletter</h3>
                <p>Inscrivez-vous à notre newsletter pour recevoir nos actualités et offres spéciales.</p>
                <form class="footer-newsletter">
                    <input type="email" placeholder="Votre email" class="form-control">
                    <button type="submit" class="button">S'inscrire</button>
                </form>
            </div>
        </div>
        <div class="copyright">
            <p>&copy; 2025 WAK INNOV - Tous droits réservés</p>
        </div>
    </footer>

    <!-- Back to top -->
    <a href="#" class="back-to-top">
        <i class="fas fa-arrow-up"></i>
    </a>

    <script>
        // Menu toggle
        const menuToggle = document.querySelector('.menu-toggle');
        const navLinks = document.querySelector('.nav-links');
        
        menuToggle.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });
        
        // Navbar scroll effect
        const navbar = document.querySelector('.navbar');
        
        window.addEventListener('scroll', () => {
            if (window.scrollY > 100) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });
        
        // FAQ accordion
        const faqItems = document.querySelectorAll('.faq-item');
        
        faqItems.forEach(item => {
            const question = item.querySelector('.faq-question');
            
            question.addEventListener('click', () => {
                item.classList.toggle('active');
            });
        });
        
        // Back to top button
        const backToTopButton = document.querySelector('.back-to-top');
        
        window.addEventListener('scroll', () => {
            if (window.scrollY > 500) {
                backToTopButton.classList.add('visible');
            } else {
                backToTopButton.classList.remove('visible');
            }
        });
        
        // Form submission
        const contactForm = document.getElementById('contactForm');
        
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Merci pour votre message ! Nous vous contacterons très rapidement.');
            contactForm.reset();
        });
        
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // Close mobile menu if open
                    if (navLinks.classList.contains('active')) {
                        navLinks.classList.remove('active');
                    }
                }
            });
        });
    </script>
</body>
</html>
