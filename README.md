<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🔒 VIP Member Portal - Private Live Access</title>
    <style>
        /* Premium Dark & Hot-Pink Theme */
        :root {
            --primary: #ff0055;
            --primary-hover: #e6004c;
            --secondary: #1e293b;
            --dark: #090d16;
            --glass: rgba(255, 255, 255, 0.06);
            --border: rgba(255, 255, 255, 0.1);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--dark);
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            color: #ffffff;
            padding-bottom: 80px;
        }

        /* Top Header */
        .header {
            text-align: center;
            padding: 40px 20px 25px;
            background: linear-gradient(to bottom, rgba(255, 0, 85, 0.2), transparent);
            border-bottom: 1px solid rgba(255, 0, 85, 0.1);
        }

        .profile-container {
            position: relative;
            width: 110px;
            height: 110px;
            margin: 0 auto 15px;
        }

        .profile-img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 3px solid var(--primary);
            object-fit: cover;
            box-shadow: 0 0 25px rgba(255, 0, 85, 0.6);
        }

        .online-badge {
            position: absolute;
            bottom: 5px;
            right: 5px;
            background: #22c55e;
            color: white;
            padding: 3px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: bold;
            border: 2px solid var(--dark);
            animation: blink 1.5s infinite;
        }

        @keyframes blink {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        h1 { font-size: 26px; font-weight: 800; margin-bottom: 8px; letter-spacing: -0.5px; }
        .sub-text { color: #94a3b8; font-size: 14px; max-width: 450px; margin: 0 auto; line-height: 1.5; }

        /* Real-time Interactive Inbox Box Section */
        .inbox-wrapper {
            max-width: 500px;
            margin: 25px auto;
            padding: 0 20px;
        }

        .inbox-card {
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .inbox-title {
            font-size: 15px;
            font-weight: 700;
            color: #f1f5f9;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .inbox-p {
            font-size: 13px;
            color: #94a3b8;
            margin-bottom: 15px;
            line-height: 1.5;
        }

        .input-group {
            display: flex;
            gap: 8px;
            background: rgba(0,0,0,0.3);
            padding: 6px;
            border-radius: 30px;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .input-group input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 10px 15px;
            color: white;
            font-size: 14px;
            outline: none;
        }

        .input-group input::placeholder { color: #64748b; }

        .submit-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 10px 22px;
            border-radius: 25px;
            font-weight: bold;
            font-size: 13px;
            cursor: pointer;
            transition: background 0.2s;
        }

        .submit-btn:hover { background: var(--primary-hover); }

        .status-msg {
            margin-top: 15px;
            padding: 12px;
            border-radius: 12px;
            font-size: 13.5px;
            line-height: 1.5;
            display: none;
            text-align: center;
        }

        /* Block-Level Link Buttons */
        .cta-container {
            max-width: 500px;
            margin: 20px auto;
            padding: 0 20px;
        }

        .main-link-btn {
            display: block !important;
            width: 100% !important;
            box-sizing: border-box !important;
            background: linear-gradient(135deg, #ff0055 0%, #ff4d6d 100%) !important;
            color: #ffffff !important;
            text-decoration: none !important;
            text-align: center !important;
            padding: 18px 20px !important;
            border-radius: 50px !important;
            font-size: 16px !important;
            font-weight: 800 !important;
            letter-spacing: 0.5px !important;
            box-shadow: 0 8px 25px rgba(255, 0, 85, 0.4) !important;
            transition: transform 0.2s, opacity 0.2s !important;
            margin: 15px 0 !important;
            cursor: pointer;
        }

        .main-link-btn:hover {
            transform: translateY(-1px);
            opacity: 0.95;
        }

        /* 👑 VIP INTERACTIVE LIVE CHAT WIDGET 👑 */
        .floating-chat {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 340px;
            background: rgba(11, 17, 30, 0.98);
            backdrop-filter: blur(12px);
            border: 1px solid var(--primary);
            border-radius: 16px;
            box-shadow: 0 15px 40px rgba(255, 0, 85, 0.4);
            z-index: 9999;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .f-chat-header {
            background: #111827;
            padding: 12px 14px;
            font-size: 13px;
            font-weight: bold;
            color: #ffffff;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        .f-live-indicator {
            color: #ef4444;
            display: flex;
            align-items: center;
            gap: 6px;
            text-transform: uppercase;
            font-size: 12px;
            letter-spacing: 0.5px;
        }

        .f-live-indicator::before {
            content: '';
            display: inline-block;
            width: 8px;
            height: 8px;
            background: #ef4444;
            border-radius: 50%;
            animation: pulse-dot 1.5s infinite;
        }

        .f-chat-feed {
            height: 200px;
            overflow-y: auto;
            padding: 12px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            scroll-behavior: smooth;
        }

        .f-chat-feed::-webkit-scrollbar { width: 4px; }
        .f-chat-feed::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.2); border-radius: 4px; }

        .f-msg {
            font-size: 13px;
            line-height: 1.4;
            animation: slideUpMsg 0.3s ease-out forwards;
            word-wrap: break-word;
        }

        .f-user { font-weight: bold; margin-right: 4px; }
        .f-text { color: #e2e8f0; }

        /* Host Message Styling */
        .host-msg {
            background: rgba(255, 0, 85, 0.15);
            border-left: 3px solid var(--primary);
            padding: 8px 10px;
            border-radius: 0 8px 8px 0;
            margin: 4px 0;
        }
        .host-name { color: #ff0055; font-weight: 900; }
        .host-badge {
            background: #ff0055; color: white;
            font-size: 9px; padding: 2px 5px; border-radius: 4px;
            margin-left: 4px; vertical-align: middle;
        }

        /* User (Traffic) Message Styling */
        .my-msg {
            text-align: right;
            background: rgba(255, 255, 255, 0.08);
            padding: 8px 12px;
            border-radius: 12px 12px 0 12px;
            align-self: flex-end;
            max-width: 85%;
            color: #fff;
            margin: 4px 0;
        }

        .c-1 { color: #38bdf8; } .c-2 { color: #a78bfa; } .c-3 { color: #34d399; } .c-4 { color: #fbbf24; } .c-5 { color: #f472b6; }

        .f-chat-input-area {
            display: flex;
            padding: 10px;
            background: rgba(0,0,0,0.4);
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        .f-chat-input {
            flex: 1;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            color: white;
            padding: 10px 12px;
            border-radius: 20px;
            font-size: 13px;
            outline: none;
        }
        .f-chat-input::placeholder { color: #64748b; }

        .f-chat-send {
            background: var(--primary);
            border: none;
            color: white;
            width: 38px;
            height: 38px;
            border-radius: 50%;
            margin-left: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: 0.2s;
        }
        .f-chat-send:hover { transform: scale(1.1); background: var(--primary-hover); }

        .typing-indicator {
            font-size: 11px;
            color: #94a3b8;
            font-style: italic;
            padding: 0 12px 5px;
            display: none;
        }

        @keyframes slideUpMsg {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes pulse-dot {
            0% { transform: scale(0.9); opacity: 1; }
            50% { transform: scale(1.2); opacity: 0.4; }
            100% { transform: scale(0.9); opacity: 1; }
        }

        /* Gallery Grid Layout */
        .gallery-heading {
            max-width: 1000px;
            margin: 40px auto 15px;
            padding: 0 20px;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #64748b;
        }

        .gallery-container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 0 20px;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 15px;
        }

        .video-card {
            background: var(--glass);
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid var(--border);
            transition: transform 0.3s, border-color 0.3s;
            color: white;
            position: relative;
            display: block;
            cursor: pointer;
        }

        .video-card:hover {
            transform: scale(1.04);
            border-color: var(--primary);
        }

        .thumbnail {
            width: 100%;
            aspect-ratio: 9/16;
            background: #111827;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .thumb-img {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            object-fit: cover; opacity: 0.7; 
        }

        .play-btn {
            position: absolute;
            background: var(--primary);
            width: 46px; height: 46px;
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            box-shadow: 0 4px 15px rgba(255, 0, 85, 0.5);
            z-index: 2;
        }

        .play-triangle {
            width: 0; height: 0;
            border-top: 9px solid transparent;
            border-left: 15px solid white;
            border-bottom: 9px solid transparent;
            margin-left: 5px;
        }

        .video-info {
            padding: 10px; font-size: 12px; text-align: center;
            background: rgba(0, 0, 0, 0.75); font-weight: 600;
            position: relative; z-index: 2; border-top: 1px solid rgba(255,255,255,0.05);
        }

        /* 🚨 ANTI-ESCAPE MODAL STYLES 🚨 */
        .escape-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(9, 13, 22, 0.96);
            backdrop-filter: blur(8px);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 99999;
            padding: 20px;
        }

        .escape-box {
            background: #111827;
            border: 3px solid #ff0055;
            border-radius: 24px;
            max-width: 440px;
            width: 100%;
            padding: 35px 25px;
            text-align: center;
            position: relative;
            box-shadow: 0 20px 50px rgba(255, 0, 85, 0.4);
            animation: popIn 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        @keyframes popIn {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .siren-icon {
            width: 65px;
            margin-bottom: 15px;
            animation: rotateSiren 0.8s ease-in-out infinite alternate;
        }

        @keyframes rotateSiren {
            from { transform: rotate(-10deg); }
            to { transform: rotate(10deg); }
        }

        .escape-headline {
            font-size: 26px;
            font-weight: 900;
            color: #ff0055;
            margin-bottom: 15px;
            letter-spacing: 0.5px;
            text-transform: uppercase;
        }

        .escape-body {
            font-size: 14.5px;
            color: #cbd5e1;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .escape-body span {
            background: #ff0055;
            color: #ffffff;
            padding: 1px 5px;
            border-radius: 4px;
            font-weight: bold;
        }

        .escape-warning {
            color: #facc15;
            font-size: 14px;
            font-weight: bold;
            margin-bottom: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        .timer-container {
            border: 2px dashed rgba(255, 0, 85, 0.4);
            border-radius: 12px;
            padding: 12px;
            margin-bottom: 25px;
            background: rgba(255, 0, 85, 0.03);
        }

        .timer-title {
            font-size: 13px;
            color: #ffffff;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .timer-clock {
            font-size: 22px;
            font-weight: 800;
            color: #ff0055;
            letter-spacing: 1px;
        }

        /* Loading Overlay Style */
        #loadingOverlay {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #090d16; z-index: 999999; align-items: center; justify-content: center;
            flex-direction: column;
        }

        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        @media (max-width: 480px) {
            .gallery-container { grid-template-columns: repeat(2, 1fr); gap: 10px; }
            h1 { font-size: 22px; }
            .floating-chat {
                width: 100%;
                bottom: 0; right: 0;
                border-radius: 16px 16px 0 0;
            }
        }
    </style>
</head>
<body>

    <div class="header">
        <div class="profile-container">
            <img src="https://github.com/mizan000321-ops/newv/blob/main/G3UZgO_XMAAzE6N.jpg?raw=true" alt="Live Host" class="profile-img">
            <span class="online-badge">LIVE NOW</span>
        </div>
        <h1>Connect with Me Live 🎥</h1>
        <p class="sub-text">Hey darling! I am waiting inside my private room. Click below to quickly pass the secure network check and unlock my official 1-on-1 live video stream instantly! 💋</p>
    </div>

    <div class="floating-chat" id="chatWidget">
        <div class="f-chat-header">
            <span class="f-live-indicator">Live Broadcast</span>
            <span style="color: #64748b;"><span id="onlineCount">1,245</span> online</span>
        </div>
        
        <div class="f-chat-feed" id="widgetFeed">
            </div>
        
        <div class="typing-indicator" id="typingIndicator">Host is typing...</div>

        <div class="f-chat-input-area">
            <input type="text" id="userChatInput" class="f-chat-input" placeholder="Say hi to host..." onkeypress="handleEnter(event)">
            <button class="f-chat-send" onclick="sendUserMessage()">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></svg>
            </button>
        </div>
    </div>

    <div class="gallery-heading">📸 My Private Album Preview (18 Clips):</div>
    
    <div class="gallery-container">
        <script>
            const images = [
                "G3UZgO_XMAAzE6N.jpg", "GoWoZl9X0AA1I6V.jpg", "Gv2LKn_XwAAsWou.jpg", 
                "HAwdaxsW0AA1AU1.jpg", "HBuOij0WoAAfrI3.jpg", "HE7LupIXEAA2xnS.jpg", 
                "HG2xUfkX0AAZEu5.jpg", "HGTqY9UX0AAUZlR.jpg", "HGwpfY6XwAAYJZl.jpg", 
                "HHN_VvQXsAAyPas.jpg", "HIdka0EWIAAYMTj.jpg"
            ];
            for (let i = 1; i <= 18; i++) {
                let src = i <= 11 
                    ? `https://github.com/mizan000321-ops/newv/blob/main/${images[i-1]}?raw=true`
                    : `https://drive.google.com/thumbnail?id=` + [
                        "1vRivbiFDOWdoBdV61
