<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Placar Beach Tennis - Controle</title>
    <style>
        body {
            font-family: sans-serif;
            margin: 20px;
            background-color: #f0f0f0;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .control-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
            width: 500px;
            margin-bottom: 20px;
        }

        .control-group {
            margin-bottom: 15px;
        }

        .control-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .control-group input[type="text"],
        .control-group button {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 3px;
            width: 100%;
            box-sizing: border-box;
            font-size: 16px;
        }

        .control-group button {
            background-color: #007bff;
            color: white;
            cursor: pointer;
            border: none;
            transition: background-color 0.3s ease;
        }

        .control-group button:hover {
            background-color: #0056b3;
        }

        .points-control {
            display: flex;
            gap: 10px;
            margin-top: 5px;
        }

        .points-control button {
            flex: 1;
        }

        .timer-control {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .timer-control button {
            flex: 1;
        }

        .tiebreak-control {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .tiebreak-control button {
            flex: 1;
            background-color: #28a745;
        }

        .tiebreak-display {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
        }

        .tiebreak-display span {
            font-weight: bold;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <div class="control-container">
        <div class="control-group">
            <label for="team1-name-input">Nome Dupla 1:</label>
            <input type="text" id="team1-name-input" value="MIRELLA / VANESSA">
            <button onclick="sendMessage({ type: 'name', team: 1, value: document.getElementById('team1-name-input').value })">Atualizar Nome 1</button>
        </div>
        <div class="control-group">
            <label for="team2-name-input">Nome Dupla 2:</label>
            <input type="text" id="team2-name-input" value="ANNA / VALÉRIA">
            <button onclick="sendMessage({ type: 'name', team: 2, value: document.getElementById('team2-name-input').value })">Atualizar Nome 2</button>
        </div>
        <div class="control-group">
            <label for="feminino-text-input">Texto Superior:</label>
            <input type="text" id="feminino-text-input" value="FEMININO D">
            <button onclick="sendMessage({ type: 'topText', value: document.getElementById('feminino-text-input').value })">Atualizar Texto Superior</button>
        </div>
        <div class="control-group">
            <label for="circuito-text-input">Texto Inferior:</label>
            <input type="text" id="circuito-text-input" value="CIRCUITO ARENA BEACH - FASE DE GRUPO">
            <button onclick="sendMessage({ type: 'bottomText', value: document.getElementById('circuito-text-input').value })">Atualizar Texto Inferior</button>
        </div>
    </div>

    <div class="points-container control-container">
        <h2>Pontuação</h2>
        <div class="control-group">
            <label>Pontuação Dupla 1:</label>
            <div class="points-control">
                <button onclick="sendMessage({ type: 'points', team: 1, value: 0 })">0</button>
                <button onclick="sendMessage({ type: 'points', team: 1, value: 15 })">15</button>
                <button onclick="sendMessage({ type: 'points', team: 1, value: 30 })">30</button>
                <button onclick="sendMessage({ type: 'points', team: 1, value: 40 })">40</button>
            </div>
        </div>
        <div class="control-group">
            <label>Pontuação Dupla 2:</label>
            <div class="points-control">
                <button onclick="sendMessage({ type: 'points', team: 2, value: 0 })">0</button>
                <button onclick="sendMessage({ type: 'points', team: 2, value: 15 })">15</button>
                <button onclick="sendMessage({ type: 'points', team: 2, value: 30 })">30</button>
                <button onclick="sendMessage({ type: 'points', team: 2, value: 40 })">40</button>
            </div>
        </div>
        <div class="control-group">
            <label>Sets Dupla 1:</label>
            <div class="points-control">
                <button onclick="sendMessage({ type: 'sets', team: 1, change: 1 })">+ Set</button>
                <button onclick="sendMessage({ type: 'sets', team: 1, change: -1 })">- Set</button>
            </div>
        </div>
        <div class="control-group">
            <label>Sets Dupla 2:</label>
            <div class="points-control">
                <button onclick="sendMessage({ type: 'sets', team: 2, change: 1 })">+ Set</button>
                <button onclick="sendMessage({ type: 'sets', team: 2, change: -1 })">- Set</button>
            </div>
        </div>
    </div>

    <div class="control-container">
        <h2>Tiebreak</h2>
        <div class="control-group">
            <label>Pontuação Tiebreak Dupla 1:</label>
            <div class="tiebreak-control">
                <button onclick="sendMessage({ type: 'tiebreak', team: 1, change: 1 })">+ Ponto TB</button>
                <button onclick="sendMessage({ type: 'tiebreak', team: 1, change: -1 })">- Ponto TB</button>
            </div>
        </div>
        <div class="control-group">
            <label>Pontuação Tiebreak Dupla 2:</label>
            <div class="tiebreak-control">
                <button onclick="sendMessage({ type: 'tiebreak', team: 2, change: 1 })">+ Ponto TB</button>
                <button onclick="sendMessage({ type: 'tiebreak', team: 2, change: -1 })">- Ponto TB</button>
            </div>
        </div>
    </div>

    <div class="control-container">
        <h2>Controles Gerais</h2>
        <div class="control-group timer-control">
            <button onclick="sendMessage({ action: 'startTimer' })" class="success">Iniciar Cronômetro</button>
            <button onclick="sendMessage({ action: 'stopTimer' })" class="danger">Zerar Cronômetro</button>
        </div>
        <div class="control-group">
            <label>Controle de Saque:</label>
            <div class="points-control">
                <button onclick="sendMessage({ type: 'serving', team: 1 })">Dupla 1 Sacando</button>
                <button onclick="sendMessage({ type: 'serving', team: 2 })">Dupla 2 Sacando</button>
            </div>
        </div>
        <div class="control-group points-control">
            <button onclick="sendMessage({ action: 'resetGamePoints' })">Zerar Pontos Game</button>
            <button onclick="sendMessage({ action: 'resetScore' })" class="danger">Zerar Placar Geral</button>
        </div>
    </div>

    <script>
        const channel = new BroadcastChannel('beachTennisScore');

        function sendMessage(data) {
            channel.postMessage(data);
        }
    </script>
</body>
</html>
