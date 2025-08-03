# Cine-blox <!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Hit Hub 🎬</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      padding: 20px;
      text-align: center;
    }

    h1 {
      color: #333;
    }

    #newBtn {
      background-color: #28a745;
      color: white;
      border: none;
      padding: 10px 20px;
      font-size: 16px;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 10px;
    }

    #formContainer {
      margin-top: 20px;
      display: none;
    }

    input {
      padding: 8px;
      margin: 5px;
      width: 80%;
      max-width: 300px;
    }

    button.add {
      background-color: #007bff;
      color: white;
      border: none;
      padding: 8px 16px;
      border-radius: 5px;
      cursor: pointer;
    }

    .videoItem {
      margin-top: 20px;
      background: white;
      padding: 10px;
      border-radius: 5px;
      box-shadow: 0 0 5px rgba(0,0,0,0.1);
    }

    iframe {
      width: 100%;
      max-width: 400px;
      height: 225px;
      border: none;
    }
  </style>
</head>
<body>

  <h1>🎬 Hit Hub</h1>
  <button id="newBtn">New</button>

  <div id="formContainer">
    <h3>Adicionar novo vídeo</h3>
    <input type="text" id="videoTitle" placeholder="Título do vídeo">
    <input type="text" id="videoURL" placeholder="URL do vídeo (YouTube)">
    <br>
    <button class="add" onclick="addVideo()">Adicionar</button>
  </div>

  <div id="videoList"></div>

  <script>
    const newBtn = document.getElementById('newBtn');
    const formContainer = document.getElementById('formContainer');
    const videoList = document.getElementById('videoList');

    newBtn.onclick = () => {
      formContainer.style.display = formContainer.style.display === 'none' ? 'block' : 'none';
    };

    function addVideo() {
      const title = document.getElementById('videoTitle').value;
      const url = document.getElementById('videoURL').value;

      if (title && url) {
        const videoItem = document.createElement('div');
        videoItem.className = 'videoItem';
        videoItem.innerHTML = `
          <h4>${title}</h4>
          <iframe src="${url}" allowfullscreen></iframe>
        `;
        videoList.appendChild(videoItem);

        // Limpar campos
        document.getElementById('videoTitle').value = '';
        document.getElementById('videoURL').value = '';
        formContainer.style.display = 'none';
      } else {
        alert('Preencha todos os campos!');
      }
    }
  </script>

</body>
</html>
