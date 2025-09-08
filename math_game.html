<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Math Game</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #1a202c;
            color: #e2e8f0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 1rem;
        }

        .container {
            max-width: 500px;
            width: 100%;
        }

        .card {
            background-color: #2d3748;
            border: 2px solid #4a5568;
            border-radius: 1rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            padding: 2rem;
            transition: all 0.3s ease-in-out;
            transform: translateY(0);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
        }

        .input-field {
            background-color: #4a5568;
            color: #e2e8f0;
            border: 2px solid #a0aec0;
            border-radius: 0.5rem;
            padding: 0.75rem 1rem;
            outline: none;
            transition: border-color 0.3s ease-in-out;
            text-align: center;
        }
        .input-field:focus {
            border-color: #63b3ed;
        }

        .btn {
            background-color: #63b3ed;
            color: white;
            padding: 0.75rem 2rem;
            border-radius: 0.5rem;
            font-weight: 700;
            transition: background-color 0.3s ease-in-out, transform 0.1s ease-in-out;
        }
        .btn:hover {
            background-color: #4299e1;
            transform: scale(1.05);
        }
        .btn:active {
            transform: scale(0.95);
        }
        
        .correct {
            color: #48bb78;
        }
        .incorrect {
            color: #f56565;
        }

        .leaderboard-table th, .leaderboard-table td {
            padding: 0.5rem 1rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
    </style>
</head>
<body class="bg-gray-900 text-white flex items-center justify-center min-h-screen">

    <!-- Main Game Container -->
    <div class="container relative">
        
        <!-- Menu/Game Over Screen -->
        <div id="menu-screen" class="card absolute inset-0 flex flex-col items-center justify-center p-8 transition-opacity duration-500 ease-in-out z-10">
            <h3 id="menu-title" class="text-3xl font-bold mb-4">Math Game</h3>
            <p id="menu-message" class="text-lg mb-4 text-center">Solve as many problems as you can in 60 seconds!</p>
            
            <!-- Username Input -->
            <div class="mb-6 w-full flex flex-col items-center">
                <label for="username-input" class="block text-sm font-medium mb-1">Your Username</label>
                <input type="text" id="username-input" class="input-field w-2/3 mb-2 text-center" placeholder="Enter your username">
                <button id="save-username-btn" class="btn text-sm px-4 py-2">Save Username</button>
            </div>
            
            <button id="start-btn" class="btn mb-8">Start Game</button>
            
            <!-- Leaderboard Section -->
            <div class="w-full">
                <h4 class="text-2xl font-bold mb-4 text-center">Leaderboard</h4>
                <div id="leaderboard-container" class="bg-gray-700 p-4 rounded-lg overflow-y-auto max-h-56">
                    <table class="w-full text-left leaderboard-table">
                        <thead>
                            <tr>
                                <th class="py-2 text-blue-300">Rank</th>
                                <th class="py-2 text-blue-300">Username</th>
                                <th class="py-2 text-blue-300">User ID</th>
                                <th class="py-2 text-blue-300">Score</th>
                            </tr>
                        </thead>
                        <tbody id="leaderboard-body">
                            <!-- Leaderboard rows will be inserted here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Game Play Screen -->
        <div id="game-screen" class="card flex flex-col items-center p-8 opacity-0 pointer-events-none transition-opacity duration-500 ease-in-out">
            
            <!-- Score and Timer -->
            <div class="flex justify-between w-full mb-6">
                <div class="flex flex-col items-center">
                    <span class="text-sm font-semibold text-gray-400">Score</span>
                    <span id="score" class="text-2xl font-bold">0</span>
                </div>
                <div class="flex flex-col items-center">
                    <span class="text-sm font-semibold text-gray-400">Time</span>
                    <span id="timer" class="text-2xl font-bold">60s</span>
                </div>
            </div>

            <!-- Question and Input -->
            <div class="flex flex-col items-center">
                <h2 id="question" class="text-4xl font-extrabold mb-4 text-center"></h2>
                <input type="number" id="answer-input" class="input-field w-32 mb-4" placeholder="Your Answer" autofocus>
                <button id="submit-btn" class="btn w-full">Submit</button>
            </div>

            <!-- Feedback -->
            <div id="feedback" class="text-lg font-semibold mt-4 text-center h-8"></div>
        </div>
    </div>
    
    <!-- User ID Display -->
    <div class="absolute top-4 left-4 text-sm bg-gray-700 p-2 rounded-lg">
        Your User ID: <span id="user-id">Loading...</span>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, getDoc, addDoc, setDoc, updateDoc, deleteDoc, onSnapshot, collection, query, where, getDocs } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // --- Firebase Configuration & Initialization ---
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : '';
        
        let db, auth;
        let userId;
        let username = '';

        // --- Game Logic ---
        const questionEl = document.getElementById('question');
        const answerInput = document.getElementById('answer-input');
        const submitBtn = document.getElementById('submit-btn');
        const scoreEl = document.getElementById('score');
        const timerEl = document.getElementById('timer');
        const feedbackEl = document.getElementById('feedback');
        
        const menuScreen = document.getElementById('menu-screen');
        const menuTitle = document.getElementById('menu-title');
        const menuMessage = document.getElementById('menu-message');
        const startBtn = document.getElementById('start-btn');
        const gameScreen = document.getElementById('game-screen');
        
        const usernameInput = document.getElementById('username-input');
        const saveUsernameBtn = document.getElementById('save-username-btn');
        const userIdEl = document.getElementById('user-id');
        const leaderboardBody = document.getElementById('leaderboard-body');

        let score = 0;
        let timeRemaining = 60;
        let timerId;
        let currentQuestion = {};
        let isGameRunning = false;

        // Function to generate a new math question
        function generateQuestion() {
            let num1, num2;

            // Increase difficulty based on score
            if (score < 5) {
                num1 = Math.floor(Math.random() * 10) + 1;
                num2 = Math.floor(Math.random() * 10) + 1;
            } else if (score < 15) {
                num1 = Math.floor(Math.random() * 20) + 1;
                num2 = Math.floor(Math.random() * 20) + 1;
            } else {
                num1 = Math.floor(Math.random() * 50) + 1;
                num2 = Math.floor(Math.random() * 50) + 1;
            }

            const operators = ['+', '-', '*'];
            const operator = operators[Math.floor(Math.random() * operators.length)];

            let problem, answer;
            switch (operator) {
                case '+':
                    problem = `${num1} + ${num2}`;
                    answer = num1 + num2;
                    break;
                case '-':
                    // Ensure answer is non-negative
                    if (num1 < num2) [num1, num2] = [num2, num1];
                    problem = `${num1} - ${num2}`;
                    answer = num1 - num2;
                    break;
                case '*':
                    problem = `${num1} x ${num2}`;
                    answer = num1 * num2;
                    break;
            }

            currentQuestion = { problem, answer };
            questionEl.textContent = currentQuestion.problem;
            answerInput.value = '';
            answerInput.focus();
        }

        // Function to check the user's answer
        function checkAnswer() {
            if (!isGameRunning) return;

            const userAnswer = parseInt(answerInput.value, 10);
            if (isNaN(userAnswer)) {
                feedbackEl.textContent = "Please enter a number.";
                feedbackEl.classList.remove('correct', 'incorrect');
                return;
            }

            if (userAnswer === currentQuestion.answer) {
                score++;
                feedbackEl.textContent = "Correct!";
                feedbackEl.className = 'correct text-lg font-semibold mt-4 text-center h-8';
            } else {
                feedbackEl.textContent = `Incorrect. The answer was ${currentQuestion.answer}.`;
                feedbackEl.className = 'incorrect text-lg font-semibold mt-4 text-center h-8';
            }
            scoreEl.textContent = score;
            generateQuestion();
        }

        // Function to handle the game timer
        function updateTimer() {
            timeRemaining--;
            timerEl.textContent = `${timeRemaining}s`;

            if (timeRemaining <= 0) {
                endGame();
            }
        }

        // Function to start the game
        function startGame() {
            if (!username) {
                feedbackEl.textContent = "Please enter and save a username first.";
                feedbackEl.className = 'incorrect text-lg font-semibold mt-4 text-center h-8';
                return;
            }

            isGameRunning = true;
            score = 0;
            timeRemaining = 60;
            scoreEl.textContent = '0';
            timerEl.textContent = '60s';
            feedbackEl.textContent = '';
            
            // Hide the menu and show the game
            menuScreen.style.opacity = 0;
            menuScreen.style.pointerEvents = 'none';
            gameScreen.style.opacity = 1;
            gameScreen.style.pointerEvents = 'auto';

            generateQuestion();
            timerId = setInterval(updateTimer, 1000);
            answerInput.focus();
        }

        // Function to end the game
        function endGame() {
            clearInterval(timerId);
            isGameRunning = false;
            
            // Show the menu and hide the game
            gameScreen.style.opacity = 0;
            gameScreen.style.pointerEvents = 'none';
            menuScreen.style.opacity = 1;
            menuScreen.style.pointerEvents = 'auto';
            
            menuTitle.textContent = "Game Over!";
            menuMessage.textContent = `You scored ${score} points, ${username}! Great job!`;
            startBtn.textContent = "Play Again";

            if (userId && username) {
                saveScore(score, userId, username);
            }
        }
        
        // --- Firestore Functions ---
        
        async function saveScore(score, userId, username) {
            try {
                // Public data collection path for leaderboards
                const scoresCollection = collection(db, `artifacts/${appId}/public/data/scores`);
                await addDoc(scoresCollection, {
                    userId: userId,
                    username: username,
                    score: score,
                    timestamp: new Date()
                });
                console.log("Score saved successfully!");
            } catch (e) {
                console.error("Error adding document: ", e);
            }
        }

        function setupLeaderboard() {
            const scoresCollection = collection(db, `artifacts/${appId}/public/data/scores`);
            // Use onSnapshot to listen for real-time updates
            onSnapshot(scoresCollection, (snapshot) => {
                const scores = [];
                snapshot.forEach(doc => {
                    scores.push(doc.data());
                });

                // Sort scores in descending order
                scores.sort((a, b) => b.score - a.score);

                // Display top 10 scores
                leaderboardBody.innerHTML = '';
                scores.slice(0, 10).forEach((scoreData, index) => {
                    const row = document.createElement('tr');
                    row.className = 'border-b border-gray-600';
                    row.innerHTML = `
                        <td class="w-1/12">${index + 1}</td>
                        <td class="w-4/12">${scoreData.username}</td>
                        <td class="w-4/12">${scoreData.userId}</td>
                        <td class="w-3/12 text-right">${scoreData.score}</td>
                    `;
                    leaderboardBody.appendChild(row);
                });
            }, (error) => {
                console.error("Error fetching leaderboard: ", error);
            });
        }
        
        // --- Firebase Initialization and Auth ---
        window.onload = async function() {
            try {
                const app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);
                
                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }
                
                onAuthStateChanged(auth, async (user) => {
                    if (user) {
                        userId = user.uid;
                        userIdEl.textContent = userId;
                        setupLeaderboard();
                        
                        // Try to get existing username
                        const userDocRef = doc(db, `artifacts/${appId}/users/${userId}/profile`, 'data');
                        const userDoc = await getDoc(userDocRef);
                        if (userDoc.exists()) {
                            username = userDoc.data().username || '';
                            usernameInput.value = username;
                        }
                    } else {
                        userIdEl.textContent = "Not signed in";
                    }
                });
            } catch(e) {
                console.error("Error initializing Firebase:", e);
                userIdEl.textContent = "Error";
            }
        };

        // Event listeners
        startBtn.addEventListener('click', startGame);

        submitBtn.addEventListener('click', () => {
            checkAnswer();
        });

        saveUsernameBtn.addEventListener('click', async () => {
            const newUsername = usernameInput.value.trim();
            if (newUsername) {
                username = newUsername;
                try {
                    const userDocRef = doc(db, `artifacts/${appId}/users/${userId}/profile`, 'data');
                    await setDoc(userDocRef, { username: username });
                    feedbackEl.textContent = `Username saved!`;
                    feedbackEl.className = 'correct text-lg font-semibold mt-4 text-center h-8';
                } catch(e) {
                    console.error("Error saving username: ", e);
                    feedbackEl.textContent = `Error saving username.`;
                    feedbackEl.className = 'incorrect text-lg font-semibold mt-4 text-center h-8';
                }
            } else {
                feedbackEl.textContent = "Username cannot be empty.";
                feedbackEl.className = 'incorrect text-lg font-semibold mt-4 text-center h-8';
            }
        });

        // Allow pressing Enter to submit
        answerInput.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') {
                e.preventDefault();
                checkAnswer();
            }
        });
    </script>
</body>
</html>
