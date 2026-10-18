<!DOCTYPE html>
<html lang="de" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salon Élégance | Ihr Premium Friseur & Beauty Salon</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Playfair Display & Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: {
                            400: '#D4AF37',
                            500: '#C5A028',
                            600: '#B38F1D',
                            light: '#F4E8C1',
                        },
                        dark: {
                            900: '#121212',
                            800: '#1E1E1E',
                            700: '#2A2A2A',
                        }
                    },
                    fontFamily: {
                        serif: ['"Playfair Display"', 'serif'],
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom Styles & Before/After Slider */
        .before-after-container {
            position: relative;
            overflow: hidden;
            user-select: none;
        }
        .after-image {
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 50%;
            overflow: hidden;
        }
        .slider-handle {
            position: absolute;
            top: 0;
            bottom: 0;
            left: 50%;
            width: 4px;
            background-color: #D4AF37;
            cursor: ew-resize;
            transform: translateX(-50%);
            z-index: 20;
        }
        .slider-button {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 36px;
            height: 36px;
            background-color: #D4AF37;
            color: #121212;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 10px rgba(0,0,0,0.5);
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #121212;
        }
        ::-webkit-scrollbar-thumb {
            background: #C5A028;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #D4AF37;
        }
    </style>
</head>
<body class="bg-dark-900 text-gray-200 font-sans antialiased selection:bg-gold-500 selection:text-dark-900">

    <!-- HEADER / NAVIGATION -->
    <header class="fixed top-0 left-0 right-0 z-40 bg-dark-900/90 backdrop-blur-md border-b border-gold-500/20 transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <!-- Logo -->
                <a href="#" class="flex items-center gap-3 group">
                    <div class="w-10 h-10 rounded-full border border-gold-400 flex items-center justify-center text-gold-400 font-serif text-xl font-bold group-hover:bg-gold-400 group-hover:text-dark-900 transition-all">
                        É
                    </div>
                    <span class="font-serif text-2xl tracking-wider text-white">SALON <span class="text-gold-400 italic">ÉLÉGANCE</span></span>
                </a>

                <!-- Desktop Navigation Links -->
                <nav class="hidden md:flex space-x-8 text-sm font-medium">
                    <a href="#home" class="hover:text-gold-400 transition-colors">Startseite</a>
                    <a href="#services" class="hover:text-gold-400 transition-colors">Leistungen & Preise</a>
                    <a href="#about" class="hover:text-gold-400 transition-colors">Über Uns</a>
                    <a href="#gallery" class="hover:text-gold-400 transition-colors">Galerie</a>
                    <a href="#team" class="hover:text-gold-400 transition-colors">Team</a>
                    <a href="#contact" class="hover:text-gold-400 transition-colors">Kontakt</a>
                </nav>

                <!-- Action Button -->
                <div class="hidden md:block">
                    <button onclick="openBookingModal()" class="bg-gradient-to-r from-gold-500 to-gold-400 hover:from-gold-400 hover:to-gold-500 text-dark-900 font-semibold px-5 py-2.5 rounded-full shadow-lg hover:shadow-gold-500/20 transition-all duration-300 transform hover:-translate-y-0.5">
                        <i class="fa-regular font-bold fa-calendar-check mr-2"></i>Termin buchen
                    </button>
                </div>

                <!-- Mobile Menu Button -->
                <div class="md:hidden">
                    <button id="mobile-menu-btn" class="text-gray-300 hover:text-white focus:outline-none p-2">
                        <i class="fa-solid fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu Overlay -->
        <div id="mobile-menu" class="hidden md:hidden bg-dark-800 border-b border-gold-500/20 px-4 pt-2 pb-6 space-y-3">
            <a href="#home" class="mobile-link block px-3 py-2 rounded-md text-base font-medium hover:bg-dark-700 hover:text-gold-400">Startseite</a>
            <a href="#services" class="mobile-link block px-3 py-2 rounded-md text-base font-medium hover:bg-dark-700 hover:text-gold-400">Leistungen & Preise</a>
            <a href="#about" class="mobile-link block px-3 py-2 rounded-md text-base font-medium hover:bg-dark-700 hover:text-gold-400">Über Uns</a>
            <a href="#gallery" class="mobile-link block px-3 py-2 rounded-md text-base font-medium hover:bg-dark-700 hover:text-gold-400">Galerie</a>
            <a href="#team" class="mobile-link block px-3 py-2 rounded-md text-base font-medium hover:bg-dark-700 hover:text-gold-400">Team</a>
            <a href="#contact" class="mobile-link block px-3 py-2 rounded-md text-base font-medium hover:bg-dark-700 hover:text-gold-400">Kontakt</a>
            <button onclick="openBookingModal()" class="w-full mt-2 bg-gold-400 text-dark-900 font-semibold py-3 rounded-xl hover:bg-gold-500 transition">
                Termin buchen
            </button>
        </div>
    </header>

    <!-- HERO SECTION -->
    <section id="home" class="relative min-h-screen flex items-center pt-20 overflow-hidden">
        <!-- Background Image with Overlay -->
        <div class="absolute inset-0 z-0">
            <img src="https://images.unsplash.com/photo-1560066984-138dadb4c035?auto=format&fit=crop&w=1920&q=80" alt="Salon Ambiente" class="w-full h-full object-cover object-center scale-105 transform animate-pulse duration-[10000ms]">
            <div class="absolute inset-0 bg-gradient-to-r from-dark-900 via-dark-900/90 to-dark-900/40"></div>
            <div class="absolute inset-0 bg-black/40"></div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 py-24">
            <div class="max-w-2xl space-y-8">
                <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-gold-400/40 bg-gold-400/10 text-gold-400 text-xs sm:text-sm font-semibold tracking-wider uppercase">
                    <i class="fa-solid fa-crown"></i> Exklusives Haarstyling & Pflege
                </div>
                
                <h1 class="font-serif text-4xl sm:text-6xl lg:text-7xl font-bold leading-tight text-white">
                    Ihr perfekter Look <br>
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-gold-400 via-gold-light to-gold-500 italic">wartet auf Sie</span>
                </h1>
                
                <p class="text-gray-300 text-lg sm:text-xl font-light leading-relaxed">
                    Erleben Sie höchste Friseurkunst in entspannter Luxus-Atmosphäre. Wir unterstreichen Ihre individuelle Persönlichkeit mit perfekten Schnitten und stilvollen Colorationen.
                </p>

                <div class="flex flex-col sm:flex-row gap-4 pt-4">
                    <button onclick="openBookingModal()" class="bg-gradient-to-r from-gold-500 to-gold-400 hover:from-gold-400 hover:to-gold-500 text-dark-900 font-bold px-8 py-4 rounded-full shadow-lg shadow-gold-500/20 transition duration-300 flex items-center justify-center gap-3 transform hover:-translate-y-1">
                        <span>Termin online vereinbaren</span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </button>
                    <a href="#services" class="border border-white/20 hover:border-gold-400 hover:text-gold-400 text-white font-medium px-8 py-4 rounded-full transition duration-300 flex items-center justify-center gap-2 backdrop-blur-sm">
                        <span>Preise & Leistungen</span>
                    </a>
                </div>

                <!-- Live Status Banner -->
                <div class="pt-6 border-t border-white/10 flex items-center gap-4">
                    <div id="status-indicator" class="flex items-center gap-2 text-sm font-medium">
                        <span class="w-3 h-3 rounded-full bg-emerald-500 animate-ping"></span>
                        <span class="text-emerald-400">Jetzt Geöffnet</span>
                    </div>
                    <span class="text-gray-500">|</span>
                    <p class="text-sm text-gray-400">Heute: <span id="today-hours">09:00 - 19:00 Uhr</span></p>
                </div>
            </div>
        </div>
    </section>

    <!-- VORTEILE / HIGHLIGHTS -->
    <section class="py-12 bg-dark-800 border-y border-gold-500/10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="flex items-center gap-4 p-4 rounded-2xl bg-dark-900/50 border border-gold-500/10">
                    <div class="w-14 h-14 rounded-full bg-gold-400/10 text-gold-400 flex items-center justify-center text-2xl flex-shrink-0">
                        <i class="fa-solid fa-scissors"></i>
                    </div>
                    <div>
                        <h3 class="font-serif text-lg font-bold text-white">Meisterhafte Schnitte</h3>
                        <p class="text-sm text-gray-400">Präzise Techniken angepasst an Ihre Kopfform</p>
                    </div>
                </div>
                <div class="flex items-center gap-4 p-4 rounded-2xl bg-dark-900/50 border border-gold-500/10">
                    <div class="w-14 h-14 rounded-full bg-gold-400/10 text-gold-400 flex items-center justify-center text-2xl flex-shrink-0">
                        <i class="fa-solid fa-pump-soap"></i>
                    </div>
                    <div>
                        <h3 class="font-serif text-lg font-bold text-white">Premium Produkte</h3>
                        <p class="text-sm text-gray-400">Ausschließlich hochwertige & vegane Pflege</p>
                    </div>
                </div>
                <div class="flex items-center gap-4 p-4 rounded-2xl bg-dark-900/50 border border-gold-500/10">
                    <div class="w-14 h-14 rounded-full bg-gold-400/10 text-gold-400 flex items-center justify-center text-2xl flex-shrink-0">
                        <i class="fa-solid fa-mug-hot"></i>
                    </div>
                    <div>
                        <h3 class="font-serif text-lg font-bold text-white">Wellness & Drinks</h3>
                        <p class="text-sm text-gray-400">Gratis Espressobar & Kopfmassage inklusive</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- LEISTUNGEN & PREISE SECTION -->
    <section id="services" class="py-24 bg-dark-900">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm mb-2">Transparent & Fai</p>
                <h2 class="font-serif text-3xl sm:text-5xl font-bold text-white mb-4">Unsere Leistungen & Preise</h2>
                <div class="w-20 h-1 bg-gold-400 mx-auto rounded-full mb-6"></div>
                <p class="text-gray-400">Wählen Sie Ihre gewünschte Behandlung aus. Alle Preise verstehen sich inkl. Beratung, Haartyp-Analyse und Styling.</p>
            </div>

            <!-- Service Category Filter Tabs -->
            <div class="flex justify-center mb-12 overflow-x-auto pb-4">
                <div class="inline-flex p-1.5 bg-dark-800 rounded-full border border-gold-500/20">
                    <button onclick="filterServices('damen')" class="service-tab active px-6 py-2.5 rounded-full text-sm font-medium transition duration-300 bg-gold-400 text-dark-900 font-semibold">
                        Damen
                    </button>
                    <button onclick="filterServices('herren')" class="service-tab px-6 py-2.5 rounded-full text-sm font-medium text-gray-300 hover:text-white transition duration-300">
                        Herren
                    </button>
                    <button onclick="filterServices('coloration')" class="service-tab px-6 py-2.5 rounded-full text-sm font-medium text-gray-300 hover:text-white transition duration-300">
                        Coloration & Balayage
                    </button>
                    <button onclick="filterServices('kinder')" class="service-tab px-6 py-2.5 rounded-full text-sm font-medium text-gray-300 hover:text-white transition duration-300">
                        Kinder & Styling
                    </button>
                </div>
            </div>

            <!-- Services Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8" id="services-container">
                <!-- Services will be populated dynamically by JavaScript -->
            </div>
        </div>
    </section>

    <!-- VORHER-NACHHER SHOWCASE SECTION -->
    <section class="py-20 bg-dark-800 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                <div>
                    <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm mb-2">Echte Ergebnisse</p>
                    <h2 class="font-serif text-3xl sm:text-4xl font-bold text-white mb-6">Vorher & Nachher Transformation</h2>
                    <p class="text-gray-300 leading-relaxed mb-6">
                        Erleben Sie die magischen Veränderungen unserer Kunden. Mit innovativen Färbetechniken, professioneller Typberatung und hochwertiger Pflege erzielen wir atemberaubende Ergebnisse.
                    </p>
                    <ul class="space-y-4 text-gray-300 mb-8">
                        <li class="flex items-center gap-3">
                            <i class="fa-solid fa-check text-gold-400"></i> Schonende Aufhellung mit Olaplex Schutz
                        </li>
                        <li class="flex items-center gap-3">
                            <i class="fa-solid fa-check text-gold-400"></i> Nahtlose Übergänge bei Balayage & Ombré
                        </li>
                        <li class="flex items-center gap-3">
                            <i class="fa-solid fa-check text-gold-400"></i> Individueller Schnitt für mehr Volumen
                        </li>
                    </ul>
                    <button onclick="openBookingModal()" class="bg-gold-400 hover:bg-gold-500 text-dark-900 font-bold px-6 py-3 rounded-full transition">
                        Ihre Transformation buchen
                    </button>
                </div>

                <!-- Interactive Before-After Slider -->
                <div class="relative rounded-2xl overflow-hidden shadow-2xl border border-gold-500/20 aspect-[4/3] before-after-container" id="before-after-slider">
                    <!-- Before Image (Base) -->
                    <img src="https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?auto=format&fit=crop&w=1000&q=80" alt="Vorher" class="w-full h-full object-cover">
                    <span class="absolute bottom-4 right-4 bg-dark-900/80 text-white text-xs px-3 py-1 rounded-full border border-white/10">Vorher</span>

                    <!-- After Image (Clipped) -->
                    <div class="after-image" id="after-image-wrapper">
                        <img src="https://images.unsplash.com/photo-1519699047748-de8e457a634e?auto=format&fit=crop&w=1000&q=80" alt="Nachher" class="absolute top-0 left-0 w-full h-full object-cover max-w-none" id="after-img-element">
                        <span class="absolute bottom-4 left-4 bg-gold-400 text-dark-900 font-bold text-xs px-3 py-1 rounded-full">Nachher</span>
                    </div>

                    <!-- Handle -->
                    <div class="slider-handle" id="slider-handle">
                        <div class="slider-button">
                            <i class="fa-solid fa-arrows-left-right text-xs"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ÜBER UNS SECTION -->
    <section id="about" class="py-24 bg-dark-900">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
                <div class="relative">
                    <div class="relative z-10 rounded-2xl overflow-hidden border border-gold-500/20 shadow-2xl">
                        <img src="https://images.unsplash.com/photo-1521590832167-7bcbfaa6381f?auto=format&fit=crop&w=1000&q=80" alt="Salon Interieur" class="w-full h-auto">
                    </div>
                    <div class="absolute -bottom-8 -right-8 w-2/3 rounded-2xl overflow-hidden border-2 border-gold-400 shadow-2xl hidden sm:block z-20">
                        <img src="https://images.unsplash.com/photo-1562322140-8baeececf3df?auto=format&fit=crop&w=600&q=80" alt="Stylist bei der Arbeit" class="w-full h-auto">
                    </div>
                    <div class="absolute -top-6 -left-6 w-32 h-32 bg-gold-400/10 rounded-full blur-2xl pointer-events-none"></div>
                </div>

                <div class="space-y-6">
                    <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm">Unsere Philosophie</p>
                    <h2 class="font-serif text-3xl sm:text-5xl font-bold text-white">Mehr als nur ein Haarschnitt</h2>
                    <p class="text-gray-300 leading-relaxed">
                        Seit über 12 Jahren steht Salon Élégance für erstklassiges Handwerk, Leidenschaft und unvergleichlichen Service. Bei uns geht es nicht nur um Haare – es geht um Ihr Wohlbefinden.
                    </p>
                    <p class="text-gray-400 leading-relaxed">
                        Wir nehmen uns Zeit für eine ausführliche Typberatung. Unser Team besucht regelmäßig internationale Fortbildungen in Paris, London und Mailand, um Ihnen stets die neuesten Trends und schonendsten Techniken bieten zu können.
                    </p>
                    
                    <div class="grid grid-cols-2 gap-6 pt-4 border-t border-gold-500/10">
                        <div>
                            <span class="font-serif text-4xl font-bold text-gold-400">12+</span>
                            <p class="text-sm text-gray-400 mt-1">Jahre Erfahrung</p>
                        </div>
                        <div>
                            <span class="font-serif text-4xl font-bold text-gold-400">15.000+</span>
                            <p class="text-sm text-gray-400 mt-1">Zufriedene Kunden</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- GALERIE SECTION -->
    <section id="gallery" class="py-24 bg-dark-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm mb-2">Inspiration</p>
                <h2 class="font-serif text-3xl sm:text-5xl font-bold text-white mb-4">Unsere Galerie</h2>
                <div class="w-20 h-1 bg-gold-400 mx-auto rounded-full mb-6"></div>
            </div>

            <!-- Gallery Filters -->
            <div class="flex justify-center gap-2 sm:gap-4 mb-10 flex-wrap">
                <button onclick="filterGallery('all')" class="gallery-btn active px-5 py-2 rounded-full text-sm bg-gold-400 text-dark-900 font-semibold transition">Alle</button>
                <button onclick="filterGallery('damen')" class="gallery-btn px-5 py-2 rounded-full text-sm bg-dark-700 text-gray-300 hover:text-white transition">Damen</button>
                <button onclick="filterGallery('herren')" class="gallery-btn px-5 py-2 rounded-full text-sm bg-dark-700 text-gray-300 hover:text-white transition">Herren</button>
                <button onclick="filterGallery('coloration')" class="gallery-btn px-5 py-2 rounded-full text-sm bg-dark-700 text-gray-300 hover:text-white transition">Coloration</button>
                <button onclick="filterGallery('hochzeit')" class="gallery-btn px-5 py-2 rounded-full text-sm bg-dark-700 text-gray-300 hover:text-white transition">Hochzeit</button>
            </div>

            <!-- Gallery Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6" id="gallery-grid">
                <!-- Item 1 -->
                <div class="gallery-item damen coloration group relative rounded-2xl overflow-hidden aspect-square border border-gold-500/10 cursor-pointer" onclick="openLightbox('https://images.unsplash.com/photo-1560869713-7d0a29430803?auto=format&fit=crop&w=1000&q=80')">
                    <img src="https://images.unsplash.com/photo-1560869713-7d0a29430803?auto=format&fit=crop&w=600&q=80" alt="Balayage Styling" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-6">
                        <div>
                            <span class="text-gold-400 text-xs font-semibold uppercase">Balayage & Waves</span>
                            <h4 class="text-white font-serif text-lg font-bold">Blond Refinement</h4>
                        </div>
                    </div>
                </div>

                <!-- Item 2 -->
                <div class="gallery-item herren group relative rounded-2xl overflow-hidden aspect-square border border-gold-500/10 cursor-pointer" onclick="openLightbox('https://images.unsplash.com/photo-1503951914875-452162b0f3f1?auto=format&fit=crop&w=1000&q=80')">
                    <img src="https://images.unsplash.com/photo-1503951914875-452162b0f3f1?auto=format&fit=crop&w=600&q=80" alt="Herren Schnitt & Bart" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-6">
                        <div>
                            <span class="text-gold-400 text-xs font-semibold uppercase">Herren Cut</span>
                            <h4 class="text-white font-serif text-lg font-bold">Fade & Beard Styling</h4>
                        </div>
                    </div>
                </div>

                <!-- Item 3 -->
                <div class="gallery-item hochzeit damen group relative rounded-2xl overflow-hidden aspect-square border border-gold-500/10 cursor-pointer" onclick="openLightbox('https://images.unsplash.com/photo-1519699047748-de8e457a634e?auto=format&fit=crop&w=1000&q=80')">
                    <img src="https://images.unsplash.com/photo-1519699047748-de8e457a634e?auto=format&fit=crop&w=600&q=80" alt="Brautfrisur" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-6">
                        <div>
                            <span class="text-gold-400 text-xs font-semibold uppercase">Brautstyling</span>
                            <h4 class="text-white font-serif text-lg font-bold">Elegante Steckfrisur</h4>
                        </div>
                    </div>
                </div>

                <!-- Item 4 -->
                <div class="gallery-item coloration damen group relative rounded-2xl overflow-hidden aspect-square border border-gold-500/10 cursor-pointer" onclick="openLightbox('https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?auto=format&fit=crop&w=1000&q=80')">
                    <img src="https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?auto=format&fit=crop&w=600&q=80" alt="Coloration" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-6">
                        <div>
                            <span class="text-gold-400 text-xs font-semibold uppercase">Farbe & Glanz</span>
                            <h4 class="text-white font-serif text-lg font-bold">Kupfer-Rot Nuancen</h4>
                        </div>
                    </div>
                </div>

                <!-- Item 5 -->
                <div class="gallery-item herren group relative rounded-2xl overflow-hidden aspect-square border border-gold-500/10 cursor-pointer" onclick="openLightbox('https://images.unsplash.com/photo-1622286342621-4bd786c2447c?auto=format&fit=crop&w=1000&q=80')">
                    <img src="https://images.unsplash.com/photo-1622286342621-4bd786c2447c?auto=format&fit=crop&w=600&q=80" alt="Gentleman Look" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-6">
                        <div>
                            <span class="text-gold-400 text-xs font-semibold uppercase">Gentleman Cut</span>
                            <h4 class="text-white font-serif text-lg font-bold">Classic Business Style</h4>
                        </div>
                    </div>
                </div>

                <!-- Item 6 -->
                <div class="gallery-item damen group relative rounded-2xl overflow-hidden aspect-square border border-gold-500/10 cursor-pointer" onclick="openLightbox('https://images.unsplash.com/photo-1492106087820-71f1a00d2b11?auto=format&fit=crop&w=1000&q=80')">
                    <img src="https://images.unsplash.com/photo-1492106087820-71f1a00d2b11?auto=format&fit=crop&w=600&q=80" alt="Bob Schnitt" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-6">
                        <div>
                            <span class="text-gold-400 text-xs font-semibold uppercase">Präzisionsschnitt</span>
                            <h4 class="text-white font-serif text-lg font-bold">Modern Bob Cut</h4>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- LIGHTBOX MODAL FOR GALLERY -->
    <div id="lightbox" class="fixed inset-0 z-50 bg-black/90 backdrop-blur-md hidden flex items-center justify-center p-4">
        <button onclick="closeLightbox()" class="absolute top-6 right-6 text-white hover:text-gold-400 text-3xl">
            <i class="fa-solid fa-xmark"></i>
        </button>
        <img id="lightbox-img" src="" alt="Enlarged gallery image" class="max-w-full max-h-[85vh] rounded-lg border border-gold-500/20 shadow-2xl">
    </div>

    <!-- UNSER TEAM SECTION -->
    <section id="team" class="py-24 bg-dark-900">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm mb-2">Kreativ & Erfahren</p>
                <h2 class="font-serif text-3xl sm:text-5xl font-bold text-white mb-4">Unser Stylisten Team</h2>
                <div class="w-20 h-1 bg-gold-400 mx-auto rounded-full mb-6"></div>
                <p class="text-gray-400">Jedes Teammitglied bringt einzigartige Spezialisierungen mit, um Ihre Wünsche perfekt umzusetzen.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Stylist 1 -->
                <div class="bg-dark-800 rounded-2xl overflow-hidden border border-gold-500/10 group hover:border-gold-400/40 transition duration-300">
                    <div class="relative overflow-hidden aspect-[4/5]">
                        <img src="https://images.unsplash.com/photo-1580618672591-eb180b1a973f?auto=format&fit=crop&w=800&q=80" alt="Isabella Moreau" class="w-full h-full object-cover group-hover:scale-105 transition duration-500">
                        <div class="absolute inset-0 bg-gradient-to-t from-dark-900 via-transparent to-transparent opacity-80"></div>
                        <div class="absolute bottom-4 left-4 right-4">
                            <span class="bg-gold-400/90 text-dark-900 text-xs font-bold px-3 py-1 rounded-full uppercase">Creative Director</span>
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 class="font-serif text-2xl font-bold text-white">Isabella Moreau</h3>
                        <p class="text-gold-400 text-sm mb-4">Spezialistin für Balayage & Braut-Styling</p>
                        <p class="text-gray-400 text-sm mb-6">10+ Jahre Erfahrung in internationalen Salons in Paris & Berlin.</p>
                        <button onclick="openBookingModal('Isabella Moreau')" class="w-full border border-gold-400 text-gold-400 hover:bg-gold-400 hover:text-dark-900 font-semibold py-2.5 rounded-xl transition duration-300">
                            Bei Isabella buchen
                        </button>
                    </div>
                </div>

                <!-- Stylist 2 -->
                <div class="bg-dark-800 rounded-2xl overflow-hidden border border-gold-500/10 group hover:border-gold-400/40 transition duration-300">
                    <div class="relative overflow-hidden aspect-[4/5]">
                        <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=800&q=80" alt="Alexander Vance" class="w-full h-full object-cover group-hover:scale-105 transition duration-500">
                        <div class="absolute inset-0 bg-gradient-to-t from-dark-900 via-transparent to-transparent opacity-80"></div>
                        <div class="absolute bottom-4 left-4 right-4">
                            <span class="bg-gold-400/90 text-dark-900 text-xs font-bold px-3 py-1 rounded-full uppercase">Master Barber</span>
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 class="font-serif text-2xl font-bold text-white">Alexander Vance</h3>
                        <p class="text-gold-400 text-sm mb-4">Herrenschnitte, Fades & Bartpflege</p>
                        <p class="text-gray-400 text-sm mb-6">Präzisions-Cuts & traditionelle Rasiermesser-Techniken.</p>
                        <button onclick="openBookingModal('Alexander Vance')" class="w-full border border-gold-400 text-gold-400 hover:bg-gold-400 hover:text-dark-900 font-semibold py-2.5 rounded-xl transition duration-300">
                            Bei Alexander buchen
                        </button>
                    </div>
                </div>

                <!-- Stylist 3 -->
                <div class="bg-dark-800 rounded-2xl overflow-hidden border border-gold-500/10 group hover:border-gold-400/40 transition duration-300">
                    <div class="relative overflow-hidden aspect-[4/5]">
                        <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?auto=format&fit=crop&w=800&q=80" alt="Sophie Lindner" class="w-full h-full object-cover group-hover:scale-105 transition duration-500">
                        <div class="absolute inset-0 bg-gradient-to-t from-dark-900 via-transparent to-transparent opacity-80"></div>
                        <div class="absolute bottom-4 left-4 right-4">
                            <span class="bg-gold-400/90 text-dark-900 text-xs font-bold px-3 py-1 rounded-full uppercase">Senior Colorist</span>
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 class="font-serif text-2xl font-bold text-white">Sophie Lindner</h3>
                        <p class="text-gold-400 text-sm mb-4">Farbkorrekturen & Glossing</p>
                        <p class="text-gray-400 text-sm mb-6">Perfekte Blondnuancen und nachhaltige Haarstruktur-Pflege.</p>
                        <button onclick="openBookingModal('Sophie Lindner')" class="w-full border border-gold-400 text-gold-400 hover:bg-gold-400 hover:text-dark-900 font-semibold py-2.5 rounded-xl transition duration-300">
                            Bei Sophie buchen
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- KUNDENBEWERTUNGEN SECTION -->
    <section class="py-24 bg-dark-800 border-y border-gold-500/10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm mb-2">Feedback</p>
                <h2 class="font-serif text-3xl sm:text-5xl font-bold text-white mb-4">Was unsere Kunden sagen</h2>
                <div class="w-20 h-1 bg-gold-400 mx-auto rounded-full"></div>
            </div>

            <!-- Testimonials Grid -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Review 1 -->
                <div class="bg-dark-900 p-8 rounded-2xl border border-gold-500/10 relative">
                    <div class="text-gold-400 mb-4 flex gap-1">
                        <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                    </div>
                    <p class="text-gray-300 text-sm leading-relaxed mb-6 italic">
                        "Einfach der beste Friseursalon der Stadt! Isabella hat meine Balayage perfekt hinbekommen. Die Atmosphäre ist super luxuriös und entspannt."
                    </p>
                    <div class="flex items-center gap-4">
                        <div class="w-12 h-12 rounded-full bg-gold-400/20 flex items-center justify-center font-bold text-gold-400 font-serif">
                            SK
                        </div>
                        <div>
                            <h4 class="text-white font-semibold text-sm">Stefanie Kramer</h4>
                            <p class="text-xs text-gray-500">Stammkundin seit 2 Jahren</p>
                        </div>
                    </div>
                </div>

                <!-- Review 2 -->
                <div class="bg-dark-900 p-8 rounded-2xl border border-gold-500/10 relative">
                    <div class="text-gold-400 mb-4 flex gap-1">
                        <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                    </div>
                    <p class="text-gray-300 text-sm leading-relaxed mb-6 italic">
                        "Perfekter Fade, erstklassiger Espresso und hervorragender Service. Alexander versteht sein Handwerk als Barber zu 100%!"
                    </p>
                    <div class="flex items-center gap-4">
                        <div class="w-12 h-12 rounded-full bg-gold-400/20 flex items-center justify-center font-bold text-gold-400 font-serif">
                            MW
                        </div>
                        <div>
                            <h4 class="text-white font-semibold text-sm">Maximilian Weber</h4>
                            <p class="text-xs text-gray-500">Verifizierter Kunde</p>
                        </div>
                    </div>
                </div>

                <!-- Review 3 -->
                <div class="bg-dark-900 p-8 rounded-2xl border border-gold-500/10 relative">
                    <div class="text-gold-400 mb-4 flex gap-1">
                        <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                    </div>
                    <p class="text-gray-300 text-sm leading-relaxed mb-6 italic">
                        "Ich war für mein Hochzeits-Styling hier. Das gesamte Team hat mich verwöhnt und meine Haare hielten den ganzen Tag perfekt. Tausend Dank!"
                    </p>
                    <div class="flex items-center gap-4">
                        <div class="w-12 h-12 rounded-full bg-gold-400/20 flex items-center justify-center font-bold text-gold-400 font-serif">
                            LM
                        </div>
                        <div>
                            <h4 class="text-white font-semibold text-sm">Laura Meyer</h4>
                            <p class="text-xs text-gray-500">Verifizierte Kundin</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ÖFFNUNGSZEITEN & KONTAKT SECTION -->
    <section id="contact" class="py-24 bg-dark-900">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
                
                <!-- Contact Info & Opening Hours -->
                <div>
                    <p class="text-gold-400 font-semibold tracking-wider uppercase text-sm mb-2">Besuchen Sie uns</p>
                    <h2 class="font-serif text-3xl sm:text-5xl font-bold text-white mb-6">Kontakt & Zeiten</h2>
                    <p class="text-gray-400 mb-8">
                        Wir freuen uns darauf, Sie persönlich in unserem Salon begrüßen zu dürfen. Parkplätze finden Sie direkt vor der Tür.
                    </p>

                    <!-- Info Cards -->
                    <div class="space-y-6 mb-10">
                        <div class="flex items-start gap-4">
                            <div class="w-10 h-10 rounded-full bg-gold-400/10 text-gold-400 flex items-center justify-center text-lg flex-shrink-0 mt-1">
                                <i class="fa-solid fa-location-dot"></i>
                            </div>
                            <div>
                                <h4 class="text-white font-semibold">Adresse</h4>
                                <p class="text-gray-400 text-sm">Goethestraße 45, 80336 München</p>
                            </div>
                        </div>

                        <div class="flex items-start gap-4">
                            <div class="w-10 h-10 rounded-full bg-gold-400/10 text-gold-400 flex items-center justify-center text-lg flex-shrink-0 mt-1">
                                <i class="fa-solid fa-phone"></i>
                            </div>
                            <div>
                                <h4 class="text-white font-semibold">Telefon</h4>
                                <p class="text-gray-400 text-sm">+49 (0) 89 123 456 78</p>
                            </div>
                        </div>

                        <div class="flex items-start gap-4">
                            <div class="w-10 h-10 rounded-full bg-gold-400/10 text-gold-400 flex items-center justify-center text-lg flex-shrink-0 mt-1">
                                <i class="fa-solid fa-envelope"></i>
                            </div>
                            <div>
                                <h4 class="text-white font-semibold">E-Mail</h4>
                                <p class="text-gray-400 text-sm">info@salon-elegance.de</p>
                            </div>
                        </div>
                    </div>

                    <!-- Öffnungszeiten Table -->
                    <div class="bg-dark-800 p-6 rounded-2xl border border-gold-500/10">
                        <h3 class="font-serif text-xl font-bold text-white mb-4 flex items-center gap-2">
                            <i class="fa-regular fa-clock text-gold-400"></i> Öffnungszeiten
                        </h3>
                        <div class="space-y-2 text-sm">
                            <div class="flex justify-between py-1 border-b border-gray-700/50">
                                <span class="text-gray-300">Montag</span>
                                <span class="text-gray-400">Geschlossen</span>
                            </div>
                            <div class="flex justify-between py-1 border-b border-gray-700/50">
                                <span class="text-gray-300">Dienstag - Freitag</span>
                                <span class="text-gold-400 font-medium">09:00 - 19:00 Uhr</span>
                            </div>
                            <div class="flex justify-between py-1 border-b border-gray-700/50">
                                <span class="text-gray-300">Samstag</span>
                                <span class="text-gold-400 font-medium">08:30 - 17:00 Uhr</span>
                            </div>
                            <div class="flex justify-between py-1">
                                <span class="text-gray-300">Sonntag & Feiertage</span>
                                <span class="text-gray-400">Geschlossen</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Contact Form -->
                <div class="bg-dark-800 p-8 sm:p-10 rounded-3xl border border-gold-500/10 relative">
                    <h3 class="font-serif text-2xl font-bold text-white mb-2">Nachricht senden</h3>
                    <p class="text-gray-400 text-sm mb-6">Haben Sie Fragen oder spezielle Wünsche? Schreiben Sie uns direkt.</p>

                    <form id="contact-form" onsubmit="handleContactSubmit(event)" class="space-y-4">
                        <div>
                            <label class="block text-xs font-semibold uppercase text-gray-400 mb-1">Name</label>
                            <input type="text" required placeholder="Ihr vollständiger Name" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-gold-400 transition">
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-semibold uppercase text-gray-400 mb-1">E-Mail</label>
                                <input type="email" required placeholder="ihre@email.de" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-gold-400 transition">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold uppercase text-gray-400 mb-1">Telefon</label>
                                <input type="tel" placeholder="0170 1234567" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-gold-400 transition">
                            </div>
                        </div>

                        <div>
                            <label class="block text-xs font-semibold uppercase text-gray-400 mb-1">Nachricht</label>
                            <textarea rows="4" required placeholder="Wie können wir Ihnen helfen?" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-gold-400 transition"></textarea>
                        </div>

                        <button type="submit" class="w-full bg-gradient-to-r from-gold-500 to-gold-400 text-dark-900 font-bold py-3.5 rounded-xl hover:from-gold-400 hover:to-gold-500 transition shadow-lg shadow-gold-500/20">
                            Nachricht absenden
                        </button>
                    </form>

                    <!-- Success Message Alert -->
                    <div id="contact-success" class="hidden absolute inset-0 bg-dark-800/95 rounded-3xl flex flex-col items-center justify-center p-8 text-center">
                        <div class="w-16 h-16 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center text-3xl mb-4">
                            <i class="fa-solid fa-check"></i>
                        </div>
                        <h4 class="font-serif text-2xl font-bold text-white mb-2">Vielen Dank!</h4>
                        <p class="text-gray-300 text-sm mb-6">Ihre Nachricht wurde erfolgreich gesendet. Wir melden uns in Kürze bei Ihnen.</p>
                        <button onclick="resetContactForm()" class="text-gold-400 underline text-sm">Weitere Nachricht senden</button>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-black border-t border-gold-500/20 py-12 text-gray-400">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row justify-between items-center gap-6 border-b border-gray-800 pb-8">
                <!-- Logo -->
                <a href="#" class="flex items-center gap-3">
                    <div class="w-8 h-8 rounded-full border border-gold-400 flex items-center justify-center text-gold-400 font-serif font-bold text-sm">
                        É
                    </div>
                    <span class="font-serif text-xl text-white">SALON <span class="text-gold-400 italic">ÉLÉGANCE</span></span>
                </a>

                <!-- Social Media -->
                <div class="flex space-x-6 text-xl">
                    <a href="#" class="hover:text-gold-400 transition"><i class="fa-brands fa-instagram"></i></a>
                    <a href="#" class="hover:text-gold-400 transition"><i class="fa-brands fa-facebook-f"></i></a>
                    <a href="#" class="hover:text-gold-400 transition"><i class="fa-brands fa-whatsapp"></i></a>
                    <a href="#" class="hover:text-gold-400 transition"><i class="fa-brands fa-tiktok"></i></a>
                </div>
            </div>

            <div class="mt-8 flex flex-col sm:flex-row justify-between items-center text-xs text-gray-500 gap-4">
                <p>&copy; <span id="current-year"></span> Salon Élégance. Alle Rechte vorbehalten.</p>
                <div class="flex space-x-6">
                    <a href="#" class="hover:text-gray-300">Impressum</a>
                    <a href="#" class="hover:text-gray-300">Datenschutz</a>
                    <a href="#" class="hover:text-gray-300">AGB</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- MULTI-STEP BOOKING MODAL -->
    <div id="booking-modal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-md hidden flex items-center justify-center p-4 overflow-y-auto">
        <div class="bg-dark-800 border border-gold-500/30 rounded-3xl w-full max-w-2xl overflow-hidden shadow-2xl relative my-8">
            
            <!-- Close Button -->
            <button onclick="closeBookingModal()" class="absolute top-5 right-5 text-gray-400 hover:text-white text-2xl z-10">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <!-- Modal Header -->
            <div class="bg-dark-900 p-6 border-b border-gold-500/10">
                <h3 class="font-serif text-2xl font-bold text-white text-center">Online Terminbuchung</h3>
                <!-- Progress Indicators -->
                <div class="flex justify-center items-center gap-2 mt-4 text-xs">
                    <span id="step-dot-1" class="w-8 h-2 rounded-full bg-gold-400"></span>
                    <span id="step-dot-2" class="w-8 h-2 rounded-full bg-gray-700"></span>
                    <span id="step-dot-3" class="w-8 h-2 rounded-full bg-gray-700"></span>
                    <span id="step-dot-4" class="w-8 h-2 rounded-full bg-gray-700"></span>
                </div>
            </div>

            <!-- Modal Body Forms -->
            <div class="p-6 sm:p-8">
                
                <!-- STEP 1: Service Selection -->
                <div id="booking-step-1" class="space-y-4">
                    <h4 class="text-white font-semibold mb-3">1. Wählen Sie eine Behandlung:</h4>
                    <div class="space-y-3 max-h-60 overflow-y-auto pr-1" id="booking-services-list">
                        <!-- Populated via JS -->
                    </div>
                    <div class="pt-4 flex justify-end">
                        <button onclick="nextStep(2)" class="bg-gold-400 text-dark-900 font-bold px-6 py-2.5 rounded-xl hover:bg-gold-500 transition">Weiter</button>
                    </div>
                </div>

                <!-- STEP 2: Stylist Selection -->
                <div id="booking-step-2" class="hidden space-y-4">
                    <h4 class="text-white font-semibold mb-3">2. Wählen Sie Ihren Wunsch-Stylisten:</h4>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3" id="stylist-options">
                        <div onclick="selectStylist('Egal / Erster freier')" class="stylist-card p-4 rounded-xl border border-gray-700 bg-dark-900 cursor-pointer hover:border-gold-400 transition flex items-center gap-3 active-stylist">
                            <div class="w-10 h-10 rounded-full bg-gold-400/20 text-gold-400 flex items-center justify-center font-bold">
                                <i class="fa-solid fa-user-check"></i>
                            </div>
                            <div>
                                <h5 class="text-white font-semibold text-sm">Egal / Schnellster Termin</h5>
                                <p class="text-xs text-gray-400">Erster verfügbarer Stylist</p>
                            </div>
                        </div>
                        <div onclick="selectStylist('Isabella Moreau')" class="stylist-card p-4 rounded-xl border border-gray-700 bg-dark-900 cursor-pointer hover:border-gold-400 transition flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full bg-gold-400/20 text-gold-400 flex items-center justify-center font-bold">IM</div>
                            <div>
                                <h5 class="text-white font-semibold text-sm">Isabella Moreau</h5>
                                <p class="text-xs text-gray-400">Creative Director</p>
                            </div>
                        </div>
                        <div onclick="selectStylist('Alexander Vance')" class="stylist-card p-4 rounded-xl border border-gray-700 bg-dark-900 cursor-pointer hover:border-gold-400 transition flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full bg-gold-400/20 text-gold-400 flex items-center justify-center font-bold">AV</div>
                            <div>
                                <h5 class="text-white font-semibold text-sm">Alexander Vance</h5>
                                <p class="text-xs text-gray-400">Master Barber</p>
                            </div>
                        </div>
                        <div onclick="selectStylist('Sophie Lindner')" class="stylist-card p-4 rounded-xl border border-gray-700 bg-dark-900 cursor-pointer hover:border-gold-400 transition flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full bg-gold-400/20 text-gold-400 flex items-center justify-center font-bold">SL</div>
                            <div>
                                <h5 class="text-white font-semibold text-sm">Sophie Lindner</h5>
                                <p class="text-xs text-gray-400">Senior Colorist</p>
                            </div>
                        </div>
                    </div>
                    <div class="pt-4 flex justify-between">
                        <button onclick="nextStep(1)" class="text-gray-400 hover:text-white px-4 py-2">Zurück</button>
                        <button onclick="nextStep(3)" class="bg-gold-400 text-dark-900 font-bold px-6 py-2.5 rounded-xl hover:bg-gold-500 transition">Weiter</button>
                    </div>
                </div>

                <!-- STEP 3: Date & Time -->
                <div id="booking-step-3" class="hidden space-y-4">
                    <h4 class="text-white font-semibold mb-3">3. Datum & Uhrzeit wählen:</h4>
                    <div class="space-y-4">
                        <div>
                            <label class="block text-xs uppercase text-gray-400 mb-1">Datum</label>
                            <input type="date" id="booking-date" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-gold-400">
                        </div>
                        <div>
                            <label class="block text-xs uppercase text-gray-400 mb-2">Verfügbare Uhrzeiten</label>
                            <div class="grid grid-cols-3 sm:grid-cols-4 gap-2" id="time-slots">
                                <button type="button" onclick="selectTime('09:30')" class="time-btn border border-gray-700 py-2 rounded-lg text-sm text-gray-300 hover:border-gold-400">09:30</button>
                                <button type="button" onclick="selectTime('11:00')" class="time-btn border border-gray-700 py-2 rounded-lg text-sm text-gray-300 hover:border-gold-400">11:00</button>
                                <button type="button" onclick="selectTime('14:00')" class="time-btn border border-gray-700 py-2 rounded-lg text-sm text-gray-300 hover:border-gold-400">14:00</button>
                                <button type="button" onclick="selectTime('16:30')" class="time-btn border border-gray-700 py-2 rounded-lg text-sm text-gray-300 hover:border-gold-400">16:30</button>
                            </div>
                        </div>
                    </div>
                    <div class="pt-4 flex justify-between">
                        <button onclick="nextStep(2)" class="text-gray-400 hover:text-white px-4 py-2">Zurück</button>
                        <button onclick="nextStep(4)" class="bg-gold-400 text-dark-900 font-bold px-6 py-2.5 rounded-xl hover:bg-gold-500 transition">Weiter</button>
                    </div>
                </div>

                <!-- STEP 4: Personal Details & Confirmation -->
                <div id="booking-step-4" class="hidden space-y-4">
                    <h4 class="text-white font-semibold mb-3">4. Kontaktdaten zur Bestätigung:</h4>
                    <div class="space-y-3">
                        <input type="text" id="cust-name" placeholder="Name, Vorname" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-2.5 text-white focus:outline-none focus:border-gold-400">
                        <input type="email" id="cust-email" placeholder="E-Mail Adresse" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-2.5 text-white focus:outline-none focus:border-gold-400">
                        <input type="tel" id="cust-phone" placeholder="Telefonnummer" class="w-full bg-dark-900 border border-gray-700 rounded-xl px-4 py-2.5 text-white focus:outline-none focus:border-gold-400">
                    </div>

                    <!-- Summary Box -->
                    <div class="bg-dark-900 p-4 rounded-xl border border-gold-500/20 text-xs text-gray-300 space-y-1 mt-4">
                        <p><strong class="text-white">Service:</strong> <span id="summary-service">-</span></p>
                        <p><strong class="text-white">Stylist:</strong> <span id="summary-stylist">-</span></p>
                        <p><strong class="text-white">Termin:</strong> <span id="summary-datetime">-</span></p>
                    </div>

                    <div class="pt-4 flex justify-between">
                        <button onclick="nextStep(3)" class="text-gray-400 hover:text-white px-4 py-2">Zurück</button>
                        <button onclick="submitBooking()" class="bg-gradient-to-r from-gold-500 to-gold-400 text-dark-900 font-bold px-8 py-3 rounded-xl hover:from-gold-400 hover:to-gold-500 transition shadow-lg shadow-gold-500/20">
                            Verbindlich buchen
                        </button>
                    </div>
                </div>

                <!-- STEP 5: Success Confirmation -->
                <div id="booking-step-5" class="hidden text-center py-8 space-y-4">
                    <div class="w-20 h-20 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center text-4xl mx-auto">
                        <i class="fa-solid fa-check"></i>
                    </div>
                    <h4 class="font-serif text-3xl font-bold text-white">Termin Reserviert!</h4>
                    <p class="text-gray-300 text-sm max-w-md mx-auto">
                        Vielen Dank! Wir haben Ihre Terminreservierung erhalten. Eine Bestätigungs-E-Mail wurde an Ihre E-Mail Adresse versendet.
                    </p>
                    <div class="pt-4">
                        <button onclick="closeBookingModal()" class="bg-gold-400 text-dark-900 font-bold px-8 py-3 rounded-xl hover:bg-gold-500 transition">
                            Schließen
                        </button>
                    </div>
                </div>

            </div>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // --- SERVICES DATA ---
        const servicesData = [
            { id: 1, name: "Waschen, Schneiden & Föhnen", category: "damen", price: "59 €", duration: "60 Min", desc: "Verwöhn-Haarwäsche mit Kopfmassage, typgerechter Präzisionsschnitt und Styling." },
            { id: 2, name: "Balayage & Glossing Komplett-Paket", category: "coloration", price: "149 €", duration: "150 Min", desc: "Sanfter Farbverlauf, Veredelung mit Glossing, Olaplex Schutzbehandlung und Föhnen." },
            { id: 3, name: "Herren Cut & Barber Treatment", category: "herren", price: "39 €", duration: "45 Min", desc: "Klassischer oder moderner Haarschnitt, Konturenrasur, Haartonic & Styling." },
            { id: 4, name: "Herren Bartpflege & Hot Towel", category: "herren", price: "25 €", duration: "30 Min", desc: "Traditionelle Nassrasur oder Barttrimmen mit warmen Kompressen." },
            { id: 5, name: "Ansatzfärbung & Glossing", category: "coloration", price: "69 €", duration: "90 Min", desc: "Perfekte Grauhaarabdeckung und brillanter Glanz für Längen und Spitzen." },
            { id: 6, name: "Kinderhaarschnitt (bis 12 Jahre)", category: "kinder", price: "22 €", duration: "30 Min", desc: "Einfühlsamer Haarschnitt für die Kleinen inklusive Styling-Gel." },
            { id: 7, name: "Braut- & Event-Hochsteckfrisur", category: "kinder", price: "89 €", duration: "90 Min", desc: "Exklusive Hochsteckfrisur oder Flechtelemente für besondere Anlässe." }
        ];

        // --- STATE VARIABLES ---
        let selectedService = servicesData[0];
        let selectedStylist = 'Egal / Erster freier';
        let selectedTime = '11:00';

        // --- DOM LOAD INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', () => {
            document.getElementById('current-year').textContent = new Date().getFullYear();
            renderServices('damen');
            setupBeforeAfterSlider();
            checkSalonStatus();
            setTomorrowDate();
        });

        // --- RENDER SERVICES ---
        function renderServices(category) {
            const container = document.getElementById('services-container');
            container.innerHTML = '';

            const filtered = servicesData.filter(s => category === 'all' || s.category === category);

            filtered.forEach(service => {
                const card = document.createElement('div');
                card.className = "bg-dark-800 p-6 rounded-2xl border border-gold-500/10 hover:border-gold-400/30 transition flex flex-col justify-between";
                card.innerHTML = `
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-serif text-xl font-bold text-white">${service.name}</h3>
                            <span class="font-serif text-xl font-bold text-gold-400">${service.price}</span>
                        </div>
                        <p class="text-xs text-gold-400/80 mb-3"><i class="fa-regular fa-clock mr-1"></i> ${service.duration}</p>
                        <p class="text-gray-400 text-sm mb-6">${service.desc}</p>
                    </div>
                    <button onclick="quickBook(${service.id})" class="w-full py-2.5 rounded-xl border border-gold-400/50 text-gold-400 hover:bg-gold-400 hover:text-dark-900 font-semibold text-sm transition duration-300">
                        Termin Buchen
                    </button>
                `;
                container.appendChild(card);
            });
        }

        // --- FILTER SERVICES TABS ---
        function filterServices(category) {
            document.querySelectorAll('.service-tab').forEach(tab => {
                tab.classList.remove('bg-gold-400', 'text-dark-900', 'font-semibold');
                tab.classList.add('text-gray-300');
            });
            event.target.classList.add('bg-gold-400', 'text-dark-900', 'font-semibold');
            event.target.classList.remove('text-gray-300');
            renderServices(category);
        }

        // --- GALLERY FILTER ---
        function filterGallery(category) {
            document.querySelectorAll('.gallery-btn').forEach(btn => {
                btn.classList.remove('bg-gold-400', 'text-dark-900', 'font-semibold');
                btn.classList.add('bg-dark-700', 'text-gray-300');
            });
            event.target.classList.add('bg-gold-400', 'text-dark-900', 'font-semibold');
            event.target.classList.remove('bg-dark-700', 'text-gray-300');

            const items = document.querySelectorAll('.gallery-item');
            items.forEach(item => {
                if (category === 'all' || item.classList.contains(category)) {
                    item.style.display = 'block';
                } else {
                    item.style.display = 'none';
                }
            });
        }

        // --- LIGHTBOX GALLERY ---
        function openLightbox(imgSrc) {
            const lightbox = document.getElementById('lightbox');
            document.getElementById('lightbox-img').src = imgSrc;
            lightbox.classList.remove('hidden');
        }
        function closeLightbox() {
            document.getElementById('lightbox').classList.add('hidden');
        }

        // --- BEFORE/AFTER SLIDER LOGIC ---
        function setupBeforeAfterSlider() {
            const container = document.getElementById('before-after-slider');
            const handle = document.getElementById('slider-handle');
            const afterWrapper = document.getElementById('after-image-wrapper');
            const afterImg = document.getElementById('after-img-element');

            if(!container) return;

            let isDragging = false;

            const updateSlider = (x) => {
                const rect = container.getBoundingClientRect();
                let position = x - rect.left;
                if (position < 0) position = 0;
                if (position > rect.width) position = rect.width;

                const percentage = (position / rect.width) * 100;
                handle.style.left = `${percentage}%`;
                afterWrapper.style.width = `${percentage}%`;
                afterImg.style.width = `${rect.width}px`;
            };

            // Set initial dynamic image width matching container
            afterImg.style.width = `${container.getBoundingClientRect().width}px`;

            window.addEventListener('resize', () => {
                afterImg.style.width = `${container.getBoundingClientRect().width}px`;
            });

            container.addEventListener('mousedown', (e) => { isDragging = true; updateSlider(e.clientX); });
            window.addEventListener('mouseup', () => { isDragging = false; });
            window.addEventListener('mousemove', (e) => { if (isDragging) updateSlider(e.clientX); });

            // Touch events for Mobile
            container.addEventListener('touchstart', (e) => { isDragging = true; updateSlider(e.touches[0].clientX); });
            window.addEventListener('touchend', () => { isDragging = false; });
            window.addEventListener('touchmove', (e) => { if (isDragging) updateSlider(e.touches[0].clientX); });
        }

        // --- LIVE SALON STATUS (OPEN/CLOSED) ---
        function checkSalonStatus() {
            const now = new Date();
            const day = now.getDay(); // 0 = Sun, 1 = Mon, ...
            const hour = now.getHours() + now.getMinutes() / 60;

            const statusIndicator = document.getElementById('status-indicator');
            let isOpen = false;

            if (day >= 2 && day <= 5) { // Tue - Fri: 09:00 - 19:00
                if (hour >= 9 && hour < 19) isOpen = true;
            } else if (day === 6) { // Sat: 08:30 - 17:00
                if (hour >= 8.5 && hour < 17) isOpen = true;
            }

            if (isOpen) {
                statusIndicator.innerHTML = `
                    <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-ping"></span>
                    <span class="text-emerald-400">Jetzt Geöffnet</span>
                `;
            } else {
                statusIndicator.innerHTML = `
                    <span class="w-2.5 h-2.5 rounded-full bg-rose-500"></span>
                    <span class="text-rose-400">Derzeit Geschlossen</span>
                `;
            }
        }

        // --- MULTI-STEP BOOKING MODAL LOGIC ---
        function openBookingModal(stylistName = null) {
            if (stylistName) {
                selectedStylist = stylistName;
            }
            populateBookingServices();
            nextStep(1);
            document.getElementById('booking-modal').classList.remove('hidden');
        }

        function closeBookingModal() {
            document.getElementById('booking-modal').classList.add('hidden');
        }

        function quickBook(serviceId) {
            const found = servicesData.find(s => s.id === serviceId);
            if (found) selectedService = found;
            openBookingModal();
        }

        function populateBookingServices() {
            const list = document.getElementById('booking-services-list');
            list.innerHTML = '';
            servicesData.forEach(s => {
                const isSelected = selectedService.id === s.id;
                const div = document.createElement('div');
                div.className = `p-3.5 rounded-xl border cursor-pointer transition flex justify-between items-center ${isSelected ? 'border-gold-400 bg-gold-400/10' : 'border-gray-700 bg-dark-900 hover:border-gray-500'}`;
                div.onclick = () => {
                    selectedService = s;
                    populateBookingServices();
                };
                div.innerHTML = `
                    <div>
                        <h5 class="text-white font-semibold text-sm">${s.name}</h5>
                        <p class="text-xs text-gray-400">${s.duration}</p>
                    </div>
                    <span class="font-bold text-gold-400 text-sm">${s.price}</span>
                `;
                list.appendChild(div);
            });
        }

        function selectStylist(name) {
            selectedStylist = name;
            document.querySelectorAll('.stylist-card').forEach(card => card.classList.remove('border-gold-400', 'bg-gold-400/10'));
            event.currentTarget.classList.add('border-gold-400', 'bg-gold-400/10');
        }

        function selectTime(time) {
            selectedTime = time;
            document.querySelectorAll('.time-btn').forEach(btn => btn.classList.remove('bg-gold-400', 'text-dark-900', 'font-bold'));
            event.target.classList.add('bg-gold-400', 'text-dark-900', 'font-bold');
        }

        function setTomorrowDate() {
            const tomorrow = new Date();
            tomorrow.setDate(tomorrow.getDate() + 1);
            const yyyy = tomorrow.getFullYear();
            const mm = String(tomorrow.getMonth() + 1).padStart(2, '0');
            const dd = String(tomorrow.getDate()).padStart(2, '0');
            document.getElementById('booking-date').value = `${yyyy}-${mm}-${dd}`;
        }

        function nextStep(step) {
            // Hide all steps
            for (let i = 1; i <= 5; i++) {
                const el = document.getElementById(`booking-step-${i}`);
                if (el) el.classList.add('hidden');
                const dot = document.getElementById(`step-dot-${i}`);
                if (dot) dot.classList.replace('bg-gold-400', 'bg-gray-700');
            }

            // Show target step
            document.getElementById(`booking-step-${step}`).classList.remove('hidden');
            const targetDot = document.getElementById(`step-dot-${step}`);
            if (targetDot) targetDot.classList.replace('bg-gray-700', 'bg-gold-400');

            // Update summary on step 4
            if (step === 4) {
                document.getElementById('summary-service').textContent = `${selectedService.name} (${selectedService.price})`;
                document.getElementById('summary-stylist').textContent = selectedStylist;
                const dateVal = document.getElementById('booking-date').value;
                document.getElementById('summary-datetime').textContent = `${dateVal} um ${selectedTime} Uhr`;
            }
        }

        function submitBooking() {
            const name = document.getElementById('cust-name').value;
            const email = document.getElementById('cust-email').value;

            if (!name || !email) {
                alert('Bitte füllen Sie mindestens Name und E-Mail aus.');
                return;
            }

            nextStep(5);
        }

        // --- CONTACT FORM HANDLER ---
        function handleContactSubmit(event) {
            event.preventDefault();
            document.getElementById('contact-success').classList.remove('hidden');
        }

        function resetContactForm() {
            document.getElementById('contact-form').reset();
            document.getElementById('contact-success').classList.add('hidden');
        }

        // --- MOBILE MENU TOGGLE ---
        const mobileBtn = document.getElementById('mobile-menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');

        mobileBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        document.querySelectorAll('.mobile-link').forEach(link => {
            link.addEventListener('click', () => {
                mobileMenu.classList.add('hidden');
            });
        });
    </script>
</body>
</html>