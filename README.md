# francopazmi-o-estudiapro
<!DOCTYPE html>
<html lang="es" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EstudiaPro IA - Tu Coach de Aprendizaje</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f5f3ff',
                            100: '#ede9fe',
                            200: '#ddd6fe',
                            300: '#c4b5fd',
                            400: '#a78bfa',
                            500: '#8b5cf6',
                            600: '#7c3aed',
                            700: '#6d28d9',
                            800: '#5b21b6',
                            900: '#4c1d95',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .dark ::-webkit-scrollbar-thumb {
            background: #475569;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
        
        /* Message animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.3s ease-out forwards;
        }
    </style>
</head>
<body class="h-full bg-slate-50 dark:bg-slate-900 text-slate-800 dark:text-slate-100 font-sans transition-colors duration-200">

    <div class="flex h-full overflow-hidden">
        
        <!-- Sidebar para navegación (Desktop) -->
        <aside class="hidden md:flex flex-col w-72 bg-white dark:bg-slate-800 border-r border-slate-200 dark:border-slate-700 h-full flex-shrink-0">
            <!-- Logo / Cabecera -->
            <div class="p-6 border-b border-slate-100 dark:border-slate-700 flex items-center justify-between">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-brand-500 to-indigo-600 flex items-center justify-center text-white shadow-md shadow-brand-500/20">
                        <i class="fa-solid fa-brain text-lg"></i>
                    </div>
                    <div>
                        <h1 class="font-extrabold text-lg leading-none tracking-tight bg-gradient-to-r from-brand-600 to-indigo-500 bg-clip-text text-transparent">EstudiaPro</h1>
                        <span class="text-xs font-semibold text-slate-400 dark:text-slate-500 uppercase tracking-widest">Tu Coach IA</span>
                    </div>
                </div>
            </div>

            <!-- Menú de opciones de estudio -->
            <div class="flex-1 overflow-y-auto px-4 py-4 space-y-5">
                
                <!-- Pega tu documento (Herramienta Principal) -->
                <div>
                    <h3 class="px-3 text-[10px] font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-2">Entrada de Datos</h3>
                    <button onclick="openTool('analizador')" id="btn-tool-analizador" class="tool-btn w-full flex items-center justify-between px-3 py-3 rounded-xl text-sm font-semibold text-slate-700 dark:text-slate-200 bg-gradient-to-r hover:from-brand-50 hover:to-indigo-50 dark:hover:from-slate-700/40 dark:hover:to-slate-700/20 transition-all border border-dashed border-slate-200 dark:border-slate-700 shadow-sm">
                        <div class="flex items-center gap-3">
                            <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-brand-100 dark:bg-brand-900/40 text-brand-600 dark:text-brand-400">
                                <i class="fa-solid fa-file-import"></i>
                            </span>
                            <span>Pegar Material / Doc</span>
                        </div>
                        <span class="text-[9px] bg-emerald-100 dark:bg-emerald-950/60 text-emerald-800 dark:text-emerald-300 px-1.5 py-0.5 rounded-full font-bold">Nuevo</span>
                    </button>
                </div>

                <!-- Métodos sugeridos -->
                <div>
                    <h3 class="px-3 text-[10px] font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-2">Métodos por Evaluación</h3>
                    <ul class="space-y-1">
                        <li>
                            <button onclick="selectCategory('exposicion')" id="btn-exposicion" class="category-btn w-full flex items-center gap-3 px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-orange-100 dark:bg-orange-950/40 text-orange-600 dark:text-orange-400">
                                    <i class="fa-solid fa-display"></i>
                                </span>
                                Exposiciones
                            </button>
                        </li>
                        <li>
                            <button onclick="selectCategory('examen_escrito')" id="btn-examen_escrito" class="category-btn w-full flex items-center gap-3 px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-blue-100 dark:bg-blue-950/40 text-blue-600 dark:text-blue-400">
                                    <i class="fa-solid fa-file-signature"></i>
                                </span>
                                Exámenes Escritos
                            </button>
                        </li>
                        <li>
                            <button onclick="selectCategory('leccion_oral')" id="btn-leccion_oral" class="category-btn w-full flex items-center gap-3 px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 dark:bg-emerald-950/40 text-emerald-600 dark:text-emerald-400">
                                    <i class="fa-solid fa-comments"></i>
                                </span>
                                Lecciones Orales
                            </button>
                        </li>
                        <li>
                            <button onclick="selectCategory('leccion_escrita')" id="btn-leccion_escrita" class="category-btn w-full flex items-center gap-3 px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-purple-100 dark:bg-purple-950/40 text-purple-600 dark:text-purple-400">
                                    <i class="fa-solid fa-pen-fancy"></i>
                                </span>
                                Lecciones Escritas
                            </button>
                        </li>
                    </ul>
                </div>

                <!-- Herramientas Interactivas -->
                <div>
                    <h3 class="px-3 text-[10px] font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-2">Herramientas & Simuladores</h3>
                    <ul class="space-y-1">
                        <li>
                            <button onclick="openTool('metodos')" id="btn-tool-metodos" class="tool-btn w-full flex items-center justify-between px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <div class="flex items-center gap-3">
                                    <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-violet-100 dark:bg-violet-950/40 text-violet-600 dark:text-violet-400">
                                        <i class="fa-solid fa-layer-group"></i>
                                    </span>
                                    Catálogo de Métodos
                                </div>
                                <span class="text-[10px] bg-violet-100 dark:bg-violet-900/50 text-violet-700 dark:text-violet-300 px-2 py-0.5 rounded-full font-bold">10+</span>
                            </button>
                        </li>
                        <li>
                            <button onclick="openTool('planificador')" id="btn-tool-planificador" class="tool-btn w-full flex items-center justify-between px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <div class="flex items-center gap-3">
                                    <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-brand-100 dark:bg-brand-900/40 text-brand-600 dark:text-brand-400">
                                        <i class="fa-solid fa-calendar-days"></i>
                                    </span>
                                    Plan de Estudio
                                </div>
                                <span class="text-[10px] bg-brand-100 dark:bg-brand-900/50 text-brand-700 dark:text-brand-300 px-2 py-0.5 rounded-full font-bold">IA</span>
                            </button>
                        </li>
                        <li>
                            <button onclick="openTool('flashcards')" id="btn-tool-flashcards" class="tool-btn w-full flex items-center justify-between px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <div class="flex items-center gap-3">
                                    <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-pink-100 dark:bg-pink-950/40 text-pink-600 dark:text-pink-400">
                                        <i class="fa-solid fa-cards-blank"></i>
                                    </span>
                                    Flashcards & Leitner
                                </div>
                                <span class="text-[10px] bg-pink-100 dark:bg-pink-900/50 text-pink-700 dark:text-pink-300 px-2 py-0.5 rounded-full font-bold">Voz</span>
                            </button>
                        </li>
                        <li>
                            <button onclick="openTool('simulador')" id="btn-tool-simulador" class="tool-btn w-full flex items-center justify-between px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <div class="flex items-center gap-3">
                                    <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-amber-100 dark:bg-amber-950/40 text-amber-600 dark:text-amber-400">
                                        <i class="fa-solid fa-graduation-cap"></i>
                                    </span>
                                    Simulador Examen
                                </div>
                                <span class="text-[10px] bg-amber-100 dark:bg-amber-900/50 text-amber-700 dark:text-amber-300 px-2 py-0.5 rounded-full font-bold">Prof</span>
                            </button>
                        </li>
                        <li>
                            <button onclick="openTool('dictado')" id="btn-tool-dictado" class="tool-btn w-full flex items-center justify-between px-3 py-2 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-300 hover:bg-slate-50 dark:hover:bg-slate-700/50 transition-all">
                                <div class="flex items-center gap-3">
                                    <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-indigo-100 dark:bg-indigo-950/40 text-indigo-600 dark:text-indigo-400">
                                        <i class="fa-solid fa-volume-high"></i>
                                    </span>
                                    Simulador Dictado
                                </div>
                                <span class="text-[10px] bg-indigo-100 dark:bg-indigo-900/50 text-indigo-700 dark:text-indigo-300 px-2 py-0.5 rounded-full font-bold">Voz</span>
                            </button>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Footer con Configuración y Tema -->
            <div class="p-4 border-t border-slate-100 dark:border-slate-700 space-y-2">
                <div class="flex items-center justify-between px-2">
                    <button onclick="toggleDarkMode()" class="text-slate-500 hover:text-slate-700 dark:text-slate-400 dark:hover:text-slate-200 p-2 rounded-lg hover:bg-slate-100 dark:hover:bg-slate-700 transition-all" title="Alternar Modo Oscuro">
                        <i class="fa-solid fa-moon dark:hidden"></i>
                        <i class="fa-solid fa-sun hidden dark:block"></i>
                    </button>
                    <button onclick="openSettingsModal()" class="text-slate-500 hover:text-slate-700 dark:text-slate-400 dark:hover:text-slate-200 p-2 rounded-lg hover:bg-slate-100 dark:hover:bg-slate-700 transition-all flex items-center gap-1.5 text-xs font-semibold" title="Configurar API Key">
                        <i class="fa-solid fa-key"></i>
                        <span>API Key</span>
                    </button>
                </div>
            </div>
        </aside>

        <!-- Main Workspace -->
        <main class="flex-1 flex flex-col h-full bg-slate-50 dark:bg-slate-900 overflow-hidden relative">
            
            <!-- Navbar de Móvil y Encabezado de Escritorio -->
            <header class="bg-white dark:bg-slate-800 border-b border-slate-200 dark:border-slate-700 h-16 flex items-center justify-between px-4 md:px-6 z-10 flex-shrink-0">
                <div class="flex items-center gap-3">
                    <button onclick="toggleMobileMenu()" class="md:hidden text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-700 p-2 rounded-lg transition-all">
                        <i class="fa-solid fa-bars text-lg"></i>
                    </button>
                    <div class="flex items-center gap-2">
                        <span id="header-icon" class="w-2.5 h-2.5 rounded-full bg-brand-500"></span>
                        <h2 id="header-title" class="font-semibold text-slate-800 dark:text-slate-100">Conversación Abierta</h2>
                    </div>
                </div>

                <div class="flex items-center gap-2">
                    <button onclick="resetAllWorkspaces()" class="flex items-center gap-1.5 px-3 py-1.5 text-xs font-semibold text-red-600 dark:text-red-400 hover:bg-red-50 dark:hover:bg-red-950/20 rounded-lg transition-all">
                        <i class="fa-solid fa-trash-can"></i>
                        <span class="hidden sm:inline">Limpiar Todo</span>
                    </button>
                </div>
            </header>

            <!-- Menú Móvil Desplegable -->
            <div id="mobile-menu" class="absolute inset-0 bg-slate-900/50 backdrop-blur-sm z-40 hidden md:hidden transition-all duration-300">
                <div class="w-64 bg-white dark:bg-slate-800 h-full p-5 flex flex-col shadow-2xl">
                    <div class="flex items-center justify-between mb-6">
                        <span class="font-bold text-slate-800 dark:text-white">EstudiaPro IA</span>
                        <button onclick="toggleMobileMenu()" class="text-slate-500 hover:text-slate-800 dark:hover:text-white">
                            <i class="fa-solid fa-xmark text-lg"></i>
                        </button>
                    </div>
                    <div class="flex-1 space-y-6 overflow-y-auto">
                        <div>
                            <button onclick="openTool('analizador')" class="w-full text-left flex items-center gap-2 py-2 text-sm font-bold text-brand-600 dark:text-brand-400"><i class="fa-solid fa-file-import"></i> Pegar Documento / Material</button>
                        </div>
                        <div>
                            <h3 class="text-[10px] font-bold text-slate-400 dark:text-slate-500 uppercase tracking-widest mb-2">Métodos</h3>
                            <ul class="space-y-1">
                                <li><button onclick="selectCategory('exposicion')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-display text-orange-500"></i> Exposiciones</button></li>
                                <li><button onclick="selectCategory('examen_escrito')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-file-signature text-blue-500"></i> Exámenes Escritos</button></li>
                                <li><button onclick="selectCategory('leccion_oral')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-comments text-emerald-500"></i> Lecciones Orales</button></li>
                                <li><button onclick="selectCategory('leccion_escrita')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-pen-fancy text-purple-500"></i> Lecciones Escritas</button></li>
                            </ul>
                        </div>
                        <div>
                            <h3 class="text-[10px] font-bold text-slate-400 dark:text-slate-500 uppercase tracking-widest mb-2">Herramientas</h3>
                            <ul class="space-y-1">
                                <li><button onclick="openTool('metodos')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-layer-group text-violet-500"></i> Catálogo Métodos</button></li>
                                <li><button onclick="openTool('planificador')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-calendar-days text-brand-500"></i> Plan de Estudio</button></li>
                                <li><button onclick="openTool('flashcards')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-cards-blank text-pink-500"></i> Flashcards & Leitner</button></li>
                                <li><button onclick="openTool('simulador')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-graduation-cap text-amber-500"></i> Simulador Examen</button></li>
                                <li><button onclick="openTool('dictado')" class="w-full text-left flex items-center gap-2 py-1.5 text-sm text-slate-600 dark:text-slate-300"><i class="fa-solid fa-volume-high text-indigo-500"></i> Simulador Dictado</button></li>
                            </ul>
                        </div>
                    </div>
                    <div class="mt-auto border-t border-slate-100 dark:border-slate-700 pt-4 flex items-center justify-between">
                        <button onclick="toggleDarkMode()" class="text-slate-500 dark:text-slate-400 p-2 hover:bg-slate-100 dark:hover:bg-slate-700 rounded-lg">
                            <i class="fa-solid fa-moon dark:hidden"></i>
                            <i class="fa-solid fa-sun hidden dark:block"></i>
                        </button>
                        <button onclick="openSettingsModal()" class="text-xs font-semibold text-slate-500 dark:text-slate-400 flex items-center gap-1.5 hover:bg-slate-100 dark:hover:bg-slate-700 p-2 rounded-lg">
                            <i class="fa-solid fa-key"></i> Clave API
                        </button>
                    </div>
                </div>
            </div>

            <!-- CHAT VIEW -->
            <div id="chat-workspace" class="flex-1 flex flex-col overflow-hidden">
                <div id="chat-messages" class="flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                    <!-- Tarjeta de Bienvenida -->
                    <div id="welcome-card" class="max-w-2xl mx-auto text-center space-y-6 py-8">
                        <div class="inline-flex items-center justify-center w-16 h-16 rounded-2xl bg-gradient-to-tr from-brand-500 to-indigo-600 text-white shadow-lg shadow-brand-500/20 mb-2">
                            <i class="fa-solid fa-graduation-cap text-3xl animate-bounce"></i>
                        </div>
                        <div class="space-y-2">
                            <h2 class="text-2xl md:text-3xl font-extrabold tracking-tight text-slate-850 dark:text-white">¡Hola! Soy tu mentor de estudio inteligente</h2>
                            <p class="text-slate-500 dark:text-slate-400 text-sm md:text-base max-w-lg mx-auto">Te ayudaré a estructurar mejores exposiciones, retener información para exámenes y simular lecciones orales o escritas con las técnicas más efectivas.</p>
                        </div>
                        
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 pt-4">
                            <button onclick="sendPrompt('Tengo una exposición importante de Biología sobre la división celular. ¿Cómo estructuro un discurso dinámico paso a paso?')" class="p-4 text-left rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 hover:border-brand-400 dark:hover:border-brand-500 transition-all group shadow-sm hover:shadow">
                                <div class="flex items-center gap-2 mb-2 text-orange-500 font-semibold text-sm">
                                    <i class="fa-solid fa-display"></i>
                                    <span>Estructurar Exposición</span>
                                </div>
                                <p class="text-xs text-slate-500 dark:text-slate-400 line-clamp-2">Tengo una exposición importante de Biología sobre la división celular. ¿Cómo la estructuro paso a paso?</p>
                            </button>

                            <button onclick="sendPrompt('Tengo un examen escrito de Historia muy difícil sobre la Segunda Guerra Mundial en 3 días. ¿Qué método de estudio rápido me recomiendas?')" class="p-4 text-left rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 hover:border-brand-400 dark:hover:border-brand-500 transition-all group shadow-sm hover:shadow">
                                <div class="flex items-center gap-2 mb-2 text-blue-500 font-semibold text-sm">
                                    <i class="fa-solid fa-file-signature"></i>
                                    <span>Tácticas para Examen</span>
                                </div>
                                <p class="text-xs text-slate-500 dark:text-slate-400 line-clamp-2">Tengo un examen escrito de Historia en 3 días. ¿Qué método rápido me recomiendas?</p>
                            </button>

                            <button onclick="sendPrompt('Tengo una lección oral sobre las leyes de la termodinámica. Hazme preguntas rápidas una por una para simular la lección oral.')" class="p-4 text-left rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 hover:border-brand-400 dark:hover:border-brand-500 transition-all group shadow-sm hover:shadow">
                                <div class="flex items-center gap-2 mb-2 text-emerald-500 font-semibold text-sm">
                                    <i class="fa-solid fa-comments"></i>
                                    <span>Simulador Lección Oral</span>
                                </div>
                                <p class="text-xs text-slate-500 dark:text-slate-400 line-clamp-2">Simula una lección oral de Física. Hazme preguntas de leyes de termodinámica una por una.</p>
                            </button>

                            <button onclick="sendPrompt('Enséñame el método de estudio de Feynman con un ejemplo práctico para entender Química Orgánica.')" class="p-4 text-left rounded-xl border border-slate-200 dark:border-slate-700 bg-white dark:bg-slate-800 hover:border-brand-400 dark:hover:border-brand-500 transition-all group shadow-sm hover:shadow">
                                <div class="flex items-center gap-2 mb-2 text-purple-500 font-semibold text-sm">
                                    <i class="fa-solid fa-pen-fancy"></i>
                                    <span>Técnica Feynman</span>
                                </div>
                                <p class="text-xs text-slate-500 dark:text-slate-400 line-clamp-2">Enséñame el método de estudio de Feynman para entender Química Orgánica de forma sencilla.</p>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Input de Mensaje de Chat -->
                <div class="p-4 bg-white dark:bg-slate-800 border-t border-slate-200 dark:border-slate-700 flex-shrink-0">
                    <form id="chat-form" onsubmit="handleMessageSubmit(event)" class="max-w-4xl mx-auto flex gap-3 items-center">
                        <div class="relative flex-1">
                            <input 
                                type="text" 
                                id="message-input" 
                                placeholder="Escribe aquí tu duda, materia o el tema que estás repasando..." 
                                class="w-full pl-4 pr-12 py-3.5 bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm placeholder:text-slate-400 dark:placeholder:text-slate-500 dark:text-slate-100"
                            >
                        </div>
                        <button type="submit" class="bg-brand-600 hover:bg-brand-700 text-white p-3.5 rounded-xl flex items-center justify-center transition-all shadow-md shadow-brand-500/20">
                            <i class="fa-solid fa-paper-plane text-sm"></i>
                        </button>
                    </form>
                    <div class="max-w-4xl mx-auto flex justify-between items-center mt-2 px-1">
                        <span class="text-[10px] text-slate-400 dark:text-slate-500">EstudiaPro analiza y estructura tus contenidos automáticamente.</span>
                        <button onclick="clearChat()" class="text-xs text-slate-400 hover:text-slate-600 dark:hover:text-slate-350">Limpiar pantalla</button>
                    </div>
                </div>
            </div>

            <!-- ANALIZADOR DE DOCUMENTOS Y NOTAS -->
            <div id="workspace-analizador" class="hidden flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                <div class="max-w-4xl mx-auto bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm">
                    <div class="flex items-center gap-3 mb-6 border-b border-slate-100 dark:border-slate-700 pb-4">
                        <div class="w-10 h-10 rounded-xl bg-brand-100 dark:bg-brand-900/40 text-brand-600 dark:text-brand-400 flex items-center justify-center text-lg">
                            <i class="fa-solid fa-file-import"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-lg">Analizador de Documentos, Temarios y Notas</h3>
                            <p class="text-xs text-slate-500">Escribe o pega tus apuntes, resúmenes, libros o materias para habilitar todas las herramientas de estudio con tu propio material.</p>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Escribe o pega tu información aquí</label>
                            <textarea id="analizador-input-text" rows="8" placeholder="Pega aquí el contenido de tu clase, diapositivas, textos de libros, notas desorganizadas o temarios..." class="w-full px-4 py-3 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm leading-relaxed dark:text-slate-100"></textarea>
                        </div>

                        <!-- Botones de Acción Rápida para el Documento -->
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-3">
                            <button onclick="processMaterial('cornell')" class="p-3 bg-violet-600 hover:bg-violet-700 text-white rounded-xl text-xs font-semibold flex flex-col items-center gap-2 transition-all shadow-sm">
                                <i class="fa-solid fa-list-check text-base"></i>
                                <span>Formatear Cornell</span>
                            </button>
                            <button onclick="processMaterial('flashcards')" class="p-3 bg-pink-600 hover:bg-pink-700 text-white rounded-xl text-xs font-semibold flex flex-col items-center gap-2 transition-all shadow-sm">
                                <i class="fa-solid fa-layer-group text-base"></i>
                                <span>Crear Flashcards</span>
                            </button>
                            <button onclick="processMaterial('dictado')" class="p-3 bg-indigo-600 hover:bg-indigo-700 text-white rounded-xl text-xs font-semibold flex flex-col items-center gap-2 transition-all shadow-sm">
                                <i class="fa-solid fa-microphone text-base"></i>
                                <span>Enviar a Dictado</span>
                            </button>
                            <button onclick="processMaterial('simulador')" class="p-3 bg-amber-600 hover:bg-amber-700 text-white rounded-xl text-xs font-semibold flex flex-col items-center gap-2 transition-all shadow-sm">
                                <i class="fa-solid fa-graduation-cap text-base"></i>
                                <span>Iniciar Examen IA</span>
                            </button>
                        </div>

                        <!-- Botón Principal: Análisis General -->
                        <button onclick="processMaterial('general')" class="w-full bg-gradient-to-r from-brand-600 to-indigo-600 hover:from-brand-700 hover:to-indigo-700 text-white font-semibold py-3.5 rounded-xl transition-all shadow-md flex items-center justify-center gap-2 text-sm mt-4">
                            <i class="fa-solid fa-wand-magic-sparkles"></i>
                            Análisis General del Material (Extraer Resumen, Ideas y Método Sugerido)
                        </button>
                    </div>

                    <!-- Panel de Resultados del Análisis -->
                    <div id="analizador-resultados" class="mt-8 hidden border-t border-slate-100 dark:border-slate-700 pt-6 space-y-4">
                        <div class="flex items-center justify-between">
                            <h4 id="analizador-res-titulo" class="font-bold text-slate-800 dark:text-slate-100">Resultado del Análisis</h4>
                            <div class="flex gap-2">
                                <button onclick="copyToClipboard('analizador-res-text')" class="text-xs text-brand-600 hover:text-brand-800 flex items-center gap-1"><i class="fa-regular fa-copy"></i> Copiar</button>
                            </div>
                        </div>

                        <div id="analizador-res-text" class="p-5 bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 rounded-xl text-sm leading-relaxed text-slate-700 dark:text-slate-200 overflow-y-auto max-h-[400px]">
                            <!-- Contenido inyectado por JS -->
                        </div>
                    </div>
                </div>
            </div>

            <!-- CATALOGO DE METODOS DE ESTUDIO -->
            <div id="workspace-metodos" class="hidden flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                <div class="max-w-5xl mx-auto space-y-6">
                    <div class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm">
                        <div class="flex items-center gap-3 mb-4 border-b border-slate-100 dark:border-slate-700 pb-4">
                            <div class="w-10 h-10 rounded-xl bg-violet-100 dark:bg-violet-900/40 text-violet-600 dark:text-violet-400 flex items-center justify-center text-lg">
                                <i class="fa-solid fa-shapes"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-lg">Catálogo Completo de Métodos de Estudio</h3>
                                <p class="text-xs text-slate-500">Haz clic en cualquier método para desplegar una guía interactiva, ejemplos de aplicación o herramientas instantáneas.</p>
                            </div>
                        </div>

                        <!-- Grid de Métodos -->
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                            <!-- Cornell -->
                            <div onclick="selectMethodDetail('cornell')" class="p-4 rounded-xl border border-slate-200 dark:border-slate-700 hover:border-violet-500 cursor-pointer bg-slate-50/50 dark:bg-slate-900/20 transition-all">
                                <span class="text-xs font-bold text-violet-600 uppercase tracking-wider block mb-1">Estructura visual</span>
                                <h4 class="font-bold text-sm text-slate-800 dark:text-white mb-1">Método de Cornell</h4>
                                <p class="text-xs text-slate-500 line-clamp-2">Organiza tus notas en ideas clave, apuntes detallados y un resumen de cierre.</p>
                            </div>

                            <!-- Leitner -->
                            <div onclick="selectMethodDetail('leitner')" class="p-4 rounded-xl border border-slate-200 dark:border-slate-700 hover:border-violet-500 cursor-pointer bg-slate-50/50 dark:bg-slate-900/20 transition-all">
                                <span class="text-xs font-bold text-pink-600 uppercase tracking-wider block mb-1">Repetición Espaciada</span>
                                <h4 class="font-bold text-sm text-slate-800 dark:text-white mb-1">Sistema de Leitner</h4>
                                <p class="text-xs text-slate-500 line-clamp-2">Repasa flashcards organizadas en cajas de dificultad para maximizar la retención.</p>
                            </div>

                            <!-- Feynman -->
                            <div onclick="selectMethodDetail('feynman')" class="p-4 rounded-xl border border-slate-200 dark:border-slate-700 hover:border-violet-500 cursor-pointer bg-slate-50/50 dark:bg-slate-900/20 transition-all">
                                <span class="text-xs font-bold text-orange-600 uppercase tracking-wider block mb-1">Para Exposiciones</span>
                                <h4 class="font-bold text-sm text-slate-800 dark:text-white mb-1">Técnica de Feynman</h4>
                                <p class="text-xs text-slate-500 line-clamp-2">Explica un tema complejo con palabras ultra-sencillas como si se lo enseñaras a un niño.</p>
                            </div>

                            <!-- Blurting -->
                            <div onclick="selectMethodDetail('blurting')" class="p-4 rounded-xl border border-slate-200 dark:border-slate-700 hover:border-violet-500 cursor-pointer bg-slate-50/50 dark:bg-slate-900/20 transition-all">
                                <span class="text-xs font-bold text-emerald-600 uppercase tracking-wider block mb-1">Exámenes Escritos</span>
                                <h4 class="font-bold text-sm text-slate-800 dark:text-white mb-1">Método de Blurting</h4>
                                <p class="text-xs text-slate-500 line-clamp-2">Volcado mental veloz del contenido de memoria, seguido de una corrección selectiva.</p>
                            </div>

                            <!-- SQ3R -->
                            <div onclick="selectMethodDetail('sq3r')" class="p-4 rounded-xl border border-slate-200 dark:border-slate-700 hover:border-violet-500 cursor-pointer bg-slate-50/50 dark:bg-slate-900/20 transition-all">
                                <span class="text-xs font-bold text-blue-600 uppercase tracking-wider block mb-1">Lectura Crítica</span>
                                <h4 class="font-bold text-sm text-slate-800 dark:text-white mb-1">Método SQ3R</h4>
                                <p class="text-xs text-slate-500 line-clamp-2">Examinar, Preguntar, Leer, Recitar y Repasar para textos densos y literatura técnica.</p>
                            </div>

                            <!-- Mind Maps -->
                            <div onclick="selectMethodDetail('mindmaps')" class="p-4 rounded-xl border border-slate-200 dark:border-slate-700 hover:border-violet-500 cursor-pointer bg-slate-50/50 dark:bg-slate-900/20 transition-all">
                                <span class="text-xs font-bold text-amber-600 uppercase tracking-wider block mb-1">Estructura Radial</span>
                                <h4 class="font-bold text-sm text-slate-800 dark:text-white mb-1">Mapas Mentales e Ideas</h4>
                                <p class="text-xs text-slate-500 line-clamp-2">Conecta conceptos clave de forma ramificada para mejorar la memoria espacial.</p>
                            </div>
                        </div>
                    </div>

                    <!-- Panel Detalle del Método de Estudio Seleccionado -->
                    <div id="metodos-detalle-container" class="hidden bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm space-y-6">
                        <div class="flex items-center justify-between border-b border-slate-100 dark:border-slate-700 pb-3">
                            <h3 id="metodo-detalle-titulo" class="font-bold text-xl text-slate-800 dark:text-white">Método Seleccionado</h3>
                            <button onclick="closeMethodDetail()" class="text-slate-400 hover:text-slate-600 dark:hover:text-slate-200"><i class="fa-solid fa-xmark"></i> Cerrar</button>
                        </div>

                        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                            <div class="md:col-span-2 space-y-4 text-sm leading-relaxed text-slate-600 dark:text-slate-300">
                                <p id="metodo-detalle-desc"></p>
                                <div class="p-4 bg-slate-50 dark:bg-slate-900 rounded-xl border border-slate-100 dark:border-slate-700 space-y-2">
                                    <h5 class="font-bold text-xs text-violet-600 uppercase">¿Cómo aplicarlo paso a paso?</h5>
                                    <ul id="metodo-detalle-pasos" class="list-disc pl-5 space-y-1.5"></ul>
                                </div>
                            </div>

                            <!-- Panel de acción específico del método -->
                            <div class="bg-violet-50/30 dark:bg-slate-900/40 p-5 border border-violet-100 dark:border-slate-700 rounded-xl flex flex-col justify-between">
                                <div>
                                    <h5 class="font-bold text-sm text-violet-700 dark:text-violet-400 mb-2">Herramienta Interactiva</h5>
                                    <p id="metodo-detalle-accion-desc" class="text-xs text-slate-500 mb-4"></p>
                                </div>
                                <div id="metodo-detalle-accion-btn-container">
                                    <!-- Botones dinámicos según el método -->
                                </div>
                            </div>
                        </div>

                        <!-- Visor de Notas Cornell Integrado (Único de Cornell) -->
                        <div id="cornell-interactive-container" class="hidden mt-4 space-y-4">
                            <h4 class="font-bold text-sm text-slate-700 dark:text-slate-300">Formato de Notas Cornell Generado:</h4>
                            <div class="border border-slate-200 dark:border-slate-700 rounded-xl overflow-hidden shadow-sm text-xs md:text-sm bg-white dark:bg-slate-900">
                                <!-- Cabecera -->
                                <div class="bg-slate-100 dark:bg-slate-800 p-4 border-b border-slate-200 dark:border-slate-700 grid grid-cols-2 gap-4">
                                    <div><strong class="text-slate-500 uppercase text-[10px]">Tema:</strong> <span id="cornell-header-tema" class="font-semibold text-slate-800 dark:text-slate-100">-</span></div>
                                    <div class="text-right"><strong class="text-slate-500 uppercase text-[10px]">Método:</strong> <span class="font-semibold text-violet-600">Apuntes Cornell IA</span></div>
                                </div>
                                <!-- Cuerpo Dos Columnas -->
                                <div class="grid grid-cols-3 min-h-[250px]">
                                    <!-- Columna Palabras Clave / Preguntas -->
                                    <div class="col-span-1 border-r border-slate-200 dark:border-slate-700 p-4 bg-slate-50/50 dark:bg-slate-900/50 space-y-3">
                                        <h5 class="font-bold text-slate-400 uppercase text-[9px] tracking-wider">Palabras Clave / Preguntas</h5>
                                        <div id="cornell-col-keys" class="whitespace-pre-line leading-relaxed text-slate-700 dark:text-slate-200 font-medium"></div>
                                    </div>
                                    <!-- Columna Notas Detalladas -->
                                    <div class="col-span-2 p-4 space-y-3">
                                        <h5 class="font-bold text-slate-400 uppercase text-[9px] tracking-wider">Apuntes e Ideas de Clase</h5>
                                        <div id="cornell-col-notes" class="whitespace-pre-line leading-relaxed text-slate-700 dark:text-slate-200"></div>
                                    </div>
                                </div>
                                <!-- Resumen Inferior -->
                                <div class="border-t border-slate-200 dark:border-slate-700 p-4 bg-violet-50/20 dark:bg-violet-950/20 space-y-2">
                                    <h5 class="font-bold text-violet-600 dark:text-violet-400 uppercase text-[9px] tracking-wider">Resumen Síntesis</h5>
                                    <div id="cornell-row-summary" class="whitespace-pre-line leading-relaxed text-slate-700 dark:text-slate-200 italic font-medium"></div>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>

            <!-- PLANIFICADOR DE ESTUDIOS -->
            <div id="workspace-planificador" class="hidden flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                <div class="max-w-3xl mx-auto bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm">
                    <div class="flex items-center gap-3 mb-6 border-b border-slate-100 dark:border-slate-700 pb-4">
                        <div class="w-10 h-10 rounded-xl bg-brand-100 dark:bg-brand-900/40 text-brand-600 dark:text-brand-400 flex items-center justify-center text-lg">
                            <i class="fa-solid fa-calendar-days"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-lg">Generador de Planes de Estudio</h3>
                            <p class="text-xs text-slate-500">Ingresa tus datos y nuestra IA creará un cronograma estructurado con las mejores técnicas.</p>
                        </div>
                    </div>

                    <form id="planificador-form" onsubmit="generateStudyPlan(event)" class="space-y-4">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Tema / Materia</label>
                                <input type="text" id="plan-tema" required placeholder="Ej: Historia Universal, Geometría Analítica" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Tipo de Evaluación</label>
                                <select id="plan-tipo" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm">
                                    <option value="Exposición Pública con diapositivas">Exposición con Diapositivas</option>
                                    <option value="Examen Escrito Integral">Examen Escrito Temático</option>
                                    <option value="Lección Oral Interactiva">Lección Oral o Defensa</option>
                                    <option value="Lección Escrita Rápida">Lección Escrita Práctica</option>
                                </select>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Días disponibles para estudiar</label>
                                <input type="number" id="plan-dias" required min="1" max="30" value="5" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Horas diarias de estudio</label>
                                <input type="number" id="plan-horas" required min="1" max="12" value="2" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm">
                            </div>
                        </div>

                        <button type="submit" class="w-full bg-brand-600 hover:bg-brand-700 text-white font-semibold py-3 rounded-xl transition-all shadow-md shadow-brand-500/20 flex items-center justify-center gap-2">
                            <i class="fa-solid fa-wand-magic-sparkles"></i>
                            Crear mi Plan Personalizado
                        </button>
                    </form>

                    <div id="planificador-resultado" class="mt-8 hidden space-y-4">
                        <div class="flex items-center justify-between border-t border-slate-100 dark:border-slate-700 pt-6">
                            <h4 class="font-bold text-slate-700 dark:text-slate-300">Tu Plan de Estudio Personalizado</h4>
                            <button onclick="copyToClipboard('plan-resultado-text')" class="text-xs font-semibold text-brand-600 hover:text-brand-800 flex items-center gap-1.5">
                                <i class="fa-regular fa-copy"></i> Copiar Plan
                            </button>
                        </div>
                        <div id="plan-resultado-text" class="p-5 bg-slate-50 dark:bg-slate-900 border border-slate-200 dark:border-slate-700 rounded-xl text-sm leading-relaxed whitespace-pre-line text-slate-600 dark:text-slate-300">
                            <!-- Inyectado por JS -->
                        </div>
                    </div>
                </div>
            </div>

            <!-- FLASHCARDS Y CAJAS LEITNER -->
            <div id="workspace-flashcards" class="hidden flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                <div class="max-w-3xl mx-auto space-y-6">
                    <div class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm">
                        <div class="flex items-center gap-3 mb-6 border-b border-slate-100 dark:border-slate-700 pb-4">
                            <div class="w-10 h-10 rounded-xl bg-pink-100 dark:bg-pink-900/40 text-pink-600 dark:text-pink-400 flex items-center justify-center text-lg">
                                <i class="fa-solid fa-cards-blank"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-lg">Flashcards de Repaso & Sistema Leitner</h3>
                                <p class="text-xs text-slate-500">Crea tarjetas de preguntas y respuestas. Agrúpalas en cajas según tu nivel de asimilación.</p>
                            </div>
                        </div>

                        <form id="flashcard-form" onsubmit="generateFlashcards(event)" class="space-y-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Ingresa el Tema o Texto para crear tarjetas</label>
                                <textarea id="flash-text" required rows="3" placeholder="Ingresa un tema o pega el texto que quieres memorizar..." class="w-full px-4 py-3 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm"></textarea>
                            </div>
                            <button type="submit" class="w-full bg-pink-600 hover:bg-pink-700 text-white font-semibold py-3 rounded-xl transition-all shadow-md shadow-pink-500/20 flex items-center justify-center gap-2">
                                <i class="fa-solid fa-sparkles"></i>
                                Generar Tarjetas Inteligentes
                            </button>
                        </form>
                    </div>

                    <!-- Panel de Cajas Leitner e Interacción -->
                    <div id="flashcards-display" class="hidden space-y-6">
                        <!-- Cajas Leitner en la Cabecera -->
                        <div class="grid grid-cols-3 gap-3">
                            <div class="p-3 bg-red-50 dark:bg-red-950/20 border border-red-100 dark:border-red-900 rounded-xl text-center">
                                <span class="text-[10px] font-bold text-red-500 uppercase tracking-wider block">Caja 1: Difícil</span>
                                <span id="leitner-box-1" class="font-extrabold text-base text-slate-700 dark:text-slate-300">0</span>
                            </div>
                            <div class="p-3 bg-amber-50 dark:bg-amber-950/20 border border-amber-100 dark:border-amber-900 rounded-xl text-center">
                                <span class="text-[10px] font-bold text-amber-500 uppercase tracking-wider block">Caja 2: Medio</span>
                                <span id="leitner-box-2" class="font-extrabold text-base text-slate-700 dark:text-slate-300">0</span>
                            </div>
                            <div class="p-3 bg-emerald-50 dark:bg-emerald-950/20 border border-emerald-100 dark:border-emerald-900 rounded-xl text-center">
                                <span class="text-[10px] font-bold text-emerald-500 uppercase tracking-wider block">Caja 3: Aprendido</span>
                                <span id="leitner-box-3" class="font-extrabold text-base text-slate-700 dark:text-slate-300">0</span>
                            </div>
                        </div>

                        <div class="flex items-center justify-between">
                            <h4 class="font-bold text-slate-700 dark:text-slate-300">Tus Tarjetas (<span id="flash-count">0</span>)</h4>
                            <span class="text-xs text-slate-400">Presiona la tarjeta para revelar la respuesta</span>
                        </div>

                        <div class="flex items-center justify-center py-4">
                            <div class="relative w-full max-w-md h-64 [perspective:1000px] cursor-pointer" onclick="flipFlashcard()">
                                <div id="flashcard-inner" class="relative w-full h-full transition-transform duration-500 [transform-style:preserve-3d] shadow-lg rounded-2xl">
                                    <!-- Cara Delantera (Pregunta) -->
                                    <div class="absolute inset-0 w-full h-full bg-gradient-to-br from-brand-50 to-indigo-50 dark:from-slate-800 dark:to-slate-750 p-8 border border-brand-100 dark:border-slate-700 rounded-2xl flex flex-col justify-between [backface-visibility:hidden]">
                                        <div class="flex items-center justify-between text-xs font-bold text-brand-600 uppercase tracking-widest">
                                            <span>Pregunta</span>
                                            <i class="fa-regular fa-circle-question"></i>
                                        </div>
                                        <p id="flashcard-question-text" class="text-center font-bold text-slate-800 dark:text-slate-100 text-lg md:text-xl">Pregunta inicial</p>
                                        <span class="text-center text-[10px] text-slate-400 font-medium">Haga clic para voltear</span>
                                    </div>
                                    <!-- Cara Trasera (Respuesta) -->
                                    <div class="absolute inset-0 w-full h-full bg-gradient-to-br from-pink-50 to-rose-50 dark:from-slate-800 dark:to-slate-750 p-8 border border-pink-100 dark:border-slate-700 rounded-2xl flex flex-col justify-between [transform:rotateY(180deg)] [backface-visibility:hidden]">
                                        <div class="flex items-center justify-between text-xs font-bold text-pink-600 uppercase tracking-widest">
                                            <span>Respuesta Explicada</span>
                                            <i class="fa-regular fa-lightbulb"></i>
                                        </div>
                                        <p id="flashcard-answer-text" class="text-center text-slate-700 dark:text-slate-200 text-base overflow-y-auto max-h-[140px] px-2">Respuesta inicial</p>
                                        <span class="text-center text-[10px] text-slate-400 font-medium">Haga clic para volver</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Calificación Leitner para Mover Tarjetas -->
                        <div class="flex justify-center gap-3 bg-slate-150/40 dark:bg-slate-800/40 p-4 rounded-xl max-w-md mx-auto">
                            <button onclick="leitnerEvaluate('box1')" class="px-4 py-2 bg-red-600 hover:bg-red-700 text-white rounded-lg text-xs font-semibold shadow-sm transition-all">
                                <i class="fa-solid fa-face-frown mr-1"></i> Difícil (Caja 1)
                            </button>
                            <button onclick="leitnerEvaluate('box2')" class="px-4 py-2 bg-amber-500 hover:bg-amber-600 text-white rounded-lg text-xs font-semibold shadow-sm transition-all">
                                <i class="fa-solid fa-face-meh mr-1"></i> Medio (Caja 2)
                            </button>
                            <button onclick="leitnerEvaluate('box3')" class="px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white rounded-lg text-xs font-semibold shadow-sm transition-all">
                                <i class="fa-solid fa-face-smile mr-1"></i> Fácil (Caja 3)
                            </button>
                        </div>

                        <!-- Controles de Navegación -->
                        <div class="flex justify-between items-center max-w-md mx-auto">
                            <button onclick="prevFlashcard()" class="flex items-center gap-2 px-4 py-2 bg-slate-200 hover:bg-slate-300 dark:bg-slate-700 dark:hover:bg-slate-600 text-slate-700 dark:text-slate-200 rounded-xl text-sm font-semibold transition-all">
                                <i class="fa-solid fa-arrow-left"></i> Anterior
                            </button>
                            <span class="text-sm font-bold text-slate-500" id="flash-progress">1 / 1</span>
                            <button onclick="nextFlashcard()" class="flex items-center gap-2 px-4 py-2 bg-slate-200 hover:bg-slate-300 dark:bg-slate-700 dark:hover:bg-slate-600 text-slate-700 dark:text-slate-200 rounded-xl text-sm font-semibold transition-all">
                                Siguiente <i class="fa-solid fa-arrow-right"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- SIMULADOR DE EXAMEN -->
            <div id="workspace-simulador" class="hidden flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                <div class="max-w-3xl mx-auto space-y-6">
                    <!-- Configuración del Simulador -->
                    <div id="sim-setup" class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm space-y-4">
                        <div class="flex items-center gap-3 mb-4 border-b border-slate-100 dark:border-slate-700 pb-4">
                            <div class="w-10 h-10 rounded-xl bg-amber-100 dark:bg-amber-900/40 text-amber-600 dark:text-amber-400 flex items-center justify-center text-lg">
                                <i class="fa-solid fa-graduation-cap"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-lg">Simulador de Examen</h3>
                                <p class="text-xs text-slate-500">Establece la materia y el profesor de la IA te hará preguntas. Responde para recibir tu calificación.</p>
                            </div>
                        </div>

                        <div class="space-y-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Materia o Tema a Evaluar</label>
                                <input type="text" id="sim-tema" placeholder="Ej: Leyes de Newton, Geometría descriptiva..." class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm">
                            </div>

                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                                <div>
                                    <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Personalidad del Profesor</label>
                                    <select id="sim-persona" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm">
                                        <option value="Un profesor extremadamente exigente pero justo. Califica rigurosamente.">Exigente / Estricto</option>
                                        <option value="Un mentor comprensivo y paciente. Te guía con cariño si cometes errores.">Paciente / Amigable</option>
                                        <option value="Un académico formal, serio y analítico que evalúa la precisión milimétrica.">Científico / Formal</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Formato del Examen</label>
                                    <select id="sim-tipo" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm">
                                        <option value="Examen Teórico Oral Corto">Preguntas de Desarrollo Cortas</option>
                                        <option value="Defensa de Proyecto Rigurosa">Preguntas Tipo "Por qué" (Defensa)</option>
                                        <option value="Examen Técnico con Ejercicios">Teórico - Práctico de Razonamiento</option>
                                    </select>
                                </div>
                            </div>

                            <button onclick="startSimulation()" class="w-full bg-amber-600 hover:bg-amber-700 text-white font-semibold py-3 rounded-xl transition-all shadow-md shadow-amber-500/20 flex items-center justify-center gap-2">
                                <i class="fa-solid fa-play"></i> Iniciar Sesión de Examen
                            </button>
                        </div>
                    </div>

                    <!-- Sesión Activa del Simulador -->
                    <div id="sim-active" class="hidden bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm space-y-6">
                        <div class="flex items-center justify-between border-b border-slate-100 dark:border-slate-700 pb-3">
                            <span class="text-xs bg-amber-100 dark:bg-amber-900/40 text-amber-700 dark:text-amber-400 px-3 py-1 rounded-full font-bold uppercase tracking-wider">Profesor en Línea</span>
                            <button onclick="stopSimulation()" class="text-xs text-red-500 hover:text-red-700 font-semibold flex items-center gap-1">
                                <i class="fa-solid fa-circle-stop"></i> Terminar Examen
                            </button>
                        </div>

                        <!-- Pregunta Actual -->
                        <div class="bg-amber-50/50 dark:bg-slate-900/50 border border-amber-100 dark:border-slate-700 rounded-xl p-5">
                            <span class="text-xs font-extrabold text-amber-600 uppercase tracking-wider block mb-2">Pregunta del Profesor:</span>
                            <p id="sim-question-box" class="text-base font-semibold leading-relaxed text-slate-800 dark:text-slate-100">
                                Cargando pregunta...
                            </p>
                        </div>

                        <!-- Respuesta del Alumno -->
                        <form onsubmit="submitSimResponse(event)" class="space-y-3">
                            <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider">Escribe tu Respuesta</label>
                            <textarea id="sim-response" required rows="4" placeholder="Argumenta tu respuesta con el mayor detalle posible..." class="w-full px-4 py-3 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm leading-relaxed dark:text-slate-100"></textarea>
                            
                            <button type="submit" class="w-full bg-amber-600 hover:bg-amber-700 text-white font-semibold py-3 rounded-xl transition-all shadow-md flex items-center justify-center gap-2">
                                <i class="fa-solid fa-paper-plane"></i> Responder y Recibir Calificación
                            </button>
                        </form>

                        <!-- Historial de Respuestas Evaluadas en esta sesión -->
                        <div id="sim-feedback-container" class="hidden space-y-3 pt-4 border-t border-slate-100 dark:border-slate-700">
                            <h4 class="font-bold text-xs uppercase text-slate-400 tracking-wider">Revisión e Historial del Examen</h4>
                            <div id="sim-feedback-box" class="space-y-4 max-h-[250px] overflow-y-auto pr-2">
                                <!-- Respuestas inyectadas dinámicamente -->
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- SIMULADOR DE DICTADO -->
            <div id="workspace-dictado" class="hidden flex-1 overflow-y-auto p-4 md:p-6 space-y-6">
                <div class="max-w-3xl mx-auto space-y-6">
                    <div class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-6 shadow-sm">
                        <div class="flex items-center gap-3 mb-6 border-b border-slate-100 dark:border-slate-700 pb-4">
                            <div class="w-10 h-10 rounded-xl bg-indigo-100 dark:bg-indigo-900/40 text-indigo-600 dark:text-indigo-400 flex items-center justify-center text-lg">
                                <i class="fa-solid fa-volume-high"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-lg">Simulador de Dictado</h3>
                                <p class="text-xs text-slate-500">Configura un texto libre y entrena tu velocidad de escritura, retención mental, ortografía o toma de notas.</p>
                            </div>
                        </div>

                        <!-- Configurar e Iniciar Dictado -->
                        <div id="dictado-setup" class="space-y-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Escribe o pega el texto para el dictado</label>
                                <textarea id="dictado-texto" rows="5" class="w-full px-4 py-3 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm dark:text-slate-100" placeholder="La fotosíntesis es el proceso mediante el cual las plantas verdes y algunos otros organismos transforman la energía luminosa en energía química. Durante este proceso, el agua y el dióxido de carbono se combinan para sintetizar carbohidratos."></textarea>
                            </div>

                            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                                <div>
                                    <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Velocidad de Voz</label>
                                    <select id="dictado-velocidad" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                                        <option value="0.65">Muy Despacio (Lento)</option>
                                        <option value="0.8" selected>Despacio (Recomendado)</option>
                                        <option value="1.0">Normal (Fluido)</option>
                                        <option value="1.2">Rápido</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Pausa entre Frases</label>
                                    <select id="dictado-pausa" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                                        <option value="1000">1 segundo</option>
                                        <option value="3000" selected>3 segundos</option>
                                        <option value="5000">5 segundos</option>
                                        <option value="8000">8 segundos</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider mb-2">Estilo de Voz</label>
                                    <select id="dictado-voz-tipo" class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                                        <option value="local">Voz Local (Sin límite)</option>
                                        <option value="gemini">Voz Premium IA (Gemini)</option>
                                    </select>
                                </div>
                            </div>

                            <div class="flex items-center gap-3 py-1">
                                <input type="checkbox" id="dictado-ciego" class="w-4.5 h-4.5 text-indigo-600 border-slate-300 rounded focus:ring-indigo-500">
                                <label for="dictado-ciego" class="text-xs font-medium text-slate-600 dark:text-slate-300">Modo "Dictado a Ciegas" (Ocultar el texto original al iniciar)</label>
                            </div>

                            <button onclick="startDictado()" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-3 rounded-xl transition-all shadow-md shadow-indigo-500/20 flex items-center justify-center gap-2">
                                <i class="fa-solid fa-circle-play"></i> Iniciar Sesión de Dictado
                            </button>
                        </div>

                        <!-- Sesión de Dictado Activa -->
                        <div id="dictado-active" class="hidden space-y-6 pt-4">
                            <div class="flex items-center justify-between border-b border-slate-100 dark:border-slate-700 pb-3">
                                <span class="text-xs bg-indigo-100 dark:bg-indigo-900/40 text-indigo-700 dark:text-indigo-400 px-3 py-1 rounded-full font-bold uppercase tracking-wider">Dictado en Progreso</span>
                                <div class="flex gap-2">
                                    <button id="btn-dictado-voz-ia" onclick="repeatPremiumSentence()" class="text-xs bg-pink-100 hover:bg-pink-200 dark:bg-pink-900/40 text-pink-700 dark:text-pink-300 px-2 py-1 rounded hidden transition-all flex items-center gap-1">
                                        <i class="fa-solid fa-wand-magic-sparkles"></i> Escuchar Voz IA
                                    </button>
                                    <button onclick="stopDictado()" class="text-xs text-red-500 hover:text-red-700 font-semibold flex items-center gap-1">
                                        <i class="fa-solid fa-circle-stop"></i> Detener
                                    </button>
                                </div>
                            </div>

                            <div id="dictado-guia-box" class="bg-indigo-50/30 dark:bg-slate-900/40 border border-indigo-100 dark:border-slate-700 rounded-xl p-4">
                                <span class="text-xs text-indigo-600 dark:text-indigo-400 font-bold uppercase tracking-wider block mb-2">Frase actual:</span>
                                <p id="dictado-frase-actual" class="text-base font-semibold leading-relaxed text-slate-800 dark:text-slate-100">
                                    Preparando dictado...
                                </p>
                                <p id="dictado-frase-oculta" class="text-sm italic text-slate-400 dark:text-slate-500 hidden">
                                    <i class="fa-solid fa-eye-slash mr-1"></i> Modo Dictado a Ciegas Activo. Escucha atentamente y escribe abajo.
                                </p>
                            </div>

                            <div class="space-y-3">
                                <div class="flex justify-between items-center">
                                    <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider">Escribe el dictado aquí abajo</label>
                                    <span id="dictado-progress-status" class="text-xs font-semibold text-indigo-600">Frase 1 de 1</span>
                                </div>
                                <textarea id="dictado-escrito-usuario" rows="4" placeholder="Comienza a escribir tan pronto como escuches la voz..." class="w-full px-4 py-3 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm dark:text-slate-100"></textarea>
                            </div>

                            <div class="grid grid-cols-2 gap-3">
                                <button onclick="pauseDictadoResume()" id="btn-dictado-pause" class="bg-slate-200 hover:bg-slate-300 dark:bg-slate-700 dark:hover:bg-slate-600 text-slate-700 dark:text-slate-200 font-semibold py-2.5 rounded-xl transition-all text-sm flex items-center justify-center gap-1.5">
                                    <i class="fa-solid fa-pause"></i> Pausar Dictado
                                </button>
                                <button onclick="evaluateDictation()" class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-2.5 rounded-xl transition-all text-sm flex items-center justify-center gap-1.5 shadow">
                                    <i class="fa-solid fa-circle-check"></i> Finalizar y Evaluar
                                </button>
                            </div>
                        </div>

                        <!-- Evaluación de Resultados -->
                        <div id="dictado-result" class="hidden mt-8 space-y-4 pt-6 border-t border-slate-100 dark:border-slate-700">
                            <div class="flex items-center justify-between">
                                <h4 class="font-bold text-slate-700 dark:text-slate-300">Resultados de tu Dictado</h4>
                                <span id="dictado-precision-badge" class="text-xs font-extrabold px-3 py-1 rounded-full">90% Precisión</span>
                            </div>

                            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                <div class="p-4 bg-emerald-50/50 dark:bg-emerald-950/20 border border-emerald-100 dark:border-emerald-850 rounded-xl space-y-1">
                                    <span class="text-xs font-bold text-emerald-600 dark:text-emerald-400 uppercase tracking-widest">Texto Original</span>
                                    <p id="dictado-res-original" class="text-xs text-slate-600 dark:text-slate-300 leading-relaxed"></p>
                                </div>
                                <div class="p-4 bg-brand-50/50 dark:bg-slate-900/50 border border-slate-200 dark:border-slate-700 rounded-xl space-y-1">
                                    <span class="text-xs font-bold text-brand-600 dark:text-brand-400 uppercase tracking-widest">Tu Texto Escrito</span>
                                    <p id="dictado-res-usuario" class="text-xs text-slate-600 dark:text-slate-300 leading-relaxed"></p>
                                </div>
                            </div>

                            <div class="p-4 bg-slate-50 dark:bg-slate-900 rounded-xl border border-slate-100 dark:border-slate-700">
                                <h5 class="text-xs font-bold text-indigo-600 mb-1 uppercase">Retroalimentación Ortográfica:</h5>
                                <p id="dictado-retro-ia" class="text-xs text-slate-500 dark:text-slate-400 leading-relaxed">
                                    Calculando corrección...
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

        </main>
    </div>

    <!-- Modal Configuración API Key -->
    <div id="settings-modal" class="fixed inset-0 bg-slate-950/50 backdrop-blur-sm flex items-center justify-center z-50 hidden transition-opacity duration-300">
        <div class="bg-white dark:bg-slate-800 rounded-2xl max-w-md w-full mx-4 p-6 border border-slate-200 dark:border-slate-700 shadow-2xl space-y-4">
            <div class="flex items-center justify-between border-b border-slate-100 dark:border-slate-700 pb-3">
                <div class="flex items-center gap-2 text-brand-600 dark:text-brand-400 font-bold">
                    <i class="fa-solid fa-gears"></i>
                    <h3>Configuración de Clave API</h3>
                </div>
                <button onclick="closeSettingsModal()" class="text-slate-400 hover:text-slate-600 dark:hover:text-slate-200">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>
            
            <p class="text-xs text-slate-500 dark:text-slate-400 leading-relaxed">
                Nuestra plataforma cuenta con una clave API integrada por defecto de forma segura en el ecosistema. Si prefieres utilizar tu propia clave de Google Gemini para expandir cuotas de uso de forma privada, puedes ingresarla aquí.
            </p>

            <div class="space-y-2">
                <label class="block text-xs font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-widest">Google Gemini API Key</label>
                <div class="relative">
                    <input type="password" id="api-key-input" placeholder="AIzaSy..." class="w-full px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-700 bg-slate-50 dark:bg-slate-950 focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm">
                </div>
            </div>

            <div class="flex gap-2 justify-end pt-2">
                <button onclick="closeSettingsModal()" class="px-4 py-2 rounded-xl text-xs font-semibold bg-slate-100 hover:bg-slate-200 dark:bg-slate-700 dark:hover:bg-slate-600 text-slate-700 dark:text-slate-200 transition-all">Cancelar</button>
                <button onclick="saveApiKey()" class="px-4 py-2 rounded-xl text-xs font-semibold bg-brand-600 hover:bg-brand-700 text-white transition-all shadow shadow-brand-500/10">Guardar Clave</button>
            </div>
        </div>
    </div>

    <div id="toast-container" class="fixed bottom-5 right-5 z-50 space-y-2 max-w-sm w-full"></div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        let currentCategory = 'general';
        let currentActiveView = 'chat'; // 'chat', 'analizador', 'metodos', 'planificador', 'flashcards', 'simulador', 'dictado'
        let chatHistory = [];
        let flashcardsList = [];
        let currentFlashcardIndex = 0;
        let simHistory = [];
        let simTemaActivo = "";
        let simPersonaActivo = "";
        let simTipoActivo = "";

        // Leitner Box State (Indices of flashcards currently stored in Box 1, 2, or 3)
        let leitnerBox1 = [];
        let leitnerBox2 = [];
        let leitnerBox3 = [];

        // Dictado Variables
        let dictadoSentences = [];
        let dictadoCurrentIndex = 0;
        let dictadoIntervalTimer = null;
        let isDictating = false;
        let isDictadoPaused = false;
        let dictadoSynthesizer = window.speechSynthesis;
        let dictadoUtterance = null;
        
        let customApiKey = localStorage.getItem('user_gemini_api_key') || "";

        const getApiUrl = () => {
            const key = customApiKey ? customApiKey : "";
            return `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${key}`;
        };

        window.onload = function() {
            if (localStorage.getItem('theme') === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
            
            document.getElementById('api-key-input').value = customApiKey;

            addSystemMessage("¡Hola! Soy EstudiaPro, tu coach de aprendizaje basado en inteligencia artificial. Escribe un tema que repasar, o bien haz clic en **'Pegar Material / Doc'** en el menú de la izquierda para analizar un documento extenso y transformarlo en flashcards, resúmenes Cornell o lecciones interactivas.");
        };

        function toggleDarkMode() {
            if (document.documentElement.classList.contains('dark')) {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('theme', 'light');
            } else {
                document.documentElement.classList.add('dark');
                localStorage.setItem('theme', 'dark');
            }
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        function openSettingsModal() {
            document.getElementById('settings-modal').classList.remove('hidden');
        }

        function closeSettingsModal() {
            document.getElementById('settings-modal').classList.add('hidden');
        }

        function saveApiKey() {
            const val = document.getElementById('api-key-input').value.trim();
            customApiKey = val;
            localStorage.setItem('user_gemini_api_key', val);
            showToast("Clave API actualizada con éxito", "success");
            closeSettingsModal();
        }

        function showToast(message, type = "info") {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = `p-4 rounded-xl shadow-lg border text-sm flex items-center gap-3 animate-fade-in transition-all duration-300`;
            
            if (type === "success") {
                toast.className += " bg-emerald-50 dark:bg-emerald-950 border-emerald-200 dark:border-emerald-800 text-emerald-800 dark:text-emerald-200";
                toast.innerHTML = `<i class="fa-solid fa-circle-check text-emerald-500"></i><span>${message}</span>`;
            } else if (type === "error") {
                toast.className += " bg-red-50 dark:bg-red-950 border-red-200 dark:border-red-800 text-red-800 dark:text-red-200";
                toast.innerHTML = `<i class="fa-solid fa-triangle-exclamation text-red-500"></i><span>${message}</span>`;
            } else {
                toast.className += " bg-blue-50 dark:bg-slate-800 border-blue-200 dark:border-slate-700 text-blue-800 dark:text-blue-200";
                toast.innerHTML = `<i class="fa-solid fa-info-circle text-blue-500"></i><span>${message}</span>`;
            }

            container.appendChild(toast);
            setTimeout(() => {
                toast.style.opacity = '0';
                setTimeout(() => toast.remove(), 300);
            }, 4000);
        }

        function copyToClipboard(elementId) {
            const text = document.getElementById(elementId).innerText;
            const dummy = document.createElement("textarea");
            document.body.appendChild(dummy);
            dummy.value = text;
            dummy.select();
            document.execCommand("copy");
            document.body.removeChild(dummy);
            showToast("Contenido copiado", "success");
        }

        function selectCategory(category) {
            currentCategory = category;
            currentActiveView = 'chat';
            
            document.querySelectorAll('.category-btn, .tool-btn').forEach(btn => {
                btn.classList.remove('bg-brand-50', 'dark:bg-brand-900/30', 'text-brand-600', 'dark:text-brand-400', 'border-l-4', 'border-brand-500');
            });
            
            const activeBtn = document.getElementById(`btn-${category}`);
            if (activeBtn) {
                activeBtn.classList.add('bg-brand-50', 'dark:bg-brand-900/30', 'text-brand-600', 'dark:text-brand-400', 'border-l-4', 'border-brand-500');
            }

            document.getElementById('chat-workspace').classList.remove('hidden');
            document.getElementById('workspace-analizador').classList.add('hidden');
            document.getElementById('workspace-metodos').classList.add('hidden');
            document.getElementById('workspace-planificador').classList.add('hidden');
            document.getElementById('workspace-flashcards').classList.add('hidden');
            document.getElementById('workspace-simulador').classList.add('hidden');
            document.getElementById('workspace-dictado').classList.add('hidden');

            const headers = {
                'exposicion': { text: 'Estudio de Exposiciones', iconClass: 'bg-orange-500' },
                'examen_escrito': { text: 'Tácticas de Exámenes Escritos', iconClass: 'bg-blue-500' },
                'leccion_oral': { text: 'Repaso de Lecciones Orales', iconClass: 'bg-emerald-500' },
                'leccion_escrita': { text: 'Preparar Lección Escrita', iconClass: 'bg-purple-500' }
            };

            const headerConf = headers[category];
            document.getElementById('header-title').innerText = headerConf.text;
            const icon = document.getElementById('header-icon');
            icon.className = `w-2.5 h-2.5 rounded-full ${headerConf.iconClass}`;

            document.getElementById('mobile-menu').classList.add('hidden');
        }

        function openTool(tool) {
            currentActiveView = tool;
            
            document.querySelectorAll('.category-btn, .tool-btn').forEach(btn => {
                btn.classList.remove('bg-brand-50', 'dark:bg-brand-900/30', 'text-brand-600', 'dark:text-brand-400', 'border-l-4', 'border-brand-500');
            });
            
            const activeBtn = document.getElementById(`btn-tool-${tool}`);
            if (activeBtn) {
                activeBtn.classList.add('bg-brand-50', 'dark:bg-brand-900/30', 'text-brand-600', 'dark:text-brand-400', 'border-l-4', 'border-brand-500');
            }

            document.getElementById('chat-workspace').classList.add('hidden');
            document.getElementById('workspace-analizador').classList.add('hidden');
            document.getElementById('workspace-metodos').classList.add('hidden');
            document.getElementById('workspace-planificador').classList.add('hidden');
            document.getElementById('workspace-flashcards').classList.add('hidden');
            document.getElementById('workspace-simulador').classList.add('hidden');
            document.getElementById('workspace-dictado').classList.add('hidden');

            const toolViews = {
                'analizador': { id: 'workspace-analizador', title: 'Analizar Notas y Documentos', icon: 'bg-brand-500' },
                'metodos': { id: 'workspace-metodos', title: 'Catálogo de Métodos de Estudio', icon: 'bg-violet-500' },
                'planificador': { id: 'workspace-planificador', title: 'Generador de Plan de Estudio', icon: 'bg-brand-500' },
                'flashcards': { id: 'workspace-flashcards', title: 'Flashcards & Sistema Leitner', icon: 'bg-pink-500' },
                'simulador': { id: 'workspace-simulador', title: 'Simulador de Examen con Profesor', icon: 'bg-amber-500' },
                'dictado': { id: 'workspace-dictado', title: 'Simulador de Dictado de Apuntes', icon: 'bg-indigo-500' }
            };

            const activeView = toolViews[tool];
            document.getElementById(activeView.id).classList.remove('hidden');
            document.getElementById('header-title').innerText = activeView.title;
            const icon = document.getElementById('header-icon');
            icon.className = `w-2.5 h-2.5 rounded-full ${activeView.icon}`;

            document.getElementById('mobile-menu').classList.add('hidden');
            
            if (tool !== 'dictado' && isDictating) {
                stopDictado();
            }
        }

        async function fetchGeminiAPI(systemInstruction, userQuery, isJSONResponse = false, schema = null) {
            const url = getApiUrl();
            const payload = {
                contents: [{
                    parts: [{ text: userQuery }]
                }],
                systemInstruction: {
                    parts: [{ text: systemInstruction }]
                }
            };

            if (isJSONResponse && schema) {
                payload.generationConfig = {
                    responseMimeType: "application/json",
                    responseSchema: schema
                };
            }

            let delay = 1000;
            const maxRetries = 3;
            
            for (let attempt = 1; attempt <= maxRetries; attempt++) {
                try {
                    const response = await fetch(url, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    if (!response.ok) {
                        throw new Error(`Error de API: ${response.status}`);
                    }

                    const result = await response.json();
                    const text = result.candidates?.[0]?.content?.parts?.[0]?.text;
                    if (text) {
                        return text;
                    } else {
                        throw new Error("Respuesta vacía o incorrecta");
                    }
                } catch (error) {
                    if (attempt === maxRetries) {
                        throw error;
                    }
                    await new Promise(resolve => setTimeout(resolve, delay));
                    delay *= 2;
                }
            }
        }

        async function processMaterial(mode) {
            const text = document.getElementById('analizador-input-text').value.trim();
            if (!text) {
                showToast("Por favor escribe o pega algo de información para analizar.", "error");
                return;
            }

            const resultsContainer = document.getElementById('analizador-resultados');
            const resultsText = document.getElementById('analizador-res-text');
            const resultsTitle = document.getElementById('analizador-res-titulo');

            resultsContainer.classList.remove('hidden');
            resultsText.innerHTML = `<div class="flex items-center gap-3 text-slate-500 justify-center py-6">
                <i class="fa-solid fa-spinner animate-spin text-brand-600 text-xl"></i>
                <span>Analizando tu material con Inteligencia Artificial...</span>
            </div>`;
            resultsText.scrollIntoView({ behavior: 'smooth' });

            if (mode === 'cornell') {
                // Iniciar Generación Cornell
                resultsTitle.innerText = "Formateo Cornell de Apuntes Inteligentes";
                const sysInstruction = "Eres un organizador de contenido experto bajo la técnica de Notas de Cornell. Formatea el texto provisto por el usuario dividiéndolo estrictamente en tres secciones en formato JSON estructurado: 1) Palabras claves/Preguntas, 2) Apuntes detallados correspondientes a esas palabras clave, 3) Resumen conciso global.";
                
                const schema = {
                    type: "OBJECT",
                    properties: {
                        tema: { type: "STRING" },
                        palabrasClave: { type: "STRING" },
                        apuntes: { type: "STRING" },
                        resumen: { type: "STRING" }
                    },
                    required: ["tema", "palabrasClave", "apuntes", "resumen"]
                };

                try {
                    const jsonRes = await fetchGeminiAPI(sysInstruction, `Genera las notas Cornell para: "${text}"`, true, schema);
                    const cornellData = JSON.parse(jsonRes);

                    // Poblar el Visor Cornell de Catálogo de Métodos
                    document.getElementById('cornell-header-tema').innerText = cornellData.tema;
                    document.getElementById('cornell-col-keys').innerText = cornellData.palabrasClave;
                    document.getElementById('cornell-col-notes').innerText = cornellData.apuntes;
                    document.getElementById('cornell-row-summary').innerText = cornellData.resumen;

                    // Abrir e interactuar en Métodos
                    openTool('metodos');
                    selectMethodDetail('cornell');
                    showToast("¡Notas Cornell formateadas y listas!", "success");

                } catch (error) {
                    console.error(error);
                    resultsText.innerHTML = `<span class="text-red-500"><i class="fa-solid fa-triangle-exclamation mr-2"></i> Error al formatear método Cornell. Intenta de nuevo.</span>`;
                }

            } else if (mode === 'flashcards') {
                // Transferir y generar
                openTool('flashcards');
                document.getElementById('flash-text').value = text;
                showToast("Texto transferido. Generando Flashcards...", "info");
                document.getElementById('flashcard-form').requestSubmit();

            } else if (mode === 'dictado') {
                // Transferir y configurar dictado
                openTool('dictado');
                document.getElementById('dictado-texto').value = text;
                showToast("Material enviado al simulador de dictado.", "success");

            } else if (mode === 'simulador') {
                // Configurar el simulador con este tema
                openTool('simulador');
                document.getElementById('sim-tema').value = text.substring(0, 80) + "...";
                showToast("Tema transferido al evaluador. Listo para iniciar.", "success");

            } else {
                // Análisis general de Estudio
                resultsTitle.innerText = "Resumen, Ideas Clave y Método de Estudio Recomendado";
                const sysInstruction = "Eres un analista de textos académicos de alto rendimiento. Analiza el documento ingresado y produce un informe en español con: 1) Resumen breve estructurado, 2) Glosario de ideas o términos fundamentales, 3) Recomendación personalizada de cuál es el MEJOR método de estudio para este texto específico.";

                try {
                    const analysis = await fetchGeminiAPI(sysInstruction, `Analiza el siguiente material: "${text}"`);
                    resultsText.innerHTML = formatPlanResult(analysis);
                } catch (error) {
                    console.error(error);
                    resultsText.innerHTML = `<span class="text-red-500"><i class="fa-solid fa-triangle-exclamation mr-2"></i> Error al contactar con la IA para analizar el documento.</span>`;
                }
            }
        }

        const methodsCatalogData = {
            'cornell': {
                title: 'Método de Cornell',
                desc: 'Desarrollado en la Universidad de Cornell en 1940, es un sistema estructurado de toma de notas muy visual. Evita acumular apuntes desorganizados e incentiva la síntesis selectiva para revisiones de último momento.',
                pasos: [
                    'Divide tu hoja en tres secciones principales: Margen izquierdo para preguntas y palabras clave, columna derecha (más ancha) para apuntes, y franja inferior para el resumen sintetizado.',
                    'Durante la lectura o clase, toma apuntes normales y rápidos en la sección derecha.',
                    'Inmediatamente después, genera preguntas desafiantes sobre esos apuntes en la columna izquierda.',
                    'Al repasar, tapa la columna de apuntes e intenta responder las preguntas utilizando únicamente la memoria.'
                ],
                accionDesc: 'Genera notas Cornell optimizadas por IA utilizando el contenido que pegaste en el analizador de materiales.',
                btnLabel: 'Ver Visor Cornell Interactivo',
                btnClass: 'bg-violet-600 hover:bg-violet-700 text-white w-full rounded-xl py-2.5 text-xs font-bold transition-all shadow-sm',
                actionFn: function() {
                    const keys = document.getElementById('cornell-col-keys').innerText;
                    if (!keys) {
                        showToast("Primero ve a 'Pegar Material/Doc' y haz clic en 'Formatear Cornell' para poblar este visor.", "info");
                    }
                    document.getElementById('cornell-interactive-container').classList.remove('hidden');
                    document.getElementById('cornell-interactive-container').scrollIntoView({ behavior: 'smooth' });
                }
            },
            'leitner': {
                title: 'Sistema de Cajas Leitner',
                desc: 'La mejor técnica de repetición espaciada utilizando tarjetas físicas o virtuales. Se basa en agrupar las tarjetas en cajas de dificultad creciente para forzar la memoria a recordar a intervalos calculados.',
                pasos: [
                    'Empieza con todas tus flashcards en la Caja 1.',
                    'Repasa las tarjetas. Si recuerdas la respuesta de forma instantánea, muévela a la Caja 2.',
                    'Si fallas en una tarjeta de cualquier caja, esta regresa de inmediato a la Caja 1 sin importar en qué nivel estaba.',
                    'La Caja 1 se repasa diariamente, la Caja 2 cada 3 días, y la Caja 3 cada 5 días.'
                ],
                accionDesc: 'Genera un set de flashcards dinámicas mediante IA para habilitar el simulador de Cajas Leitner en EstudiaPro.',
                btnLabel: 'Ir al Repasador Leitner',
                btnClass: 'bg-pink-600 hover:bg-pink-750 text-white w-full rounded-xl py-2.5 text-xs font-bold transition-all shadow-sm',
                actionFn: function() {
                    openTool('flashcards');
                }
            },
            'feynman': {
                title: 'Técnica de Richard Feynman',
                desc: 'Creada por el físico ganador del Nobel, parte de la premisa de que "el verdadero conocimiento se mide en tu capacidad de explicar algo a otros de manera extremadamente elemental".',
                pasos: [
                    'Elige el concepto que deseas dominar por completo.',
                    'Explícalo de forma escrita u oral utilizando analogías simples y un lenguaje que un niño de 8 años pueda captar.',
                    'Identifica las zonas de tu explicación donde te trabaste o tuviste que usar palabras técnicas complejas.',
                    'Vuelve a los apuntes originales para llenar esos vacíos y simplifica la explicación aún más.'
                ],
                accionDesc: 'El chatbot te guiará evaluando tu explicación simplificada paso a paso.',
                btnLabel: 'Practicar Feynman con Chatbot',
                btnClass: 'bg-orange-500 hover:bg-orange-600 text-white w-full rounded-xl py-2.5 text-xs font-bold transition-all shadow-sm',
                actionFn: function() {
                    selectCategory('general');
                    sendPrompt("Quiero usar la Técnica Feynman. Explícame brevemente cómo interactuarás conmigo y ayúdame a repasar un tema complejo de mi elección simplificándolo.");
                }
            },
            'blurting': {
                title: 'Método de Blurting (Volcado Mental)',
                desc: 'Una técnica de memorización brutal que mide exactamente qué recuerdas y qué has olvidado. Evita el "efecto ilusión de competencia" donde crees que lo sabes todo solo por leer tus notas.',
                pasos: [
                    'Lee detenidamente un capítulo de tus apuntes durante 15 minutos de forma súper enfocada.',
                    'Cierra el documento y pon un temporizador de 5 minutos.',
                    'Escribe en una hoja (o procesador) absolutamente todo lo que recuerdes, tan rápido como puedas, sin detenerte a formatear.',
                    'Abre tus apuntes de nuevo y resalta en rojo o color contrastante toda la información crucial que omitiste.'
                ],
                accionDesc: 'Utiliza el área de escritura libre del dictador o del chatbot de EstudiaPro para realizar un volcado libre.',
                btnLabel: 'Hacer Volcado en Chat',
                btnClass: 'bg-emerald-600 hover:bg-emerald-700 text-white w-full rounded-xl py-2.5 text-xs font-bold transition-all shadow-sm',
                actionFn: function() {
                    selectCategory('general');
                    sendPrompt("Quiero que me evalúes mediante la técnica de Blurting. Por favor explícame cómo lo haremos.");
                }
            },
            'sq3r': {
                title: 'SQ3R (Survey, Question, Read, Recite, Review)',
                desc: 'Diseñado para abordar libros densos y temarios técnicos extensos. Consiste en una lectura activa de 5 fases para garantizar que la información no entre por un oído y salga por el otro.',
                pasos: [
                    'Survey (Inspeccionar): Ojear títulos, subtítulos, gráficos y resúmenes del capítulo en 2 minutos.',
                    'Question (Preguntar): Convertir cada título en una pregunta (ej. si el título es "Leyes de Kepler", pregúntate "¿Qué son las leyes de Kepler?").',
                    'Read (Leer): Leer con concentración buscando responder activamente la pregunta formulada en el paso previo.',
                    'Recite (Recitar): Explicar en voz alta la sección leída sin mirar el libro.',
                    'Review (Repasar): Repasar las notas tomadas periódicamente.'
                ],
                accionDesc: 'Pídele al chatbot de EstudiaPro que analice tu texto dividiéndolo en preguntas tipo SQ3R.',
                btnLabel: 'Extraer Preguntas SQ3R',
                btnClass: 'bg-blue-600 hover:bg-blue-700 text-white w-full rounded-xl py-2.5 text-xs font-bold transition-all shadow-sm',
                actionFn: function() {
                    selectCategory('examen_escrito');
                    sendPrompt("Por favor, enséñame cómo estructurar un estudio SQ3R del tema que yo elija.");
                }
            },
            'mindmaps': {
                title: 'Mapas Mentales Estructurados',
                desc: 'Un método visual asociativo que mapea la información de forma radial emulando el funcionamiento cognitivo de las conexiones neuronales.',
                pasos: [
                    'Escribe el concepto central en el centro de tu espacio en grande o con un dibujo de referencia.',
                    'Crea ramificaciones primarias para los subtemas más importantes.',
                    'Añade sub-ramificaciones para detalles, datos clave y fórmulas usando colores diferentes.',
                    'Utiliza íconos o dibujos en lugar de párrafos densos de texto.'
                ],
                accionDesc: 'Solicita a EstudiaPro IA que te diseñe un borrador textual estructurado de las ramas principales de un Mapa Mental.',
                btnLabel: 'Generar Estructura en Chat',
                btnClass: 'bg-amber-600 hover:bg-amber-700 text-white w-full rounded-xl py-2.5 text-xs font-bold transition-all shadow-sm',
                actionFn: function() {
                    selectCategory('general');
                    sendPrompt("Por favor diseña la jerarquía radial y ramas sugeridas para hacer un Mapa Mental de un tema académico.");
                }
            }
        };

        function selectMethodDetail(methodKey) {
            const data = methodsCatalogData[methodKey];
            if (!data) return;

            document.getElementById('metodo-detalle-titulo').innerText = data.title;
            document.getElementById('metodo-detalle-desc').innerText = data.desc;
            document.getElementById('metodo-detalle-accion-desc').innerText = data.accionDesc;

            const pasosList = document.getElementById('metodo-detalle-pasos');
            pasosList.innerHTML = "";
            data.pasos.forEach(p => {
                const li = document.createElement('li');
                li.innerText = p;
                pasosList.appendChild(li);
            });

            const btnContainer = document.getElementById('metodo-detalle-accion-btn-container');
            btnContainer.innerHTML = "";
            const btn = document.createElement('button');
            btn.className = data.btnClass;
            btn.innerText = data.btnLabel;
            btn.onclick = data.actionFn;
            btnContainer.appendChild(btn);

            document.getElementById('metodos-detalle-container').classList.remove('hidden');
            document.getElementById('metodos-detalle-container').scrollIntoView({ behavior: 'smooth' });
            
            if (methodKey !== 'cornell') {
                document.getElementById('cornell-interactive-container').classList.add('hidden');
            }
        }

        function closeMethodDetail() {
            document.getElementById('metodos-detalle-container').classList.add('hidden');
        }

        function resetAllWorkspaces() {
            clearChat();
            document.getElementById('analizador-input-text').value = "";
            document.getElementById('analizador-resultados').classList.add('hidden');
            document.getElementById('cornell-interactive-container').classList.add('hidden');
            document.getElementById('metodos-detalle-container').classList.add('hidden');
            
            flashcardsList = [];
            document.getElementById('flashcards-display').classList.add('hidden');
            document.getElementById('flash-text').value = "";
            
            stopSimulation();
            stopDictado();
            
            leitnerBox1 = [];
            leitnerBox2 = [];
            leitnerBox3 = [];
            updateLeitnerCounters();

            showToast("Todas las secciones han sido reseteadas.", "info");
        }

        function clearChat() {
            document.getElementById('chat-messages').innerHTML = "";
            chatHistory = [];
            const welcomeCard = document.getElementById('welcome-card');
            if (welcomeCard) {
                document.getElementById('chat-messages').appendChild(welcomeCard);
            }
        }

        function handleMessageSubmit(event) {
            event.preventDefault();
            const input = document.getElementById('message-input');
            const query = input.value.trim();
            if (!query) return;

            input.value = "";
            sendPrompt(query);
        }

        async function sendPrompt(userQuery) {
            const welcomeCard = document.getElementById('welcome-card');
            if (welcomeCard && welcomeCard.parentNode) {
                welcomeCard.remove();
            }

            addUserMessage(userQuery);
            chatHistory.push({ role: "user", text: userQuery });

            const loadingId = addLoadingIndicator();

            const systemPrompt = `Actúa como un Coach de Estudio Universitario de nivel internacional. 
            Tus especialidades son técnicas eficientes para:
            1. Exposiciones (Método Feynman, regla 10-20-30 de diapositivas, estructura Hook-Meat-Payoff).
            2. Exámenes Escritos (Repetición Espaciada, Recuperación Activa, Técnica Cornell, Blurting).
            3. Lecciones Orales (preguntas de autoevaluación, control del habla y muletillas).
            4. Lecciones Escritas (análisis de palabras claves, resúmenes óptimos).

            Responde estructuradamente en español. Brinda planes prácticos e interactivos.`;

            try {
                const reply = await fetchGeminiAPI(systemPrompt, userQuery);
                removeLoadingIndicator(loadingId);
                addSystemMessage(reply);
                chatHistory.push({ role: "model", text: reply });
            } catch (error) {
                console.error(error);
                removeLoadingIndicator(loadingId);
                addSystemMessage("Disculpa, he tenido un inconveniente técnico intentando procesar tu duda. Por favor intenta de nuevo en unos segundos.");
                showToast("Error en conexión con el motor IA", "error");
            }
        }

        function addUserMessage(text) {
            const chatBox = document.getElementById('chat-messages');
            const wrapper = document.createElement('div');
            wrapper.className = "flex justify-end animate-fade-in";
            wrapper.innerHTML = `
                <div class="max-w-[85%] bg-brand-600 text-white rounded-2xl px-5 py-3 shadow-md">
                    <p class="text-sm leading-relaxed">${escapeHtml(text)}</p>
                </div>
            `;
            chatBox.appendChild(wrapper);
            scrollToBottom();
        }

        function addSystemMessage(text) {
            const chatBox = document.getElementById('chat-messages');
            const wrapper = document.createElement('div');
            wrapper.className = "flex justify-start items-start gap-3 animate-fade-in";
            const formattedText = formatMarkdown(text);
            
            wrapper.innerHTML = `
                <div class="w-8 h-8 rounded-lg bg-gradient-to-tr from-brand-500 to-indigo-600 flex items-center justify-center text-white flex-shrink-0 text-sm shadow">
                    <i class="fa-solid fa-robot"></i>
                </div>
                <div class="max-w-[85%] bg-white dark:bg-slate-800 text-slate-800 dark:text-slate-100 rounded-2xl px-5 py-3 border border-slate-100 dark:border-slate-700 shadow-sm leading-relaxed text-sm">
                    ${formattedText}
                </div>
            `;
            chatBox.appendChild(wrapper);
            scrollToBottom();
        }

        function addLoadingIndicator() {
            const chatBox = document.getElementById('chat-messages');
            const wrapper = document.createElement('div');
            const id = "loading-" + Date.now();
            wrapper.id = id;
            wrapper.className = "flex justify-start items-center gap-3 animate-fade-in";
            wrapper.innerHTML = `
                <div class="w-8 h-8 rounded-lg bg-slate-200 dark:bg-slate-700 flex items-center justify-center text-slate-500 flex-shrink-0 text-sm">
                    <i class="fa-solid fa-spinner animate-spin"></i>
                </div>
                <div class="bg-white dark:bg-slate-800 rounded-2xl px-5 py-3 border border-slate-100 dark:border-slate-700 shadow-sm">
                    <span class="text-xs text-slate-400 dark:text-slate-500 font-medium">Buscando el mejor método de estudio...</span>
                </div>
            `;
            chatBox.appendChild(wrapper);
            scrollToBottom();
            return id;
        }

        function removeLoadingIndicator(id) {
            const el = document.getElementById(id);
            if (el) el.remove();
        }

        function scrollToBottom() {
            const chatBox = document.getElementById('chat-messages');
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function escapeHtml(text) {
            return text
                .replace(/&/g, "&amp;")
                .replace(/</g, "&lt;")
                .replace(/>/g, "&gt;")
                .replace(/"/g, "&quot;")
                .replace(/'/g, "&#039;");
        }

        function formatMarkdown(text) {
            let formatted = escapeHtml(text);
            formatted = formatted.replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>');
            formatted = formatted.replace(/\*(.*?)\*/g, '<em>$1</em>');
            formatted = formatted.replace(/\n/g, '<br>');
            return formatted;
        }

        async function generateStudyPlan(event) {
            event.preventDefault();
            const tema = document.getElementById('plan-tema').value.trim();
            const tipo = document.getElementById('plan-tipo').value;
            const dias = document.getElementById('plan-dias').value;
            const horas = document.getElementById('plan-horas').value;

            if (!tema) return;

            const rContainer = document.getElementById('planificador-resultado');
            const rText = document.getElementById('plan-resultado-text');
            
            rContainer.classList.remove('hidden');
            rText.innerHTML = `<div class="flex items-center gap-3 text-slate-500 justify-center py-6">
                <i class="fa-solid fa-spinner animate-spin text-brand-600 text-xl"></i>
                <span>Creando tu cronograma personalizado con IA...</span>
            </div>`;
            rText.scrollIntoView({ behavior: 'smooth' });

            const sysInstruction = "Eres un experto planificador de cronogramas de estudio. Estructura un cronograma diario altamente detallado, indicando metodologías avanzadas recomendadas para cada sesión.";
            const userQuery = `Diseña un plan de estudio de ${dias} días para "${tema}" para prepararme de cara a un/una "${tipo}". Tengo disponibles ${horas} horas diarias. Explica qué métodos específicos usar por bloques de tiempo.`;

            try {
                const plan = await fetchGeminiAPI(sysInstruction, userQuery);
                rText.innerHTML = formatPlanResult(plan);
            } catch (error) {
                console.error(error);
                rText.innerHTML = `<span class="text-red-500"><i class="fa-solid fa-triangle-exclamation mr-2"></i> Error al generar el plan de estudios.</span>`;
            }
        }

        function formatPlanResult(text) {
            let output = escapeHtml(text);
            output = output.replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>');
            return output;
        }

        async function generateFlashcards(event) {
            event.preventDefault();
            const textToProcess = document.getElementById('flash-text').value.trim();
            if (!textToProcess) return;

            showToast("Generando flashcards con IA...", "info");

            const sysInstruction = "Eres un asistente de estudio especializado en Recuerdo Activo. Genera un set de preguntas y respuestas cortas a partir de la información del usuario.";
            const schema = {
                type: "ARRAY",
                items: {
                    type: "OBJECT",
                    properties: {
                        pregunta: { type: "STRING" },
                        respuesta: { type: "STRING" }
                    },
                    required: ["pregunta", "respuesta"]
                }
            };

            const userQuery = `Crea de 5 a 8 flashcards esenciales para este material: "${textToProcess}"`;

            try {
                const jsonText = await fetchGeminiAPI(sysInstruction, userQuery, true, schema);
                const cards = JSON.parse(jsonText);

                if (cards && cards.length > 0) {
                    flashcardsList = cards;
                    currentFlashcardIndex = 0;
                    
                    // Inicializar Cajas Leitner
                    leitnerBox1 = cards.map((_, index) => index);
                    leitnerBox2 = [];
                    leitnerBox3 = [];

                    renderFlashcard();
                    updateLeitnerCounters();
                    
                    document.getElementById('flashcards-display').classList.remove('hidden');
                    document.getElementById('flash-count').innerText = flashcardsList.length;
                    showToast("¡Flashcards generadas e ingresadas en la Caja 1 Leitner!", "success");
                } else {
                    showToast("Formato de tarjetas inválido.", "error");
                }
            } catch (error) {
                console.error(error);
                showToast("Fallo al contactar con el generador de flashcards", "error");
            }
        }

        function renderFlashcard() {
            if (flashcardsList.length === 0) return;

            const card = flashcardsList[currentFlashcardIndex];
            const inner = document.getElementById('flashcard-inner');
            inner.style.transform = "";

            document.getElementById('flashcard-question-text').innerText = card.pregunta;
            document.getElementById('flashcard-answer-text').innerText = card.respuesta;
            document.getElementById('flash-progress').innerText = `${currentFlashcardIndex + 1} / ${flashcardsList.length}`;
        }

        function flipFlashcard() {
            const inner = document.getElementById('flashcard-inner');
            if (inner.style.transform === "rotateY(180deg)") {
                inner.style.transform = "";
            } else {
                inner.style.transform = "rotateY(180deg)";
            }
        }

        function nextFlashcard() {
            if (flashcardsList.length === 0) return;
            currentFlashcardIndex = (currentFlashcardIndex + 1) % flashcardsList.length;
            renderFlashcard();
        }

        function prevFlashcard() {
            if (flashcardsList.length === 0) return;
            currentFlashcardIndex = (currentFlashcardIndex - 1 + flashcardsList.length) % flashcardsList.length;
            renderFlashcard();
        }

        function leitnerEvaluate(boxTarget) {
            if (flashcardsList.length === 0) return;
            
            // Remover de todas las cajas anteriores para esta tarjeta actual
            leitnerBox1 = leitnerBox1.filter(idx => idx !== currentFlashcardIndex);
            leitnerBox2 = leitnerBox2.filter(idx => idx !== currentFlashcardIndex);
            leitnerBox3 = leitnerBox3.filter(idx => idx !== currentFlashcardIndex);

            if (boxTarget === 'box1') {
                leitnerBox1.push(currentFlashcardIndex);
                showToast("Tarjeta enviada a Caja 1 (Por repasar)", "info");
            } else if (boxTarget === 'box2') {
                leitnerBox2.push(currentFlashcardIndex);
                showToast("Tarjeta enviada a Caja 2 (Asimilado)", "success");
            } else {
                leitnerBox3.push(currentFlashcardIndex);
                showToast("Tarjeta enviada a Caja 3 (Completamente aprendido)", "success");
            }

            updateLeitnerCounters();
            nextFlashcard();
        }

        function updateLeitnerCounters() {
            document.getElementById('leitner-box-1').innerText = leitnerBox1.length;
            document.getElementById('leitner-box-2').innerText = leitnerBox2.length;
            document.getElementById('leitner-box-3').innerText = leitnerBox3.length;
        }

        async function startSimulation() {
            const tema = document.getElementById('sim-tema').value.trim();
            const persona = document.getElementById('sim-persona').value;
            const tipo = document.getElementById('sim-tipo').value;

            if (!tema) {
                showToast("Por favor ingresa un tema o material de evaluación", "error");
                return;
            }

            simTemaActivo = tema;
            simPersonaActivo = persona;
            simTipoActivo = tipo;
            simHistory = [];

            document.getElementById('sim-setup').classList.add('hidden');
            document.getElementById('sim-active').classList.remove('hidden');
            document.getElementById('sim-question-box').innerText = "El profesor está formulando tu primera pregunta...";
            document.getElementById('sim-feedback-container').classList.add('hidden');
            document.getElementById('sim-feedback-box').innerHTML = "";

            const systemPrompt = `Actúas como un profesor evaluando a un alumno. 
            Personalidad: ${persona}.
            Materia: ${tema}.
            Tipo de Examen: ${tipo}.

            Haz únicamente tu primera pregunta de forma rigurosa y directa. Saluda de acuerdo a tu personalidad.`;

            try {
                const primerPregunta = await fetchGeminiAPI(systemPrompt, `Inicia el examen sobre ${tema}`);
                document.getElementById('sim-question-box').innerText = primerPregunta;
                simHistory.push({ role: "model", text: primerPregunta });
            } catch (error) {
                console.error(error);
                showToast("Error de conexión al simular", "error");
                stopSimulation();
            }
        }

        async function submitSimResponse(event) {
            event.preventDefault();
            const responseInput = document.getElementById('sim-response');
            const userResponse = responseInput.value.trim();
            if (!userResponse) return;

            responseInput.value = "";
            showToast("Profesor evaluando tu respuesta...", "info");

            simHistory.push({ role: "user", text: userResponse });

            const fbContainer = document.getElementById('sim-feedback-container');
            const fbBox = document.getElementById('sim-feedback-box');
            fbContainer.classList.remove('hidden');

            const systemPrompt = `Eres un evaluador riguroso: ${simPersonaActivo} de la materia "${simTemaActivo}" para el examen "${simTipoActivo}".
            1. Califica de manera sutil e indica si la respuesta fue correcta o incompleta.
            2. Brinda una retroalimentación breve.
            3. A continuación formula la siguiente pregunta para continuar.`;

            const contextoConversacion = simHistory.map(h => `${h.role === 'model' ? 'Profesor' : 'Alumno'}: ${h.text}`).join('\n');

            try {
                const evaluacionYPregunta = await fetchGeminiAPI(systemPrompt, contextoConversacion);
                document.getElementById('sim-question-box').innerText = evaluacionYPregunta;

                const itemHistorial = document.createElement('div');
                itemHistorial.className = "p-3 rounded-lg bg-slate-100 dark:bg-slate-700/50 border border-slate-200 dark:border-slate-700 space-y-1.5";
                itemHistorial.innerHTML = `
                    <div class="text-xs text-brand-600 dark:text-brand-400 font-bold">Tu respuesta anterior:</div>
                    <p class="text-xs italic text-slate-600 dark:text-slate-300">"${userResponse}"</p>
                    <div class="text-xs text-amber-600 dark:text-amber-400 font-bold mt-1">Evaluación del Profesor:</div>
                    <p class="text-xs text-slate-800 dark:text-slate-200">${formatMarkdown(evaluacionYPregunta.split('\n')[0])}</p>
                `;
                fbBox.insertBefore(itemHistorial, fbBox.firstChild);
                simHistory.push({ role: "model", text: evaluacionYPregunta });

            } catch (error) {
                console.error(error);
                showToast("Error al obtener retroalimentación", "error");
            }
        }

        function stopSimulation() {
            document.getElementById('sim-setup').classList.remove('hidden');
            document.getElementById('sim-active').classList.add('hidden');
            simHistory = [];
        }

        function startDictado() {
            let originalText = document.getElementById('dictado-texto').value.trim();
            if (!originalText) {
                originalText = "La fotosíntesis es el proceso mediante el cual las plantas verdes y algunos otros organismos transforman la energía luminosa en energía química. Durante este proceso, el agua y el dióxido de carbono se combinan para sintetizar carbohidratos.";
                document.getElementById('dictado-texto').value = originalText;
            }

            dictadoSentences = originalText.split(/(?<=[.!?])\s+/).filter(s => s.length > 2);
            if (dictadoSentences.length === 0) {
                showToast("Por favor ingresa un texto válido para dictar.", "error");
                return;
            }

            dictadoCurrentIndex = 0;
            isDictating = true;
            isDictadoPaused = false;
            
            document.getElementById('dictado-setup').classList.add('hidden');
            document.getElementById('dictado-active').classList.remove('hidden');
            document.getElementById('dictado-result').classList.add('hidden');
            document.getElementById('dictado-escrito-usuario').value = "";

            const isCiego = document.getElementById('dictado-ciego').checked;
            if (isCiego) {
                document.getElementById('dictado-frase-actual').classList.add('hidden');
                document.getElementById('dictado-frase-oculta').classList.remove('hidden');
            } else {
                document.getElementById('dictado-frase-actual').classList.remove('hidden');
                document.getElementById('dictado-frase-oculta').classList.add('hidden');
            }

            const tVoz = document.getElementById('dictado-voz-tipo').value;
            const btnVozIA = document.getElementById('btn-dictado-voz-ia');
            if (tVoz === 'gemini') {
                btnVozIA.classList.remove('hidden');
            } else {
                btnVozIA.classList.add('hidden');
            }

            showToast("¡Dictado iniciado!", "success");
            executeDictadoStep();
        }

        async function executeDictadoStep() {
            if (!isDictating || isDictadoPaused) return;

            if (dictadoCurrentIndex >= dictadoSentences.length) {
                evaluateDictation();
                return;
            }

            const sentence = dictadoSentences[dictadoCurrentIndex];
            document.getElementById('dictado-frase-actual').innerText = sentence;
            document.getElementById('dictado-progress-status').innerText = `Frase ${dictadoCurrentIndex + 1} de ${dictadoSentences.length}`;

            const voiceStyle = document.getElementById('dictado-voz-tipo').value;
            
            if (voiceStyle === 'gemini') {
                await playSentenceGeminiTTS(sentence);
            } else {
                playSentenceLocalTTS(sentence);
            }
        }

        function playSentenceLocalTTS(text) {
            if (dictadoSynthesizer.speaking) {
                dictadoSynthesizer.cancel();
            }

            dictadoUtterance = new SpeechSynthesisUtterance(text);
            dictadoUtterance.lang = 'es-ES';
            
            const rateVal = parseFloat(document.getElementById('dictado-velocidad').value);
            dictadoUtterance.rate = rateVal;

            dictadoUtterance.onend = function() {
                if (!isDictating || isDictadoPaused) return;
                
                const msInterval = parseInt(document.getElementById('dictado-pausa').value);
                dictadoIntervalTimer = setTimeout(() => {
                    dictadoCurrentIndex++;
                    executeDictadoStep();
                }, msInterval);
            };

            dictadoUtterance.onerror = function() {
                dictadoIntervalTimer = setTimeout(() => {
                    dictadoCurrentIndex++;
                    executeDictadoStep();
                }, 4000);
            };

            dictadoSynthesizer.speak(dictadoUtterance);
        }

        async function playSentenceGeminiTTS(text) {
            const statusLabel = document.getElementById('dictado-progress-status');
            const originalStatusText = statusLabel.innerText;
            statusLabel.innerHTML = `<span class="text-pink-600 animate-pulse"><i class="fa-solid fa-spinner animate-spin"></i> Generando Voz IA Premium...</span>`;

            try {
                const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent?key=${customApiKey}`;
                const payload = {
                    contents: [{
                        parts: [{ text: `Say clearly and slowly for dictation: ${text}` }]
                    }],
                    generationConfig: {
                        responseModalities: ["AUDIO"],
                        speechConfig: {
                            voiceConfig: {
                                prebuiltVoiceConfig: { voiceName: "Erinome" }
                            }
                        }
                    }
                };

                const response = await fetch(url, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    throw new Error("TTS API request failed");
                }

                const result = await response.json();
                const part = result?.candidates?.[0]?.content?.parts?.[0];
                const audioData = part?.inlineData?.data;
                const mimeType = part?.inlineData?.mimeType;

                statusLabel.innerText = originalStatusText;

                if (audioData && mimeType && mimeType.startsWith("audio/")) {
                    const sampleRateMatch = mimeType.match(/rate=(\d+)/);
                    const sampleRate = sampleRateMatch ? parseInt(sampleRateMatch[1], 10) : 24000;
                    
                    const pcmData = base64ToArrayBuffer(audioData);
                    const pcm16 = new Int16Array(pcmData);
                    const wavBlob = pcmToWav(pcm16, sampleRate);
                    const audioUrl = URL.createObjectURL(wavBlob);
                    
                    const audio = new Audio(audioUrl);
                    const rateVal = parseFloat(document.getElementById('dictado-velocidad').value);
                    audio.playbackRate = rateVal;

                    audio.onended = function() {
                        if (!isDictating || isDictadoPaused) return;
                        
                        const msInterval = parseInt(document.getElementById('dictado-pausa').value);
                        dictadoIntervalTimer = setTimeout(() => {
                            dictadoCurrentIndex++;
                            executeDictadoStep();
                        }, msInterval);
                    };

                    audio.play();
                } else {
                    throw new Error("No audio returned");
                }
            } catch (error) {
                console.error(error);
                statusLabel.innerText = originalStatusText;
                playSentenceLocalTTS(text);
            }
        }

        async function repeatPremiumSentence() {
            if (!isDictating || dictadoCurrentIndex >= dictadoSentences.length) return;
            const sentence = dictadoSentences[dictadoCurrentIndex];
            showToast("Reproduciendo de nuevo con Voz IA...", "info");
            
            isDictadoPaused = true;
            document.getElementById('btn-dictado-pause').innerHTML = `<i class="fa-solid fa-play"></i> Reanudar Dictado`;
            
            if (dictadoSynthesizer.speaking) {
                dictadoSynthesizer.cancel();
            }
            clearTimeout(dictadoIntervalTimer);

            await playSentenceGeminiTTS(sentence);
        }

        function pauseDictadoResume() {
            const btn = document.getElementById('btn-dictado-pause');
            
            if (isDictadoPaused) {
                isDictadoPaused = false;
                btn.innerHTML = `<i class="fa-solid fa-pause"></i> Pausar Dictado`;
                showToast("Dictado reanudado", "info");
                executeDictadoStep();
            } else {
                isDictadoPaused = true;
                btn.innerHTML = `<i class="fa-solid fa-play"></i> Reanudar Dictado`;
                showToast("Dictado pausado", "info");
                if (dictadoSynthesizer.speaking) {
                    dictadoSynthesizer.cancel();
                }
                clearTimeout(dictadoIntervalTimer);
            }
        }

        function stopDictado() {
            isDictating = false;
            isDictadoPaused = false;
            clearTimeout(dictadoIntervalTimer);
            if (dictadoSynthesizer.speaking) {
                dictadoSynthesizer.cancel();
            }

            document.getElementById('dictado-setup').classList.remove('hidden');
            document.getElementById('dictado-active').classList.add('hidden');
        }

        async function evaluateDictation() {
            isDictating = false;
            clearTimeout(dictadoIntervalTimer);
            if (dictadoSynthesizer.speaking) {
                dictadoSynthesizer.cancel();
            }

            const originalText = document.getElementById('dictado-texto').value.trim();
            const userText = document.getElementById('dictado-escrito-usuario').value.trim();

            if (!userText) {
                showToast("El dictado se detuvo sin contenido.", "error");
                document.getElementById('dictado-setup').classList.remove('hidden');
                document.getElementById('dictado-active').classList.add('hidden');
                return;
            }

            const origWords = originalText.toLowerCase().replace(/[.,\/#!$%\^&\*;:{}=\-_`~()]/g,"").split(/\s+/);
            const userWords = userText.toLowerCase().replace(/[.,\/#!$%\^&\*;:{}=\-_`~()]/g,"").split(/\s+/);

            let matchingCount = 0;
            const userWordsSet = new Set(userWords);
            origWords.forEach(w => {
                if (userWordsSet.has(w)) matchingCount++;
            });

            const precision = Math.round((matchingCount / Math.max(origWords.length, 1)) * 100);

            document.getElementById('dictado-setup').classList.remove('hidden');
            document.getElementById('dictado-active').classList.add('hidden');
            
            const rContainer = document.getElementById('dictado-result');
            rContainer.classList.remove('hidden');
            rContainer.scrollIntoView({ behavior: 'smooth' });

            document.getElementById('dictado-res-original').innerText = originalText;
            document.getElementById('dictado-res-usuario').innerText = userText;

            const badge = document.getElementById('dictado-precision-badge');
            badge.innerText = `${precision}% Precisión`;
            
            if (precision >= 85) {
                badge.className = "text-xs font-extrabold px-3 py-1 rounded-full bg-emerald-100 text-emerald-800 dark:bg-emerald-900/50 dark:text-emerald-300";
            } else if (precision >= 50) {
                badge.className = "text-xs font-extrabold px-3 py-1 rounded-full bg-amber-100 text-amber-800 dark:bg-amber-900/50 dark:text-amber-300";
            } else {
                badge.className = "text-xs font-extrabold px-3 py-1 rounded-full bg-red-100 text-red-800 dark:bg-red-900/50 dark:text-red-300";
            }

            const retroBox = document.getElementById('dictado-retro-ia');
            retroBox.innerHTML = `<i class="fa-solid fa-spinner animate-spin mr-1"></i> Analizando errores con Inteligencia Artificial...`;

            const sysInstruction = "Actúas como un profesor experto en ortografía y gramática española. Revisa de forma súper breve los errores en el texto escrito por el alumno basándote en el original.";
            const queryText = `Original: "${originalText}"\nAlumno: "${userText}"`;

            try {
                const retro = await fetchGeminiAPI(sysInstruction, queryText);
                retroBox.innerHTML = formatMarkdown(retro);
            } catch (err) {
                console.error(err);
                retroBox.innerText = `Evaluación terminada. Nivel de precisión: ${precision}%. Intenta revisar la puntuación y acentuación.`;
            }
        }

        function pcmToWav(pcm16, sampleRate) {
            const buffer = new ArrayBuffer(44 + pcm16.length * 2);
            const view = new DataView(buffer);
            
            writeString(view, 0, 'RIFF');
            view.setUint32(4, 36 + pcm16.length * 2, true);
            writeString(view, 8, 'WAVE');
            writeString(view, 12, 'fmt ');
            view.setUint32(16, 16, true);
            view.setUint16(20, 1, true);
            view.setUint16(22, 1, true);
            view.setUint32(24, sampleRate, true);
            view.setUint32(28, sampleRate * 2, true);
            view.setUint16(32, 2, true);
            view.setUint16(34, 16, true);
            writeString(view, 36, 'data');
            view.setUint32(40, pcm16.length * 2, true);
            
            let offset = 44;
            for (let i = 0; i < pcm16.length; i++, offset += 2) {
                view.setInt16(offset, pcm16[i], true);
            }
            
            return new Blob([buffer], { type: 'audio/wav' });
        }

        function writeString(view, offset, string) {
            for (let i = 0; i < string.length; i++) {
                view.setUint8(offset + i, string.charCodeAt(i));
            }
        }

        function base64ToArrayBuffer(base64) {
            const binaryString = window.atob(base64);
            const len = binaryString.length;
            const bytes = new Uint8Array(len);
            for (let i = 0; i < len; i++) {
                bytes[i] = binaryString.charCodeAt(i);
            }
            return bytes.buffer;
        }
    </script>
</body>
</html>
