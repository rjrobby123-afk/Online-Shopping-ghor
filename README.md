# Online-Shopping-ghor
আমাদের থেকে পণ‍্য কিনলে আপনি 100℅ বিশ্বস্ত পণ‍্য পাবেন এবং প্রতি মাসে যে ক্রেতা সর্বোচ্চ টাকার পণ্য কেনে তাকে 2 লাখ টাকা পুরষ্কার দেওয়া হয়। তাই আমাদের সাথে থাকুন এবং বেশি বেশি পণ‍্য ক্রয় করুন।
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Digital Store - Clothing & Media Store</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f8f9fa;
            color: #333;
            line-height: 1.6;
        }

        /* Header */
        header {
            background-color: #1e293b;
            color: #ffffff;
            padding: 20px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        header h1 {
            font-size: 22px;
        }

        .admin-toggle-btn {
            background-color: #f59e0b;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            font-size: 14px;
        }

        .admin-toggle-btn:hover {
            background-color: #d97706;
        }

        .admin-logout-btn {
            background-color: #dc2626;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            font-size: 14px;
            display: none;
        }

        .admin-logout-btn:hover {
            background-color: #b91c1c;
        }

        /* Container */
        .container {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
        }

        /* Admin Panel */
        .admin-panel {
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.08);
            margin-bottom: 30px;
            display: none;
        }

        .admin-panel h3 {
            margin-bottom: 15px;
            color: #1e293b;
            border-bottom: 2px solid #e2e8f0;
            padding-bottom: 8px;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-size: 14px;
            font-weight: 600;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #cbd5e1;
            border-radius: 5px;
            font-size: 14px;
        }

        .btn-save {
            background-color: #16a34a;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        .btn-save:hover {
            background-color: #15803d;
        }

        /* Orders Table */
        .orders-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            font-size: 14px;
        }

        .orders-table th,
        .orders-table td {
            border: 1px solid #cbd5e1;
            padding: 10px;
            text-align: left;
        }

        .orders-table th {
            background-color: #f1f5f9;
        }

        .btn-approve {
            background-color: #16a34a;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            margin-right: 5px;
        }

        .btn-reject {
            background-color: #dc2626;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
        }

        /* Tabs */
        .tabs {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .tab-btn {
            background-color: #e2e8f0;
            border: none;
            padding: 10px 18px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 15px;
            font-weight: 600;
            transition: 0.3s;
        }

        .tab-btn.active,
        .tab-btn:hover {
            background-color: #0284c7;
            color: white;
        }

        /* Grid */
        .item-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
        }

        .item-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .item-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(0, 0, 0, 0.75);
            color: white;
            padding: 4px 10px;
            border-radius: 5px;
            font-size: 12px;
            text-transform: uppercase;
            z-index: 2;
        }

        .media-preview {
            background-color: #000;
            height: 180px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            position: relative;
        }

        .media-preview video,
        .media-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .sample-tag {
            position: absolute;
            bottom: 10px;
            left: 10px;
            background: rgba(239, 68, 68, 0.9);
            color: white;
            padding: 2px 8px;
            font-size: 11px;
            border-radius: 4px;
            font-weight: bold;
        }

        .item-info {
            padding: 20px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .item-title {
            font-size: 18px;
            margin-bottom: 8px;
            color: #1e293b;
        }

        .item-desc {
            font-size: 14px;
            color: #64748b;
            margin-bottom: 12px;
        }

        .price {
            font-size: 18px;
            font-weight: bold;
            color: #e11d48;
        }

        /* Reactions */
        .reactions-bar {
            display: flex;
            gap: 15px;
            margin: 12px 0;
            border-top: 1px solid #e2e8f0;
            border-bottom: 1px solid #e2e8f0;
            padding: 8px 0;
        }

        .react-btn {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            color: #64748b;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: 0.2s;
        }

        .react-btn:hover {
            color: #0284c7;
        }

        /* Reviews */
        .reviews-section {
            margin-top: 12px;
            background: #f8fafc;
            padding: 10px;
            border-radius: 6px;
            font-size: 13px;
        }

        .review-list {
            max-height: 100px;
            overflow-y: auto;
            margin-bottom: 8px;
        }

        .review-item {
            background: white;
            padding: 5px 8px;
            border-radius: 4px;
            margin-bottom: 5px;
            border-left: 3px solid #0284c7;
        }

        .review-form input {
            width: 100%;
            padding: 5px 8px;
            font-size: 12px;
            border: 1px solid #cbd5e1;
            border-radius: 4px;
            margin-bottom: 5px;
        }

        .review-form button {
            background-color: #0284c7;
            color: white;
            border: none;
            padding: 4px 10px;
            border-radius: 4px;
            font-size: 12px;
            cursor: pointer;
            font-weight: bold;
        }

        .btn-action {
            background-color: #0284c7;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            width: 100%;
            margin-top: 12px;
            font-size: 14px;
        }

        .btn-action.unlocked {
            background-color: #16a34a;
        }

        .btn-action.pending {
            background-color: #d97706;
            cursor: not-allowed;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.65);
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 15px;
        }

        .modal-content {
            background: white;
            width: 100%;
            max-width: 480px;
            padding: 28px;
            border-radius: 10px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
            position: relative;
        }

        .close-btn {
            position: absolute;
            top: 12px;
            right: 18px;
            font-size: 24px;
            cursor: pointer;
            color: #64748b;
        }

        .modal-title {
            font-size: 20px;
            margin-bottom: 15px;
            color: #1e293b;
        }

        .payment-instruction {
            background: #f1f5f9;
            padding: 15px;
            border-radius: 6px;
            font-size: 14px;
            margin-bottom: 15px;
            color: #334155;
            line-height: 1.6;
        }

        .highlight-number {
            color: #e11d48;
            font-weight: bold;
            font-size: 16px;
        }

        .security-note {
            background: #fef3c7;
            border-left: 4px solid #f59e0b;
            padding: 10px 12px;
            margin-bottom: 15px;
            font-size: 13px;
            color: #92400e;
            border-radius: 0 6px 6px 0;
        }

        .btn-submit {
            width: 100%;
            background-color: #0284c7;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            font-weight: bold;
        }

        .btn-submit:hover {
            background-color: #0369a1;
        }

        /* Admin Login Modal */
        .admin-login-box {
            text-align: center;
        }

        .admin-login-box input {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border: 1px solid #cbd5e1;
            border-radius: 5px;
            font-size: 15px;
            text-align: center;
        }

        .admin-login-box button {
            width: 100%;
            background-color: #1e293b;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            font-size: 15px;
            cursor: pointer;
            font-weight: bold;
        }

        footer {
            background-color: #1e293b;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 50px;
        }

        /* Admin only delete button inside admin panel */
        .admin-item-list {
            margin-top: 20px;
        }

        .admin-item-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border: 1px solid #e2e8f0;
            border-radius: 6px;
            margin-bottom: 8px;
            background: #f8fafc;
        }

        .admin-item-row button {
            background-color: #dc2626;
            color: white;
            border: none;
            padding: 5px 12px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 13px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <!-- Header -->
    <header>
        <h1>My Digital & Clothing Store</h1>
        <div>
            <button class="admin-toggle-btn" id="adminToggleBtn" onclick="requestAdminAccess()">⚙️ Admin Panel</button>
            <button class="admin-logout-btn" id="adminLogoutBtn" onclick="logoutAdmin()">Logout</button>
        </div>
    </header>

    <div class="container">

        <!-- Admin Panel (Password Protected) -->
        <div class="admin-panel" id="adminPanel">
            <h3>নতুন পণ্য বা কন্টেন্ট যুক্ত করুন</h3>
            <form id="uploadForm" onsubmit="addNewItem(event)" style="margin-bottom: 30px;">
                <div class="form-grid">
                    <div class="form-group">
                        <label>কন্টেন্টের ধরণ (Category)</label>
                        <select id="itemCategory" onchange="toggleCategoryFields()" required>
                            <option value="video">ভিডিও (Video)</option>
                            <option value="book">বই / PDF (Book / PDF)</option>
                            <option value="photo">ছবি (Photo)</option>
                            <option value="clothing">পোশাক (Clothing)</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>শিরোনাম (Title)</label>
                        <input type="text" id="itemTitle" placeholder="যেমন: প্রিমিয়াম হুডি বা কোর্স" required>
                    </div>
                    <div class="form-group">
                        <label>মূল্য (Price in BDT)</label>
                        <input type="text" id="itemPrice" placeholder="যেমন: ৳ 750" required>
                    </div>
                    <div class="form-group">
                        <label>ছবির লিংক বা স্যাম্পল URL</label>
                        <input type="text" id="itemSampleUrl" placeholder="পণ্যের ছবির লিংক দিন" required>
                    </div>
                </div>

                <div class="form-group" id="clothingFields" style="display: none; margin-bottom: 15px;">
                    <label>সাইজ ও কালার অপশন (কমা দিয়ে আলাদা করুন)</label>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 5px;">
                        <input type="text" id="itemSizes" placeholder="সাইজ: S, M, L, XL, XXL">
                        <input type="text" id="itemColors" placeholder="কালার: Black, Blue, Red, White">
                    </div>
                </div>

                <div class="form-group" style="margin-bottom: 15px;">
                    <label>মূল ফাইল / ডেলিভারি লিংক (Full Content / Delivery Link)</label>
                    <input type="text" id="itemFullUrl" placeholder="এপ্রুভ হওয়ার পর ক্রেতা যে লিংক দেখতে পাবে" required>
                </div>
                <div class="form-group" style="margin-bottom: 15px;">
                    <label>বর্ণনা (Description)</label>
                    <textarea id="itemDesc" rows="2" placeholder="পণ্য সম্পর্কে বিস্তারিত লিখুন..." required></textarea>
                </div>
                <button type="submit" class="btn-save">💾 পণ্য পাবলিশ করুন</button>
            </form>

            <!-- Admin Product Management (Delete only here) -->
            <h3>পণ্য ব্যবস্থাপনা (শুধুমাত্র অ্যাডমিন)</h3>
            <div class="admin-item-list" id="adminItemList">
                <!-- Items for delete will appear here -->
            </div>

            <h3 style="margin-top: 30px;">গ্রাহকদের পেমেন্ট ও অর্ডার ভেরিফিকেশন (Pending Approvals)</h3>
            <div style="overflow-x: auto;">
                <table class="orders-table">
                    <thead>
                        <tr>
                            <th>গ্রাহক নাম্বার</th>
                            <th>মাধ্যম</th>
                            <th>TrxID</th>
                            <th>পণ্য / সাইজ-কালার</th>
                            <th>পদক্ষেপ</th>
                        </tr>
                    </thead>
                    <tbody id="ordersTableBody">
                        <!-- Pending orders will load here -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Filter Tabs -->
        <div class="tabs">
            <button class="tab-btn active" onclick="filterItems('all')">সকল পণ্য</button>
            <button class="tab-btn" onclick="filterItems('clothing')">পোশাক 👕</button>
            <button class="tab-btn" onclick="filterItems('video')">ভিডিও</button>
            <button class="tab-btn" onclick="filterItems('book')">বই / PDF</button>
            <button class="tab-btn" onclick="filterItems('photo')">ছবি</button>
        </div>

        <!-- Catalog Grid -->
        <div class="item-grid" id="itemGrid">
            <!-- Dynamic Items will load here -->
        </div>
    </div>

    <!-- Payment Modal -->
    <div class="modal" id="paymentModal">
        <div class="modal-content">
            <span class="close-btn" onclick="closePaymentModal()">&times;</span>
            <h3 class="modal-title" id="modalItemTitle">Checkout</h3>
            
            <div class="security-note">
                <strong>নিরাপত্তা নোটিশ:</strong> পেমেন্ট জমা দেওয়ার পর আপনার অর্ডার অ্যাডমিনের অনুমোদনের অপেক্ষায় থাকবে। অনুমোদন না হওয়া পর্যন্ত কোনো কন্টেন্ট বা পণ্য অ্যাক্সেস করা যাবে না।
            </div>

            <div class="payment-instruction">
                <strong>পেমেন্ট নির্দেশিকা:</strong><br>
                বিকাশ / নগদ / রকেট নাম্বার: <span class="highlight-number">01720859745</span> (Personal)<br>
                নির্ধারিত মূল্য: <span id="modalItemPrice" style="font-weight: bold; color: #e11d48;"></span><br>
                সিলেক্টেড সাইজ/কালার: <span id="modalSelectedOptions" style="font-weight: bold; color: #0284c7;"></span><br><br>
                এই নাম্বারে টাকা পাঠিয়ে আপনার ট্রানজেকশন আইডি এবং প্রেরক নাম্বার নিচে জমা দিন।
            </div>
            
            <form id="paymentForm" onsubmit="submitPaymentRequest(event)">
                <div class="form-group" style="margin-bottom: 12px;">
                    <label>পেমেন্ট মাধ্যম (Payment Method)</label>
                    <select id="paymentMethod" required>
                        <option value="bKash">bKash</option>
                        <option value="Nagad">Nagad</option>
                        <option value="Rocket">Rocket</option>
                    </select>
                </div>
                <div class="form-group" style="margin-bottom: 12px;">
                    <label>আপনার মোবাইল নাম্বার (Sender Number)</label>
                    <input type="text" id="senderNumber" placeholder="যেমন: 017XXXXXXXX" required>
                </div>
                <div class="form-group" style="margin-bottom: 15px;">
                    <label>ট্রানজেকশন আইডি (TrxID)</label>
                    <input type="text" id="trxId" placeholder="যেমন: 9H87G6F5D4" required>
                </div>
                <button type="submit" class="btn-submit">অর্ডার ও পেমেন্ট রিকোয়েস্ট জমা দিন</button>
            </form>
        </div>
    </div>

    <!-- Admin Login Modal -->
    <div class="modal" id="adminLoginModal">
        <div class="modal-content admin-login-box">
            <span class="close-btn" onclick="closeAdminLogin()">&times;</span>
            <h3 class="modal-title">অ্যাডমিন লগইন</h3>
            <p style="font-size: 14px; color: #64748b; margin-bottom: 10px;">শুধুমাত্র অনুমোদিত অ্যাডমিন প্রবেশ করতে পারবেন</p>
            <input type="password" id="adminPassword" placeholder="পাসওয়ার্ড লিখুন" autocomplete="off">
            <button onclick="verifyAdminPassword()">প্রবেশ করুন</button>
            <p id="loginError" style="color: #dc2626; font-size: 13px; margin-top: 10px; display: none;">ভুল পাসওয়ার্ড। আবার চেষ্টা করুন।</p>
            <p style="margin-top: 15px; font-size: 13px;">
                <a href="javascript:void(0)" onclick="showForgotPassword()" style="color: #0284c7; text-decoration: none; font-weight: 600;">পাসওয়ার্ড ভুলে গেছেন?</a>
            </p>
        </div>
    </div>

    <!-- Forgot Password / Recovery Modal -->
    <div class="modal" id="forgotPasswordModal">
        <div class="modal-content admin-login-box">
            <span class="close-btn" onclick="closeForgotPassword()">&times;</span>
            <h3 class="modal-title">পাসওয়ার্ড রিকভারি</h3>
            <p style="font-size: 13px; color: #64748b; margin-bottom: 12px; line-height: 1.5;">
                পাসওয়ার্ড ভুলে গেলে নিচের রিকভারি কোডটি ব্যবহার করুন।<br>
                (নোট: প্রকৃত ইমেইল পাঠানো এই সিস্টেমে সম্ভব নয়। কোডটি পূর্বনির্ধারিত।)
            </p>
            
            <div id="recoveryStep1">
                <input type="text" id="recoveryCodeInput" placeholder="রিকভারি কোড লিখুন (৬ সংখ্যা)" maxlength="6" autocomplete="off">
                <button onclick="verifyRecoveryCode()">কোড যাচাই করুন</button>
                <p id="recoveryError" style="color: #dc2626; font-size: 13px; margin-top: 10px; display: none;">ভুল রিকভারি কোড।</p>
            </div>

            <div id="recoveryStep2" style="display: none;">
                <p style="font-size: 14px; color: #16a34a; margin-bottom: 10px;">✓ কোড সঠিক। এখন নতুন পাসওয়ার্ড সেট করুন।</p>
                <input type="password" id="newPasswordInput" placeholder="নতুন পাসওয়ার্ড লিখুন" autocomplete="off">
                <input type="password" id="confirmPasswordInput" placeholder="নতুন পাসওয়ার্ড নিশ্চিত করুন" autocomplete="off">
                <button onclick="setNewPassword()">নতুন পাসওয়ার্ড সংরক্ষণ করুন</button>
                <p id="newPassError" style="color: #dc2626; font-size: 13px; margin-top: 10px; display: none;"></p>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2026 My Digital & Clothing Store. All rights reserved.</p>
    </footer>

    <!-- JavaScript Logic -->
    <script>
        // ==================== CONFIGURATION (সুরক্ষিত) ====================
        // পাসওয়ার্ড ও রিকভারি কোড এনকোডেড আকারে রাখা হয়েছে
        // সাধারণ View Source এ সরাসরি পড়া যাবে না
        const _0x4a2f = ["QWRtaW5AMjAyNg==", "NDc4MjI0"];

        function _d(s) {
            try { return atob(s); } catch(e) { return ""; }
        }

        function getAdminPassword() {
            const stored = localStorage.getItem('_ap');
            if (stored) {
                try { return _d(stored); } catch(e) { return _d(_0x4a2f[0]); }
            }
            return _d(_0x4a2f[0]);
        }

        function setAdminPassword(newPass) {
            localStorage.setItem('_ap', btoa(newPass));
        }

        function getRecoveryCode() {
            return _d(_0x4a2f[1]);
        }

        // ==================== STATE ====================
        let items = JSON.parse(localStorage.getItem('storeItems')) || [
            {
                id: 1,
                category: 'clothing',
                title: 'স্টাইলিশ প্রিমিয়াম উইন্টার হুডি',
                price: '৳ 850',
                sampleUrl: 'https://images.unsplash.com/photo-1556905055-8f358a7a47b2?auto=format&fit=crop&w=600&q=80',
                fullUrl: 'https://example.com/order-success-1',
                desc: 'উচ্চমানের সুতি কাপড়ে তৈরি আরামদায়ক হুডি।',
                sizes: 'M, L, XL',
                colors: 'Black, Navy Blue, Ash',
                likes: 15,
                loves: 32,
                reviews: [{ name: 'রিফাত', text: 'কাপড়ের মান অনেক ভালো ছিল!' }]
            },
            {
                id: 2,
                category: 'video',
                title: 'কমপ্লিট ওয়েব ডেভেলপমেন্ট কোর্স',
                price: '৳ 300',
                sampleUrl: 'https://www.w3schools.com/html/mov_bbb.mp4',
                fullUrl: 'https://example.com/full-video-link-1',
                desc: 'জিরো থেকে প্রো লেভেল ওয়েব ডেভেলপমেন্ট শিখুন।',
                likes: 12,
                loves: 25,
                reviews: [{ name: 'হাসান', text: 'অসাধারণ একটি কোর্স!' }]
            }
        ];

        let unlockedItems = JSON.parse(localStorage.getItem('unlockedItems')) || [];
        let pendingItems = JSON.parse(localStorage.getItem('pendingItems')) || [];
        let orders = JSON.parse(localStorage.getItem('storeOrders')) || [];
        let isAdminLoggedIn = false;

        let currentItemId = null;
        let currentItemTitle = '';
        let currentSelectedSize = '';
        let currentSelectedColor = '';

        // ==================== ADMIN AUTH ====================
        function requestAdminAccess() {
            if (isAdminLoggedIn) {
                toggleAdminPanel();
            } else {
                document.getElementById('adminLoginModal').style.display = 'flex';
                document.getElementById('adminPassword').value = '';
                document.getElementById('loginError').style.display = 'none';
            }
        }

        function closeAdminLogin() {
            document.getElementById('adminLoginModal').style.display = 'none';
        }

        function verifyAdminPassword() {
            const password = document.getElementById('adminPassword').value;
            if (password === getAdminPassword()) {
                isAdminLoggedIn = true;
                document.getElementById('adminLoginModal').style.display = 'none';
                document.getElementById('adminToggleBtn').style.display = 'none';
                document.getElementById('adminLogoutBtn').style.display = 'inline-block';
                document.getElementById('adminPanel').style.display = 'block';
                renderOrdersTable();
                renderAdminItemList();
            } else {
                document.getElementById('loginError').style.display = 'block';
            }
        }

        function logoutAdmin() {
            isAdminLoggedIn = false;
            document.getElementById('adminPanel').style.display = 'none';
            document.getElementById('adminToggleBtn').style.display = 'inline-block';
            document.getElementById('adminLogoutBtn').style.display = 'none';
        }

        function toggleAdminPanel() {
            const panel = document.getElementById('adminPanel');
            if (isAdminLoggedIn) {
                panel.style.display = panel.style.display === 'block' ? 'none' : 'block';
                if (panel.style.display === 'block') {
                    renderOrdersTable();
                    renderAdminItemList();
                }
            }
        }

        // ==================== PASSWORD RECOVERY ====================
        function showForgotPassword() {
            document.getElementById('adminLoginModal').style.display = 'none';
            document.getElementById('forgotPasswordModal').style.display = 'flex';
            // Reset recovery form
            document.getElementById('recoveryStep1').style.display = 'block';
            document.getElementById('recoveryStep2').style.display = 'none';
            document.getElementById('recoveryCodeInput').value = '';
            document.getElementById('recoveryError').style.display = 'none';
            document.getElementById('newPasswordInput').value = '';
            document.getElementById('confirmPasswordInput').value = '';
            document.getElementById('newPassError').style.display = 'none';
        }

        function closeForgotPassword() {
            document.getElementById('forgotPasswordModal').style.display = 'none';
        }

        function verifyRecoveryCode() {
            const code = document.getElementById('recoveryCodeInput').value.trim();
            if (code === getRecoveryCode()) {
                document.getElementById('recoveryStep1').style.display = 'none';
                document.getElementById('recoveryStep2').style.display = 'block';
                document.getElementById('recoveryError').style.display = 'none';
            } else {
                document.getElementById('recoveryError').style.display = 'block';
            }
        }

        function setNewPassword() {
            const newPass = document.getElementById('newPasswordInput').value;
            const confirmPass = document.getElementById('confirmPasswordInput').value;
            const errorEl = document.getElementById('newPassError');

            if (!newPass || newPass.length < 4) {
                errorEl.textContent = 'পাসওয়ার্ড কমপক্ষে ৪ অক্ষরের হতে হবে।';
                errorEl.style.display = 'block';
                return;
            }
            if (newPass !== confirmPass) {
                errorEl.textContent = 'দুটি পাসওয়ার্ড মিলছে না।';
                errorEl.style.display = 'block';
                return;
            }

            setAdminPassword(newPass);
            errorEl.style.display = 'none';
            alert('নতুন পাসওয়ার্ড সফলভাবে সংরক্ষণ করা হয়েছে। এখন নতুন পাসওয়ার্ড দিয়ে লগইন করুন।');
            closeForgotPassword();
            // Automatically open login modal
            document.getElementById('adminLoginModal').style.display = 'flex';
            document.getElementById('adminPassword').value = '';
            document.getElementById('loginError').style.display = 'none';
        }

        // ==================== PRODUCT MANAGEMENT ====================
        function toggleCategoryFields() {
            const category = document.getElementById('itemCategory').value;
            const clothingFields = document.getElementById('clothingFields');
            clothingFields.style.display = (category === 'clothing') ? 'block' : 'none';
        }

        function addNewItem(event) {
            event.preventDefault();
            if (!isAdminLoggedIn) {
                alert('শুধুমাত্র অ্যাডমিন পণ্য যোগ করতে পারেন।');
                return;
            }

            const category = document.getElementById('itemCategory').value;
            const title = document.getElementById('itemTitle').value;
            const price = document.getElementById('itemPrice').value;
            const sampleUrl = document.getElementById('itemSampleUrl').value;
            const fullUrl = document.getElementById('itemFullUrl').value;
            const desc = document.getElementById('itemDesc').value;
            const sizes = category === 'clothing' ? document.getElementById('itemSizes').value : '';
            const colors = category === 'clothing' ? document.getElementById('itemColors').value : '';

            const newItem = {
                id: Date.now(),
                category,
                title,
                price,
                sampleUrl,
                fullUrl,
                desc,
                sizes,
                colors,
                likes: 0,
                loves: 0,
                reviews: []
            };

            items.push(newItem);
            localStorage.setItem('storeItems', JSON.stringify(items));
            
            document.getElementById('uploadForm').reset();
            toggleCategoryFields();
            renderItems('all');
            renderAdminItemList();
            alert('পণ্য সফলভাবে পাবলিশ হয়েছে।');
        }

        function deleteItem(id) {
            if (!isAdminLoggedIn) {
                alert('শুধুমাত্র অ্যাডমিন পণ্য মুছে ফেলতে পারেন।');
                return;
            }
            if (confirm('আপনি কি নিশ্চিতভাবে এই পণ্যটি ডিলিট করতে চান?')) {
                items = items.filter(item => item.id !== id);
                localStorage.setItem('storeItems', JSON.stringify(items));
                renderItems('all');
                renderAdminItemList();
                alert('পণ্যটি সফলভাবে ডিলিট করা হয়েছে।');
            }
        }

        function renderAdminItemList() {
            const container = document.getElementById('adminItemList');
            if (!container) return;

            if (items.length === 0) {
                container.innerHTML = '<p style="color:#64748b;">কোনো পণ্য নেই।</p>';
                return;
            }

            container.innerHTML = items.map(item => `
                <div class="admin-item-row">
                    <div>
                        <strong>${item.title}</strong>
                        <br>
                        <small style="color:#64748b;">${item.category} | ${item.price}</small>
                    </div>
                    <button onclick="deleteItem(${item.id})">🗑️ ডিলিট</button>
                </div>
            `).join('');
        }

        // ==================== REACTIONS & REVIEWS ====================
        function addReaction(id, type) {
            const item = items.find(i => i.id === id);
            if (item) {
                if (type === 'like') item.likes++;
                if (type === 'love') item.loves++;
                localStorage.setItem('storeItems', JSON.stringify(items));
                const activeTab = document.querySelector('.tab-btn.active');
                let cat = 'all';
                if (activeTab) {
                    const text = activeTab.textContent;
                    if (text.includes('পোশাক')) cat = 'clothing';
                    else if (text.includes('ভিডিও')) cat = 'video';
                    else if (text.includes('বই')) cat = 'book';
                    else if (text.includes('ছবি')) cat = 'photo';
                }
                renderItems(cat);
            }
        }

        function addReview(event, id) {
            event.preventDefault();
            const nameInput = document.getElementById(`name-${id}`);
            const textInput = document.getElementById(`text-${id}`);
            
            const name = nameInput.value.trim();
            const text = textInput.value.trim();

            if (name && text) {
                const item = items.find(i => i.id === id);
                if (item) {
                    item.reviews.push({ name, text });
                    localStorage.setItem('storeItems', JSON.stringify(items));
                    renderItems('all');
                    alert('আপনার রিভিউ সফলভাবে জমা হয়েছে।');
                }
            }
        }

        // ==================== RENDER CATALOG ====================
        function renderItems(filterCategory) {
            const grid = document.getElementById('itemGrid');
            grid.innerHTML = '';

            items.forEach(item => {
                if (filterCategory !== 'all' && item.category !== filterCategory) {
                    return;
                }

                const isUnlocked = unlockedItems.includes(item.id);
                const isPending = pendingItems.includes(item.id);
                
                let mediaHtml = '';
                if (item.category === 'video') {
                    mediaHtml = `
                        <div class="media-preview">
                            <video src="${item.sampleUrl}" muted controls loop></video>
                            <span class="sample-tag">ভিডিও স্যাম্পল</span>
                        </div>
                    `;
                } else {
                    mediaHtml = `
                        <div class="media-preview">
                            <img src="${item.sampleUrl}" alt="Sample">
                            <span class="sample-tag">পণ্যের ছবি</span>
                        </div>
                    `;
                }

                // Clothing options
                let clothingOptionsHtml = '';
                if (item.category === 'clothing') {
                    const sizeList = item.sizes ? item.sizes.split(',') : ['Free Size'];
                    const colorList = item.colors ? item.colors.split(',') : ['Standard'];

                    clothingOptionsHtml = `
                        <div style="background: #f1f5f9; padding: 10px; border-radius: 6px; margin: 12px 0; font-size: 13px;">
                            <div style="margin-bottom: 8px; display: flex; align-items: center; justify-content: space-between;">
                                <label style="font-weight: bold;">সাইজ:</label>
                                <select id="size-${item.id}" style="padding: 4px 8px; border-radius: 4px; border: 1px solid #cbd5e1; width: 70%;">
                                    ${sizeList.map(s => `<option value="${s.trim()}">${s.trim()}</option>`).join('')}
                                </select>
                            </div>
                            <div style="display: flex; align-items: center; justify-content: space-between;">
                                <label style="font-weight: bold;">কালার:</label>
                                <select id="color-${item.id}" style="padding: 4px 8px; border-radius: 4px; border: 1px solid #cbd5e1; width: 70%;">
                                    ${colorList.map(c => `<option value="${c.trim()}">${c.trim()}</option>`).join('')}
                                </select>
                            </div>
                        </div>
                    `;
                }

                let btnText = '🔒 অর্ডার / আনলক করুন';
                let btnClass = 'btn-action';
                let onClickAttr = `openPaymentModal(${item.id}, '${item.title.replace(/'/g, "\\'")}', '${item.price}', '${item.category}')`;

                if (isUnlocked) {
                    btnText = '🔓 অ্যাক্সেস বা কনফার্মেশন দেখুন';
                    btnClass = 'btn-action unlocked';
                    onClickAttr = `accessContent('${item.fullUrl}')`;
                } else if (isPending) {
                    btnText = '⏳ পেমেন্ট ভেরিফিকেশনের অপেক্ষায়';
                    btnClass = 'btn-action pending';
                    onClickAttr = `alert('আপনার পেমেন্ট বর্তমানে অ্যাডমিনের পর্যালোচনায় আছে। অনুগ্রহ করে অপেক্ষা করুন।')`;
                }

                let reviewsHtml = '';
                if (item.reviews && item.reviews.length > 0) {
                    item.reviews.forEach(rev => {
                        reviewsHtml += `<div class="review-item"><strong>${rev.name}:</strong> ${rev.text}</div>`;
                    });
                } else {
                    reviewsHtml = `<div style="color: #94a3b8; font-size: 12px; text-align: center;">এখনো কোনো রিভিউ নেই।</div>`;
                }

                const card = document.createElement('div');
                card.className = 'item-card';
                card.innerHTML = `
                    <div class="item-badge">${item.category}</div>
                    ${mediaHtml}
                    <div class="item-info">
                        <div>
                            <h3 class="item-title">${item.title}</h3>
                            <p class="item-desc">${item.desc}</p>
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <span class="price">${item.price}</span>
                            </div>

                            ${clothingOptionsHtml}

                            <div class="reactions-bar">
                                <button class="react-btn" onclick="addReaction(${item.id}, 'like')">👍 লাইক (${item.likes})</button>
                                <button class="react-btn" onclick="addReaction(${item.id}, 'love')">❤️ লাভ (${item.loves})</button>
                            </div>

                            <div class="reviews-section">
                                <div style="font-weight: bold; margin-bottom: 5px; color: #1e293b;">রিভিউ ও কমেন্ট:</div>
                                <div class="review-list">
                                    ${reviewsHtml}
                                </div>
                                <form class="review-form" onsubmit="addReview(event, ${item.id})">
                                    <input type="text" id="name-${item.id}" placeholder="আপনার নাম" required>
                                    <input type="text" id="text-${item.id}" placeholder="আপনার মন্তব্য লিখুন" required>
                                    <button type="submit">রিভিউ জমা দিন</button>
                                </form>
                            </div>
                        </div>

                        <div>
                            <button class="${btnClass}" onclick="${onClickAttr}">${btnText}</button>
                        </div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function filterItems(category) {
            const buttons = document.querySelectorAll('.tab-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            renderItems(category);
        }

        // ==================== PAYMENT FLOW ====================
        function openPaymentModal(id, title, price, category) {
            currentItemId = id;
            currentItemTitle = title;
            
            if (category === 'clothing') {
                const sizeEl = document.getElementById(`size-${id}`);
                const colorEl = document.getElementById(`color-${id}`);
                currentSelectedSize = sizeEl ? sizeEl.value : 'N/A';
                currentSelectedColor = colorEl ? colorEl.value : 'N/A';
            } else {
                currentSelectedSize = 'N/A';
                currentSelectedColor = 'N/A';
            }

            document.getElementById('modalItemTitle').innerText = `অর্ডার করুন: ${title}`;
            document.getElementById('modalItemPrice').innerText = price;
            document.getElementById('modalSelectedOptions').innerText = 
                category === 'clothing' 
                    ? `সাইজ: ${currentSelectedSize}, কালার: ${currentSelectedColor}` 
                    : 'প্রযোজ্য নয় (ডিজিটাল আইটেম)';
            document.getElementById('paymentModal').style.display = 'flex';
        }

        function closePaymentModal() {
            document.getElementById('paymentModal').style.display = 'none';
        }

        function submitPaymentRequest(event) {
            event.preventDefault();
            const method = document.getElementById('paymentMethod').value;
            const sender = document.getElementById('senderNumber').value.trim();
            const trx = document.getElementById('trxId').value.trim();

            if (!sender || !trx) {
                alert('দয়া করে সঠিক মোবাইল নাম্বার এবং ট্রানজেকশন আইডি প্রদান করুন।');
                return;
            }

            // Prevent duplicate pending for same item from same browser
            if (pendingItems.includes(currentItemId)) {
                alert('এই পণ্যের জন্য ইতিমধ্যে একটি পেমেন্ট রিকোয়েস্ট অপেক্ষমাণ আছে।');
                return;
            }

            const newOrder = {
                orderId: Date.now(),
                itemId: currentItemId,
                title: currentItemTitle,
                details: currentSelectedSize !== 'N/A' 
                    ? `সাইজ: ${currentSelectedSize}, কালার: ${currentSelectedColor}` 
                    : 'ডিজিটাল ফাইল',
                method,
                sender,
                trx
            };

            orders.push(newOrder);
            pendingItems.push(currentItemId);

            localStorage.setItem('storeOrders', JSON.stringify(orders));
            localStorage.setItem('pendingItems', JSON.stringify(pendingItems));

            alert('আপনার পেমেন্ট ও অর্ডার রিকোয়েস্ট সফলভাবে জমা হয়েছে।\\n\\nঅ্যাডমিন ভেরিফিকেশন সম্পন্ন হওয়ার পর আপনি পণ্যের অ্যাক্সেস পাবেন। অনুগ্রহ করে অপেক্ষা করুন।');
            
            closePaymentModal();
            document.getElementById('paymentForm').reset();
            renderItems('all');
        }

        // ==================== ORDER APPROVAL ====================
        function renderOrdersTable() {
            const tbody = document.getElementById('ordersTableBody');
            tbody.innerHTML = '';

            if (orders.length === 0) {
                tbody.innerHTML = `<tr><td colspan="5" style="text-align: center; color: #64748b;">কোনো পেমেন্ট রিকোয়েস্ট নেই।</td></tr>`;
                return;
            }

            orders.forEach((order, index) => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${order.sender}</td>
                    <td>${order.method}</td>
                    <td><strong>${order.trx}</strong></td>
                    <td>${order.title}<br><small style="color: #0284c7;">(${order.details})</small></td>
                    <td>
                        <button class="btn-approve" onclick="approveOrder(${index}, ${order.itemId})">Approve</button>
                        <button class="btn-reject" onclick="rejectOrder(${index}, ${order.itemId})">Reject</button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        function approveOrder(index, itemId) {
            if (!isAdminLoggedIn) return;

            pendingItems = pendingItems.filter(id => id !== itemId);
            if (!unlockedItems.includes(itemId)) {
                unlockedItems.push(itemId);
            }
            orders.splice(index, 1);

            localStorage.setItem('unlockedItems', JSON.stringify(unlockedItems));
            localStorage.setItem('pendingItems', JSON.stringify(pendingItems));
            localStorage.setItem('storeOrders', JSON.stringify(orders));

            renderOrdersTable();
            renderItems('all');
            alert('অর্ডার সফলভাবে অনুমোদন করা হয়েছে। ক্রেতা এখন অ্যাক্সেস পাবেন।');
        }

        function rejectOrder(index, itemId) {
            if (!isAdminLoggedIn) return;
            if (confirm('আপনি কি এই অর্ডারটি বাতিল করতে চান?')) {
                pendingItems = pendingItems.filter(id => id !== itemId);
                orders.splice(index, 1);

                localStorage.setItem('pendingItems', JSON.stringify(pendingItems));
                localStorage.setItem('storeOrders', JSON.stringify(orders));

                renderOrdersTable();
                renderItems('all');
                alert('অর্ডারটি বাতিল করা হয়েছে।');
            }
        }

        function accessContent(fullUrl) {
            window.open(fullUrl, '_blank');
        }

        // ==================== INIT ====================
        renderItems('all');
    </script>

</body>
</html>
