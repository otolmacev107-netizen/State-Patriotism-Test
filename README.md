# State-Patriotism-Test
You must pass this test to be assessed by the supervisor and then... You'll find out more.
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ГосТест — проверка лояльности гражданина</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0b1c33 0%, #1a3a5c 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .site-container {
            width: 100%;
            max-width: 1200px;
            margin: 20px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            position: relative;
        }

        .gos-header {
            background: #1f3a6b;
            color: white;
            padding: 15px 30px;
            border-bottom: 3px solid #ffd700;
        }

        .header-content {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .gerb {
            width: 50px;
            height: 50px;
            background: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #1f3a6b;
            font-weight: bold;
            font-size: 24px;
        }

        .gos-header h1 {
            font-size: 28px;
            font-weight: 600;
            letter-spacing: 1px;
            flex-grow: 1;
        }

        .user-placeholder {
            background: rgba(255,255,255,0.1);
            padding: 8px 15px;
            border-radius: 30px;
            font-size: 14px;
            border: 1px solid rgba(255,215,0,0.5);
        }

        .test-main {
            padding: 30px;
            position: relative;
            min-height: 500px;
        }

        .nadziratel-container {
            position: absolute;
            top: 20px;
            right: 30px;
            width: 150px;
            text-align: center;
            z-index: 10;
        }

        .nadziratel-face {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: radial-gradient(circle at 30% 30%, #fff5b0, #ffe070);
            margin: 0 auto 10px;
            position: relative;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            border: 3px solid #ffd700;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .nadziratel-face::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 33.3%;
            background: white;
            border-radius: 60px 60px 0 0;
            opacity: 0.3;
        }

        .nadziratel-face::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 33.3%;
            background: red;
            border-radius: 0 0 60px 60px;
            opacity: 0.3;
        }

        .eye-left, .eye-right {
            position: absolute;
            width: 15px;
            height: 15px;
            background: #1a3a5c;
            border-radius: 50%;
            top: 40px;
        }

        .eye-left { left: 30px; }
        .eye-right { right: 30px; }

        .mouth {
            position: absolute;
            width: 40px;
            height: 20px;
            background: transparent;
            bottom: 30px;
            left: 40px;
            border-bottom: 4px solid #1a3a5c;
            border-radius: 0 0 20px 20px;
            transition: all 0.2s;
        }

        .mouth.happy { border-bottom: 4px solid #1a3a5c; }
        .mouth.neutral { border-bottom: 2px solid #1a3a5c; width: 30px; left: 45px; }
        .mouth.angry { border-bottom: 4px solid red; border-radius: 0; transform: rotate(5deg); }
        .mouth.dead { border-bottom: none; background: #333; height: 2px; width: 30px; }

        .nadziratel-name {
            font-size: 11px;
            color: #666;
            background: #f5f5f5;
            padding: 5px;
            border-radius: 20px;
        }

        .progress-section {
            margin: 20px 0;
            max-width: 70%;
        }

        .progress-text {
            font-size: 14px;
            color: #1f3a6b;
            margin-bottom: 5px;
        }

        .progress-bar {
            height: 10px;
            background: #e0e0e0;
            border-radius: 10px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #1f3a6b, #ffd700);
            width: 0%;
            transition: width 0.3s;
        }

        .question-block {
            background: #f8faff;
            border-radius: 20px;
            padding: 30px;
            margin-right: 180px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            border: 1px solid #d4e0f0;
        }

        .question-text {
            font-size: 24px;
            font-weight: 600;
            color: #1f3a6b;
            margin-bottom: 30px;
            line-height: 1.4;
        }

        .answers-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .answer-btn {
            background: white;
            border: 2px solid #d4e0f0;
            border-radius: 50px;
            padding: 15px 25px;
            font-size: 16px;
            text-align: left;
            cursor: pointer;
            transition: all 0.2s;
            color: #1f3a6b;
            font-weight: 500;
        }

        .answer-btn:hover {
            background: #e5eeff;
            border-color: #1f3a6b;
            transform: translateX(5px);
        }

        .answer-btn.selected {
            background: #1f3a6b;
            color: white;
            border-color: #ffd700;
        }

        .roskomnadzor-ticker {
            margin-top: 40px;
            background: #000;
            color: #ffd700;
            padding: 8px;
            font-size: 12px;
            border-radius: 5px;
            opacity: 0.8;
        }

        .roskomnadzor-ticker marquee {
            color: #ffd700;
        }

        .gos-footer {
            background: #f0f4fa;
            padding: 20px 30px;
            font-size: 13px;
            color: #666;
            text-align: center;
            border-top: 1px solid #d4e0f0;
        }

        .footer-links a {
            color: #1f3a6b;
            text-decoration: none;
            margin: 0 10px;
        }

        .footer-links a:hover {
            text-decoration: underline;
        }

        .easter-egg-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            z-index: 9999;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            color: white;
        }

        .easter-content {
            max-width: 800px;
            padding: 40px;
            font-family: 'Courier New', monospace;
            font-size: 20px;
            line-height: 2;
            text-align: center;
            white-space: pre-wrap;
            color: #ffd700;
        }

        .easter-close {
            padding: 10px 30px;
            background: #ffd700;
            border: none;
            border-radius: 30px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 20px;
            color: #1f3a6b;
            font-weight: bold;
        }

        .ending-block {
            text-align: center;
            padding: 60px 40px;
            background: #f8faff;
            border-radius: 20px;
            margin-right: 180px;
        }

        .ending-text {
            font-size: 18px;
            line-height: 1.8;
            color: #1f3a6b;
            white-space: pre-wrap;
            margin-bottom: 30px;
            font-family: 'Courier New', monospace;
        }

        .restart-button {
            background: #1f3a6b;
            color: white;
            border: none;
            border-radius: 50px;
            padding: 15px 40px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .restart-button:hover {
            background: #ffd700;
            color: #1f3a6b;
        }

        @media (max-width: 900px) {
            .nadziratel-container {
                position: static;
                margin-bottom: 20px;
            }
            .question-block, .ending-block {
                margin-right: 0;
            }
            .progress-section {
                max-width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="site-container">
        <header class="gos-header">
            <div class="header-content">
                <div class="gerb">🇷🇺</div>
                <h1>ГосТест</h1>
                <div class="user-placeholder">Гражданин РФ</div>
            </div>
        </header>

        <main class="test-main">
            <div class="nadziratel-container" id="nadziratel">
                <div class="nadziratel-face" id="nadziratel-face">
                    <div class="eye-left"></div>
                    <div class="eye-right"></div>
                    <div class="mouth" id="mouth"></div>
                </div>
                <div class="nadziratel-name">Ваш персональный друг и наставник</div>
            </div>

            <div class="progress-section">
                <div class="progress-text">Вопрос <span id="current-question-num">1</span> из <span id="total-questions">111</span></div>
                <div class="progress-bar">
                    <div class="progress-fill" id="progress-fill" style="width: 0.9%;"></div>
                </div>
            </div>

            <div class="question-block" id="question-block">
                <div class="question-text" id="question-text">Загрузка вопроса...</div>
                <div class="answers-list" id="answers-list"></div>
            </div>

            <div class="easter-egg-overlay" id="easter-egg" style="display: none;">
                <div class="easter-content" id="easter-content"></div>
                <button class="easter-close" id="easter-close" style="display: none;">Продолжить</button>
            </div>

            <div class="ending-block" id="ending-block" style="display: none;">
                <div class="ending-text" id="ending-text"></div>
                <button class="restart-button" id="restart-btn">Пройти тест заново</button>
            </div>

            <div class="roskomnadzor-ticker">
                <marquee behavior="scroll" direction="left">Данный тест одобрен Роскомнадзором. Все вопросы согласованы с Министерством Правды. Любое несовпадение с официальной позицией является глюком вашего восприятия. Пожалуйста, перезагрузите патриотизм.</marquee>
            </div>
        </main>

        <footer class="gos-footer">
            <div class="footer-links">
                <a href="#">Обратная связь</a> | 
                <a href="#">Политика конфиденциальности</a> | 
                <a href="#">Сообщить о ошибке</a>
            </div>
            <div class="copyright">© 2025, Министерство Цифрового Развития РФ</div>
        </footer>
    </div>

    <script>
        (function() {
            // ==================== ВСЕ 111 ВОПРОСОВ ====================
            const questions = [
                // 1
                {
                    text: "Как вы относитесь к тому, что Роскомнадзор призвал прожить день без Wi-Fi?",
                    answers: [
                        { text: "Поддерживаю, полезно отдохнуть от сети", loy: 2, par: 0, hum: 0, str: 0, svg: 0 },
                        { text: "Ну, день без интернета — это романтично", loy: 0, par: 1, hum: 0, str: 0, svg: 0 },
                        { text: "Вы издеваетесь? У меня работа в онлайне", loy: -1, par: 2, hum: -1, str: 0, svg: 0 },
                        { text: "Отключить Wi-Fi — не значит потерять связь? Потерял связь с реальностью", loy: -3, par: 3, hum: 2, str: 1, svg: 0 }
                    ]
                },
                // 2
                {
                    text: "Ваше мнение о блокировке Telegram?",
                    answers: [
                        { text: "Правильно, вражеский мессенджер", loy: 2, par: -1, hum: -1, str: 0, svg: 0 },
                        { text: "Пользуюсь через VPN, но молчу", loy: -1, par: 3, hum: 1, str: 2, svg: 1 },
                        { text: "Достойной альтернативы нет до сих пор", loy: -2, par: 1, hum: 0, str: 0, svg: 0 },
                        { text: "На развитие Telegram потратили миллиарды, чтобы потом заблокировать?", loy: -3, par: 2, hum: 3, str: 0, svg: 2 }
                    ]
                },
                // 3
                {
                    text: "Что такое «ТСПУ»?",
                    answers: [
                        { text: "Технические средства противодействия угрозам", loy: 2, par: -1, hum: -1, str: 0, svg: 0 },
                        { text: "Что-то военное", loy: 0, par: 0, hum: 0, str: 0, svg: 0 },
                        { text: "То, из-за чего у меня падает ютуб", loy: -2, par: 2, hum: 1, str: 1, svg: 0 },
                        { text: "Оно сломалось, операторы пускают трафик мимо", loy: -3, par: 3, hum: 2, str: 0, svg: 1 }
                    ]
                },
                // 4
                {
                    text: "Вы пользуетесь VPN?",
                    answers: [
                        { text: "Нет, мне нечего скрывать", loy: 2, par: -2, hum: -1, str: 0, svg: 0 },
                        { text: "Только для работы", loy: 0, par: 1, hum: 0, str: 1, svg: 0 },
                        { text: "Да, чтобы заходить в инстаграм", loy: -2, par: 2, hum: 0, str: 1, svg: 1 },
                        { text: "У меня свой VPN на роутере, попробуйте заблокировать", loy: -3, par: 3, hum: 3, str: 2, svg: 2 }
                    ]
                },
                // 5
                {
                    text: "Как вы относитесь к замедлению YouTube?",
                    answers: [
                        { text: "Нормально, есть VK Видео", loy: 2, par: 0, hum: -1, str: 0, svg: 0 },
                        { text: "Грузится, но смотреть можно", loy: 0, par: 1, hum: 0, str: 0, svg: 0 },
                        { text: "Я плачу за интернет, а не за буфер", loy: -2, par: 2, hum: 1, str: 1, svg: 0 },
                        { text: "Это подобно сдаче городов врагу", loy: -3, par: 3, hum: 2, str: 2, svg: 1 }
                    ]
                },
                // 6
                {
                    text: "Вы знаете, что такое «Единый реестр запрещенной информации»?",
                    answers: [
                        { text: "Наш щит от фейков", loy: 2, par: -1, hum: -1, str: 0, svg: 0 },
                        { text: "Список плохих сайтов", loy: 1, par: 0, hum: 0, str: 0, svg: 0 },
                        { text: "Туда попадает всё, что движется", loy: -2, par: 2, hum: 1, str: 0, svg: 0 },
                        { text: "Там уже пол-интернета, скоро и этот тест туда отправят", loy: -3, par: 3, hum: 3, str: 1, svg: 1 }
                    ]
                },
                // 7
                {
                    text: "Ваше отношение к тому, что РКН блокирует мемы?",
                    answers: [
                        { text: "Мемы должны быть патриотичными", loy: 2, par: 0, hum: -2, str: 0, svg: 0 },
                        { text: "Зависит от мема", loy: 0, par: 0, hum: 0, str: 0, svg: 0 },
                        { text: "Запретили фотожабы на Сюткина? Серьёзно?", loy: -2, par: 1, hum: 2, str: 0, svg: 1 },
                        { text: "А что если я скажу тебе, что ты фейк?", loy: -3, par: 2, hum: 3, str: 1, svg: 1 }
                    ]
                },
                // 8
                {
                    text: "Вы пользуетесь пиратскими сайтами?",
                    answers: [
                        { text: "Нет, я за авторские права", loy: 2, par: -1, hum: -1, str: 0, svg: 0 },
                        { text: "Иногда смотрю фильмы", loy: -1, par: 1, hum: 0, str: 0, svg: 0 },
                        { text: "А где их смотреть, если всё платное?", loy: -2, par: 1, hum: 1, str: 0, svg: 0 },
                        { text: "Заблокировали пиратские копии — теперь я без мультиков", loy: -3, par: 2, hum: 2, str: 1, svg: 0 }
                    ]
                },
                // 9
                {
                    text: "Что вы делаете, когда сайт заблокирован?",
                    answers: [
                        { text: "Иду на госуслуги", loy: 2, par: -1, hum: -1, str: 0, svg: 0 },
                        { text: "Ищу зеркало", loy: -1, par: 2, hum: 0, str: 1, svg: 0 },
                        { text: "Матерю Роскомнадзор", loy: -2, par: 2, hum: 2, str: 0, svg: 0 },
                        { text: "Звоню другу в ФСБ, чтобы разблокировали", loy: -3, par: 3, hum: 3, str: 2, svg: 1 }
                    ]
                },
                // 10
                {
                    text: "Вы замечали, что интернет отключают в регионах?",
                    answers: [
                        { text: "Это для нашей безопасности", loy: 2, par: 0, hum: -1, str: 0, svg: 0 },
                        { text: "Иногда пропадает связь", loy: 0, par: 1, hum: 0, str: 1, svg: 0 },
                        { text: "Я живу в Москве, у меня всё работает", loy: -1, par: 1, hum: 1, str: 0, svg: 0 },
                        { text: "Массовые отключения доставляют серьёзные неудобства", loy: -3, par: 2, hum: 0, str: 2, svg: 0 }
                    ]
                },
                // 11
                {
                    text: "Мем «ББПЕ» с лицом Валерия Сюткина — это?",
                    answers: [
                        { text: "Не знаю такого", loy: 2, par: 0, hum: -1, str: 0, svg: 0 },
                        { text: "Видел, но не понимаю", loy: 0, par: 1, hum: 0, str: 0, svg: 0 },
                        { text: "Классика, расшифровать цензурно невозможно", loy: -2, par: 1, hum: 2, str: 0, svg: 1 },
                        { text: "Сюткин подал в суд? А я и не знал", loy: -3, par: 2, hum: 2, str: 1, svg: 1 }
                    ]
                },
                // 12
                {
                    text: "Как вы относитесь к «Абсурдопедии»?",
                    answers: [
                        { text: "Сайт с опасной информацией", loy: 2, par: 0, hum: -1, str: 0, svg: 0 },
                        { text: "Просто википедия-пародия", loy: 0, par: 0, hum: 0, str: 0, svg: 0 },
                        { text: "Там смешно пишут про политику", loy: -2, par: 1, hum: 2, str: 0, svg: 1 },
                        { text: "Там статья про Путина — теперь я знаю, меня заблокируют", loy: -3, par: 3, hum: 2, str: 2, svg: 1 }
                    ]
                },
                // 13
                {
                    text: "Мем про цыган из фильма «Большой куш»?",
                    answers: [
                        { text: "Не помню такого", loy: 2, par: 0, hum: -1, str: 0, svg: 0 },
                        { text: "Забавный фильм", loy: 0, par: 0, hum: 1, str: 0, svg: 0 },
                        { text: "«Два пистолета, четыре ствола...»", loy: -1, par: 1, hum: 2, str: 0, svg: 0 },
                        { text: "Останкинский суд запретил. Всё, теперь это экстремизм", loy: -3, par: 2, hum: 3, str: 1, svg: 1 }
                    ]
         
