<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Time Swap!🕜</title>
    <style>
        /* General Styles */
        html, body {
            height: 100%;
            margin: 0;
            padding: 0;
            font-family: 'Quicksand', sans-serif;
            background-color: #f8f0e3;
            color: #4a4a4a;
            line-height: 1.6;
        }

        .page-wrapper {
            display: flex;
            flex-direction: column;
            min-height: 100%;
            margin: 0 auto;
            max-width: 1200px;
            border: 5px solid #a2d2ff;
            border-radius: 15px;
            overflow: hidden;
            background-color: #fff;
            position: relative;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
        }

        .top-buttons {
            position: absolute;
            top: 20px;
            right: 20px;
            display: flex;
            gap: 10px;
            z-index: 10;
        }

        .top-buttons button {
            background-color: #ffb3ba;
            color: white;
            border: 1px solid #ff8c94;
            padding: 10px 15px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.2s ease, transform 0.1s ease;
        }

        .top-buttons button:hover {
            background-color: #ff8c94;
        }

        .top-buttons button:active {
            background-color: #e6737a;
            transform: scale(0.95);
        }

        header {
            background-color: #a2d2ff;
            color: white;
            padding: 2rem 0;
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 3px solid #8ac4ff;
        }

        h1, h2 {
            margin-bottom: 20px;
            color: #3f72af;
            text-align: center;
            font-family: 'Fredoka One', cursive;
        }

        main {
            padding: 40px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            gap: 30px; /* Space between sections */
        }

        /* Section Styling */
        .section {
            background-color: #f2faff;
            border: 1px solid #d0e2ff;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
            width: 100%;
            box-sizing: border-box;
        }

        .section-title {
            color: #3f72af;
            border-bottom: 2px dashed #d0e2ff;
            padding-bottom: 15px;
            margin-bottom: 25px;
            font-size: 1.7rem;
            font-family: 'Fredoka One', cursive;
        }

        /* User Info Section */
        #profile-section-wrapper .section-title {
            background-color: #e6f9ff; /* Light background for title */
            padding: 15px;
            border-radius: 8px 8px 0 0;
            margin-bottom: 0;
        }
        #profile-section-wrapper .section-content {
            background-color: #e6f9ff;
            padding: 30px;
            border: 1px solid #d0e2ff;
            border-radius: 0 0 10px 10px;
        }

        /* Create Task Section */
        #create-task-section-wrapper .section-title {
            background-color: #b8f2e6; /* Light background for title */
            padding: 15px;
            border-radius: 8px 8px 0 0;
            margin-bottom: 0;
        }
        #create-task-section-wrapper .section-content {
            background-color: #b8f2e6;
            padding: 30px;
            border: 1px solid #8ee4af;
            border-radius: 0 0 10px 10px;
        }

        /* Available Tasks Section */
        #available-tasks-section-wrapper .section-title {
            background-color: #fff5eb; /* Light background for title */
            padding: 15px;
            border-radius: 8px 8px 0 0;
            margin-bottom: 0;
        }
        #available-tasks-section-wrapper .section-content {
            background-color: #fff5eb;
            padding: 30px;
            border: 1px solid #ffe8d6;
            border-radius: 0 0 10px 10px;
        }

        /* User Info */
        .user-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }

        .user-info p {
            margin: 0;
            font-size: 1.1rem;
            color: #555;
        }

        .user-info button {
            background-color: #a7d9ed;
            color: #333;
            border: 1px solid #8ac4ff;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s ease;
        }

        .user-info button:hover {
            background-color: #8ac4ff;
            color: white;
        }

        /* Profile Section */
        #proflile-section input[type="text"],
        #proflile-section input[type="tel"],
        #task-form input[type="text"],
        #task-form textarea,
        #task-form input[type="number"] {
            width: calc(100% - 24px);
            padding: 12px;
            margin-bottom: 15px;
            border: 1px solid #ccebff;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 1rem;
        }

        #proflile-section button,
        #task-form button {
            background-color: #b8f2e6;
            color: #333;
            border: 1px solid #8ee4af;
            padding: 12px 22px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s ease;
        }

        #proflile-section button:hover,
        #task-form button:hover {
            background-color: #8ee4af;
            color: white;
        }

        /* Task Form */
        #task-form {
            display: none; /* Initially hidden */
            padding-top: 20px;
        }

        #task-form textarea {
            height: 120px;
            border: 1px solid #ccebff;
            border-radius: 8px;
        }

        /* Task List */
        .task-list {
            list-style: none;
            padding: 0;
        }

        .task-list li {
            background-color: #fff;
            border: 1px solid #ffe8d6;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
        }

        .task-list li h3 {
            margin-top: 0;
            margin-bottom: 10px;
            color: #3f72af;
        }

        .task-list li p {
            margin-bottom: 8px;
            color: #555;
        }

        .task-list li .task-details {
            margin-bottom: 12px;
            font-size: 0.95rem;
            color: #777;
        }

        .task-list li .actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .task-list li .actions button {
            padding: 10px 15px;
            font-size: 0.9rem;
            cursor: pointer;
            border: none;
            border-radius: 6px;
            transition: background-color 0.3s ease;
        }

        .task-list li .actions .accept-btn {
            background-color: #a7d9ed;
            color: #333;
        }

        .task-list li .actions .accept-btn:hover {
            background-color: #8ac4ff;
            color: white;
        }

        .task-list li .actions .verify-btn {
            background-color: #fdd835;
            color: #333;
        }

        .task-list li .actions .verify-btn:hover {
            background-color: #fbc02d;
        }

        .task-list li .actions .completed-text {
            color: #777;
            font-style: italic;
        }

        .task-list li .actions .view-profile-btn {
            background-color: #f0ad4e;
            color: white;
        }

        .task-list li .actions .view-profile-btn:hover {
            background-color: #e08e0b;
        }

        .task-list li .actions .view-offerer-profile-btn {
            background-color: #5cb85c;
            color: white;
        }

        .task-list li .actions .view-offerer-profile-btn:hover {
            background-color: #4cae4c;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 1.5rem 0;
            color: #777;
            font-size: 0.9rem;
            margin-top: 40px;
            border-top: 1px solid #d0e2ff;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.4);
        }

        .modal-content {
            background-color: #fff;
            margin: 15% auto; /* Adjusted margin */
            padding: 30px;
            border: 1px solid #a2d2ff;
            width: 80%;
            border-radius: 12px;
            position: relative;
        }

        .close-button {
            color: #aaa;
            position: absolute;
            top: 10px;
            right: 15px; /* Adjusted position */
            font-size: 30px;
            font-weight: bold;
            cursor: pointer;
        }

        .close-button:hover,
        .close-button:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }

        .modal-content h2 {
            margin-top: 0;
            margin-bottom: 20px;
            color: #3f72af;
            font-family: 'Fredoka One', cursive;
        }

        .modal-content p {
            margin-bottom: 15px;
            line-height: 1.7;
        }

        .modal-content ul {
            padding-left: 20px;
            margin-bottom: 15px;
        }

        .modal-content li {
            margin-bottom: 8px;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .page-wrapper {
                margin: 0 auto;
                border-left: none;
                border-right: none;
                border-radius: 0;
                box-shadow: none;
            }
            .top-buttons {
                position: fixed;
                top: 0;
                right: 0;
                background-color: rgba(255, 255, 255, 0.9);
                padding: 10px;
                border-bottom: 1px solid #ddd;
            }
            header {
                margin-top: 60px;
            }
            main {
                padding: 20px;
                gap: 20px;
            }
            .section {
                padding: 20px;
                margin-bottom: 15px;
            }
        }

        @media (max-width: 600px) {
            .top-buttons {
                flex-direction: column;
                align-items: flex-end;
                gap: 5px;
            }
            .top-buttons button {
                width: 100%;
            }
            main {
                padding: 20px;
                gap: 20px;
            }
            .section {
                padding: 15px;
            }
        }

        /* Location Settings */
        #location-settings {
            margin-bottom: 20px;
            padding: 15px;
            background-color: #e0f7fa;
            border: 1px solid #b2ebf2;
            border-radius: 8px;
            display: flex;
            gap: 15px;
            align-items: center;
        }

        #location-settings label {
            font-weight: bold;
        }

        #default-location {
            padding: 8px;
            border: 1px solid #8ac4ff;
            border-radius: 4px;
        }

        #location-range {
            padding: 8px;
            border: 1px solid #8ac4ff;
            border-radius: 4px;
        }

        #set-default-location-btn, #use-current-location-btn {
            background-color: #a7d9ed;
            color: #333;
            border: 1px solid #8ac4ff;
            padding: 8px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: background-color 0.3s ease;
        }

        #set-default-location-btn:hover, #use-current-location-btn:hover {
            background-color: #8ac4ff;
            color: white;
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;700&family=Fredoka+One&display=swap" rel="stylesheet">
</head>
<body>
    <div class="page-wrapper">
        <div class="top-buttons">
            <button id="about-btn">About App</button>
            <button id="terms-btn">Terms of Service</button>
        </div>
        <header>
            <h1>Time Swap!</h1>
            <p style="font-size: 1.1rem; margin-top: 5px;">Connecting Your Local Community</p>
        </header>
        <main>
            <div id="profile-section-wrapper">
                <h2 class="section-title">Your Profile</h2>
                <div class="section-content">
                    <div class="user-info">
                        <p>Your Credits: <span id="user-credits">0</span></p>
                        <button id="profile-btn">CreateProfile</button>
                    </div>
                    <div id="proflile-section" style="display: none;">
                        <input type="text" id="profile-name" placeholder="Enter your name">
                        <input type="tel" id="profile-phone" placeholder="Enter your phone number">
                        <button id="save-profile">Save Profile</button>
                    </div>
                </div>
            </div>

            <div id="location-settings">
                <h2 class="section-title">Location Settings</h2>
                <label for="default-location">Default Location:</label>
                <input type="text" id="default-location" placeholder="e.g., Sugar Land, TX">
                <button id="set-default-location-btn">Set Default</button>
                <button id="use-current-location-btn">Use Current Location</button>
                <label for="location-range">Show tasks within:</label>
                <select id="location-range">
                    <option value="all">All</option>
                    <option value="20">20 miles</option>
                    <option value="30">30 miles</option>
                </select>
            </div>

            <div id="create-task-section-wrapper">
                <h2 class="section-title">Offer Your Time</h2>
                <div class="section-content">
                    <button id="add-task-btn">Create a New Task</button>
                    <form id="task-form" style="display: none;">
                        <input type="text" id="task-title" placeholder="Task Title">
                        <textarea id="task-description" placeholder="Task Description"></textarea>
                        <input type="number" id="task-hours" placeholder="Estimated Hours">
                        <button type="button" id="submit-task">Submit Task</button>
                    </form>
                </div>
            </div>

            <div id="available-tasks-section-wrapper">
                <h2 class="section-title">View Available Tasks</h2>
                <div class="section-content">
                    <ul class="task-list" id="task-list"></ul>
                </div>
            </div>
        </main>
        <footer>
            <p>&copy; 2023 Time Swap! All rights reserved.</p>
        </footer>

        <div id="about-modal" class="modal">
            <div class="modal-content">
                <span class="close-button" id="close-about">&times;</span>
                <h2>About Time Swap! 😊</h2>
                <p>Time Swap! is a community platform designed to help people exchange services and skills. Offer your time to help others and earn credits, which you can then use to request help for your own needs.</p>
                <p>Connect with your local community and build a network of mutual support!</p>
                <h3>Key Features:</h3>
                <ul>
                    <li>Create a profile and earn credits for helping others.</li>
                    <li>Offer tasks you need help with or offer your skills to assist others.</li>
                    <li>Browse available tasks in your local area.</li>
                    <li>Accept tasks and coordinate with the task poster.</li>
                    <li>Verify task completion to award credits.</li>
                </ul>
                <p>We believe in the power of community and the value of shared time and effort.</p>
            </div>
        </div>

        <div id="terms-modal" class="modal">
            <div class="modal-content">
                <span class="close-button" id="close-terms">&times;</span>
                <h2>Terms of Service 🕜</h2>
                <p>Please read these Terms of Service carefully before using the Time Swap! application.</p>
                <p>By accessing or using the application, you agree to be bound by these terms.</p>
                <h3>1. Acceptance of Terms</h3>
                <p>These Terms of Service constitute a legally binding agreement between you and Time Swap!.</p>
                <h3>2. User Accounts</h3>
                <p>You are responsible for maintaining the confidentiality of your account and password.</p>
                <h3>3. Task Listings</h3>
                <p>Users are responsible for the accuracy and legality of their task listings.</p>
                <h3>4. Credits</h3>
                <p>Credits earned through Time Swap! are non-transferable and have no cash value.</p>
                <h3>5. Limitation of Liability</h3>
                <p>Time Swap! is not responsible for any interactions or outcomes resulting from the use of the application.</p>
                <p>For the full Terms of Service, please refer to our dedicated policy page.</p>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // DOM Elements
            const aboutBtn = document.getElementById('about-btn');
            const termsBtn = document.getElementById('terms-btn');
            const aboutModal = document.getElementById('about-modal');
            const termsModal = document.getElementById('terms-modal');
            const closeAbout = document.getElementById('close-about');
            const closeTerms = document.getElementById('close-terms');

            const profileSection = document.getElementById('proflile-section');
            const profileBtn = document.getElementById('profile-btn');
            const profileNameInput = document.getElementById('profile-name');
            const profilePhoneInput = document.getElementById('profile-phone');
            const saveProfileBtn = document.getElementById('save-profile');
            const userCreditsSpan = document.getElementById('user-credits');
            const addTaskBtn = document.getElementById('add-task-btn');
            const taskForm = document.getElementById('task-form');
            const taskTitleInput = document.getElementById('task-title');
            const taskDescriptionInput = document.getElementById('task-description');
            const taskHoursInput = document.getElementById('task-hours');
            const submitTaskBtn = document.getElementById('submit-task');
            const taskList = document.getElementById('task-list');

            const defaultLocationInput = document.getElementById('default-location');
            const setDefaultLocationBtn = document.getElementById('set-default-location-btn');
            const useCurrentLocationBtn = document.getElementById('use-current-location-btn');
            const locationRangeSelect = document.getElementById('location-range');

            // Local Storage Keys
            const PROFILE_KEY = 'timeSwapProfile';
            const CREDITS_KEY = 'timeSwapCredits';
            const TASKS_KEY = 'timeSwapTasks';
            const LOCATION_KEY = 'timeSwapLocation';
            const LOCATION_RANGE_KEY = 'timeSwapLocationRange';

            // Default Values
            let userProfile = getFromLocalStorage(PROFILE_KEY, {});
            let userCredits = getFromLocalStorage(CREDITS_KEY, 0);
            let tasks = getFromLocalStorage(TASKS_KEY, []);
            let userLocation = getFromLocalStorage(LOCATION_KEY, null);
            let locationRange = getFromLocalStorage(LOCATION_RANGE_KEY, 'all');

            // Helper Functions
            function saveToLocalStorage(key, value) {
                localStorage.setItem(key, JSON.stringify(value));
            }

            function getFromLocalStorage(key, defaultValue) {
                const storedValue = localStorage.getItem(key);
                return storedValue ? JSON.parse(storedValue) : defaultValue;
            }

            function updateCreditsDisplay() {
                userCreditsSpan.textContent = userCredits;
            }

            function toggleProfileSection() {
                profileSection.style.display = profileSection.style.display === 'none' ? 'block' : 'none';
                profileBtn.textContent = userProfile.name ? 'Edit Profile' : 'Create Profile';
                if (userProfile.name) {
                    profileNameInput.value = userProfile.name;
                    profilePhoneInput.value = userProfile.phone || '';
                } else {
                    profileNameInput.value = '';
                    profilePhoneInput.value = '';
                }
            }

            function getLocation() {
                if (navigator.geolocation) {
                    navigator.geolocation.getCurrentPosition(showPosition, handleLocationError);
                } else {
                    alert("Geolocation is not supported by this browser.");
                }
            }

            function showPosition(position) {
                userLocation = { coords: { latitude: position.coords.latitude, longitude: position.coords.longitude } };
                saveToLocalStorage(LOCATION_KEY, userLocation);
                alert(`Location updated to: Latitude ${position.coords.latitude}, Longitude ${position.coords.longitude}`);
                renderTaskList();
            }

            function handleLocationError(error) {
                switch (error.code) {
                    case error.PERMISSION_DENIED:
                        alert("User denied the request for Geolocation.");
                        break;
                    case error.POSITION_UNAVAILABLE:
                        alert("Location information is unavailable.");
                        break;
                    case error.TIMEOUT:
                        alert("The request to get user location timed out.");
                        break;
                    case error.UNKNOWN_ERROR:
                        alert("An unknown error occurred.");
                        break;
                }
            }

            function calculateDistance(lat1, lon1, lat2, lon2) {
                const R = 6371; // Radius of the earth in km
                const dLat = deg2rad(lat2 - lat1);
                const dLon = deg2rad(lon2 - lon1);
                const a =
                    Math.sin(dLat / 2) * Math.sin(dLat / 2) +
                    Math.cos(deg2rad(lat1)) * Math.cos(deg2rad(lat2)) *
                    Math.sin(dLon / 2) * Math.sin(dLon / 2);
                const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
                const distanceKm = R * c; // Distance in km
                return distanceKm * 0.621371; // Distance in miles
            }

            function deg2rad(deg) {
                return deg * (Math.PI / 180)
            }

            function acceptTask(index) {
                if (!userProfile.name) {
                    alert('Please create a profile before accepting tasks.');
                    return;
                }
                if (tasks[index].status === 'available' && tasks[index].offererName !== userProfile.name) {
                    tasks[index].status = 'accepted';
                    tasks[index].accepterName = userProfile.name; // Add the name of the accepter
                    saveToLocalStorage(TASKS_KEY, tasks);
                    renderTaskList(); // Re-render to update the button visibility
                } else {
                    alert('This task is no longer available or you cannot accept your own task.');
                }
            }

            function verifyTask(index) {
                if (tasks[index].status === 'accepted' && tasks[index].offererName === userProfile.name) {
                    const hours = tasks[index].hours;
                    userCredits += hours * 2;
                    saveToLocalStorage(CREDITS_KEY, userCredits);
                    tasks[index].status = 'completed';
                    saveToLocalStorage(TASKS_KEY, tasks);
                    updateCreditsDisplay();
                    renderTaskList();
                    alert(`Task completed! You have awarded ${hours * 2} credits.`);
                } else {
                    alert('You cannot verify completion for a task that is not accepted or not offered by you.');
                }
            }

            function filterTasksByLocation(taskListArray, currentLocation, range) {
                if (range === 'all' || !currentLocation?.coords) {
                    return taskListArray;
                }

                const filtered = taskListArray.filter(task => {
                    if (task.offererName === userProfile.name) {
                        return true; // Always show user's own tasks
                    }
                    if (task.locationCoords && currentLocation.coords) {
                        const distance = calculateDistance(
                            currentLocation.coords.latitude,
                            currentLocation.coords.longitude,
                            task.locationCoords.latitude,
                            task.locationCoords.longitude
                        );
                        return (range === '20' && distance <= 20) || (range === '30' && distance <= 30);
                    } else if (task.location && currentLocation?.string) {
                        // Basic string matching as a fallback if coordinates aren't available
                        return task.location.toLowerCase().includes(currentLocation.string.toLowerCase());
                    }
                    return false; // Don't include if no location info or outside range
                });
                return filtered;
            }

            function displayProfile() {
                if (userProfile && userProfile.name) {
                    profileBtn.textContent = 'Edit Profile';
                    profileNameInput.value = userProfile.name;
                    profilePhoneInput.value = userProfile.phone || '';
                    profileSection.style.display = 'none'; // Hide after loading
                } else {
                    profileBtn.textContent = 'Create Profile';
                    profileSection.style.display = 'block';
                }
            }

            function renderTaskList() {
                taskList.innerHTML = '';
                const filteredTasks = filterTasksByLocation(tasks, userLocation, locationRange);

                filteredTasks.forEach((task, index) => {
                    const listItem = document.createElement('li');
                    listItem.innerHTML = `
                        <h3>${task.title}</h3>
                        <p class="task-details">Offered by: ${task.offererName || 'Anonymous'}</p>
                        <p class="task-details">Description: ${task.description}</p>
                        <p class="task-details">Hours: ${task.hours}</p>
                        <p class="task-details">Credits: ${task.hours * 2}</p>
                        <p class="task-details">Location: ${task.location || 'Not specified'}</p>
                        <p class="task-details">Status: ${task.status || 'available'}</p>
                        <div class="actions">
                            ${task.status === 'available' && task.offererName !== userProfile.name ? `<button class="accept-btn" data-index="${index}" data-offerer="${task.offererName}">Accept</button>` : ''}
                            ${task.status === 'completed' && task.offererName === userProfile.name ? '<span class="task-details">Completed</span>' : ''}
                            ${task.status === 'available' && task.offererName !== userProfile.name ? `<button class="view-profile-btn" data-profile-name="${task.offererName}">View Profile</button>` : ''}
                            ${task.status === 'accepted' && task.accepterName === userProfile.name ? `<button class="view-offerer-profile-btn" data-task-index="${index}">View Offerer Profile</button>` : ''}
                        </div>
                    `;

                    const acceptButton = listItem.querySelector('.accept-btn');
                    if (acceptButton) {
                        acceptButton.addEventListener('click', () => acceptTask(index));
                    }

                    const verifyButton = listItem.querySelector('.verify-btn');
                    if (verifyButton) {
                        verifyButton.addEventListener('click', () => verifyTask(index));
                    }

                    const viewProfileButton = listItem.querySelector('.view-profile-btn');
                    if (viewProfileButton) {
                        viewProfileButton.addEventListener('click', (event) => {
                            const profileName = event.target.dataset.profileName;
                            const otherUserProfile = tasks.find(task => task.offererName === profileName)?.offererProfile;
                            if (otherUserProfile) {
                                const canContact = otherUserProfile.allowContact;
                                const phoneNumber = canContact ? otherUserProfile.phone : 'Contact information not shared.';
                                alert(`Profile Name: ${otherUserProfile.name}\nPhone: ${phoneNumber}`);
                            } else {
                                alert('Profile information not found.');
                            }
                        });
                    }

                    const viewOffererProfileButton = listItem.querySelector('.view-offerer-profile-btn');
                    if (viewOffererProfileButton) {
                        viewOffererProfileButton.addEventListener('click', (event) => {
                            const taskIndex = parseInt(event.target.dataset.taskIndex);
                            const offererProfile = tasks[taskIndex]?.offererProfile;
                            if (offererProfile) {
                                const canContact = offererProfile.allowContact;
                                const phoneNumber = canContact ? offererProfile.phone : 'Contact information not shared.';
                                alert(`Offerer Profile Name: ${offererProfile.name}\nPhone: ${phoneNumber}`);
                            } else {
                                alert('Offerer profile information not found for this task.');
                            }
                        });
                    }

                    taskList.appendChild(listItem);
                });
            }

            saveProfileBtn.addEventListener('click', () => {
                const name = profileNameInput.value.trim();
                const phone = profilePhoneInput.value.trim();

                if (name) {
                    const allowContact = confirm('Allow others who accept your tasks to contact you through your phone number?');
                    userProfile = { name, phone, allowContact };
                    saveToLocalStorage(PROFILE_KEY, userProfile);
                    displayProfile();
                    alert('Profile saved!');
                    profileSection.style.display = 'none';
                    renderTaskList(); // Re-render to potentially show new tasks with the updated profile
                } else {
                    alert('Please enter your name.');
                }
            });

            profileBtn.addEventListener('click', toggleProfileSection);

            addTaskBtn.addEventListener('click', () => {
                taskForm.style.display = 'block';
            });

            submitTaskBtn.addEventListener('click', () => {
                const title = taskTitleInput.value.trim();
                const description = taskDescriptionInput.value.trim();
                const hours = parseInt(taskHoursInput.value.trim());
                const location = defaultLocationInput.value.trim();

                if (!title || !description || isNaN(hours) || hours <= 0) {
                    alert('Please fill out all fields.');
                    return;
                }

                const task = {
                    title,
                    description,
                    hours,
                    status: 'available',
                    offererName: userProfile.name,
                    offererProfile: { name: userProfile.name, phone: userProfile.phone, allowContact: userProfile.allowContact }, // Embed offerer's profile
                    location,
                    // In a real app, you'd geocode the location here and store coordinates
                };

                tasks.push(task);
                saveToLocalStorage(TASKS_KEY, tasks);
                taskForm.style.display = 'none';
                taskTitleInput.value = '';
                taskDescriptionInput.value = '';
                taskHoursInput.value = '';
                renderTaskList();
            });

            // Event listeners for modals
            aboutBtn.addEventListener('click', () => {
                aboutModal.style.display = 'block';
            });

            termsBtn.addEventListener('click', () => {
                termsModal.style.display = 'block';
            });

            closeAbout.addEventListener('click', () => {
                aboutModal.style.display = 'none';
            });

            closeTerms.addEventListener('click', () => {
                termsModal.style.display = 'none';
            });

            window.onclick = function(event) {
                if (event.target === aboutModal) {
                    aboutModal.style.display = 'none';
                }
                if (event.target === termsModal) {
                    termsModal.style.display = 'none';
                }
            }

            setDefaultLocationBtn.addEventListener('click', () => {
                const location = defaultLocationInput.value.trim();
                if (location) {
                    saveToLocalStorage(LOCATION_KEY, { string: location }); // Save as string for now
                    userLocation = { string: location };
                    alert(`Default location set to: ${location}`);
                    renderTaskList(); // Re-render based on potentially new location context (though filtering logic needs coordinates for distance)
                } else {
                    alert('Please enter a default location.');
                }
            });

            useCurrentLocationBtn.addEventListener('click', getLocation);

            locationRangeSelect.addEventListener('change', (event) => {
                locationRange = event.target.value;
                saveToLocalStorage(LOCATION_RANGE_KEY, locationRange);
                renderTaskList();
            });

            // Initial setup
            updateCreditsDisplay();
            displayProfile();
            renderTaskList();
            defaultLocationInput.value = userLocation?.string || '';
            locationRangeSelect.value = locationRange;
        });
    </script>
</body>
</html>
