<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Magical Horizon - Sunshine Days Fan Site</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

  body {
    margin: 0; padding: 0;
    background: linear-gradient(135deg, #f7c8f0, #f5e1ff);
    font-family: 'Press Start 2P', cursive;
    color: #9c2a8e;
    user-select: none;
  }

  header {
    background: #f48fb1;
    padding: 12px;
    text-align: center;
    font-size: 1.5em;
    color: #fff;
    letter-spacing: 2px;
    border-bottom: 4px solid #e040fb;
  }

  main {
    max-width: 700px;
    margin: 12px auto 50px;
    background: #fff0ffcc;
    border: 3px dotted #9c2a8e;
    border-radius: 12px;
    padding: 20px;
  }

  nav {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 20px;
  }
  nav button {
    background: #f48fb1;
    border: 2px solid #9c2a8e;
    color: white;
    padding: 8px 14px;
    cursor: pointer;
    border-radius: 6px;
    font-size: 10px;
    transition: 0.3s;
  }
  nav button:hover {
    background: #9c2a8e;
  }

  section {
    display: none;
    animation: fadeIn 0.5s ease forwards;
  }
  section.active {
    display: block;
  }

  h2 {
    text-align: center;
    font-size: 1.4em;
    margin-bottom: 16px;
  }

  .stars-bg {
    position: fixed;
    top: 0; left: 0; width: 100%; height: 100%;
    pointer-events: none;
    z-index: -1;
    background:
      radial-gradient(circle at 10% 20%, #ff99cc 2px, transparent 3px),
      radial-gradient(circle at 30% 70%, #f48fb1 1.5px, transparent 2.5px),
      radial-gradient(circle at 80% 40%, #ff66aa 2px, transparent 3px),
      radial-gradient(circle at 60% 80%, #ffa1dc 1.5px, transparent 3px);
    background-repeat: repeat;
  }

  /* Big pixel star */
  .big-star {
    font-size: 60px;
    text-align: center;
    margin: 12px 0 20px;
    color: #ff77cc;
    filter: drop-shadow(0 0 3px #ff33aa);
  }

  /* Character card style */
  .char-card {
    border: 2px dashed #9c2a8e;
    border-radius: 14px;
    padding: 14px;
    margin: 10px auto;
    max-width: 600px;
    background: #ffe6f7cc;
    box-shadow: 0 0 8px #f48fb1aa;
  }
  .char-card h3 {
    font-size: 1.2em;
    margin: 6px 0 10px;
    color: #d4198e;
  }
  .char-card p {
    margin: 4px 0;
    font-size: 10px;
  }
  .fav-line {
    font-style: italic;
    color: #9c2a8e;
    margin: 8px 0;
    font-size: 10px;
  }
  .headcanon-list {
    font-size: 9px;
    margin-left: 12px;
  }

  /* Seasons menu */
  .season-list {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
  }
  .season-list button {
    background: #f48fb1;
    border: 2px solid #9c2a8e;
    color: white;
    cursor: pointer;
    border-radius: 8px;
    font-size: 12px;
    padding: 6px 12px;
  }
  .season-list button:hover {
    background: #9c2a8e;
  }

  /* Episode list */
  .episode-list {
    max-width: 400px;
    margin: 0 auto 24px;
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    justify-content: center;
  }
  .episode-list button {
    background: #ffb6e7;
    border: 1px solid #d4198e;
    border-radius: 6px;
    padding: 6px 10px;
    font-size: 10px;
    cursor: pointer;
  }
  .episode-list button:hover {
    background: #d4198e;
    color: white;
  }

  /* Comment box */
  #commentBox {
    margin-top: 20px;
    width: 100%;
    display: flex;
    gap: 8px;
  }
  #commentInput {
    flex-grow: 1;
    font-family: 'Press Start 2P', cursive;
    font-size: 10px;
    padding: 6px;
    border: 2px solid #9c2a8e;
    border-radius: 6px;
  }
  #commentSend {
    background: #f48fb1;
    border: none;
    color: white;
    font-family: 'Press Start 2P', cursive;
    font-size: 10px;
    padding: 6px 10px;
    cursor: pointer;
    border-radius: 6px;
    transition: 0.3s;
  }
  #commentSend:hover {
    background: #9c2a8e;
  }

  /* Comments list */
  #commentsList {
    margin-top: 12px;
    max-height: 160px;
    overflow-y: auto;
    background: #ffe6f7cc;
    padding: 10px;
    border-radius: 12px;
    border: 2px dashed #d4198e;
    font-size: 10px;
  }
  .comment {
    border-bottom: 1px dotted #9c2a8e;
    padding: 4px 0;
  }
  .comment strong {
    color: #d4198e;
  }

  /* User profile popup */
  #profilePopup {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0);
    background: #ffe6f7;
    border: 3px dashed #9c2a8e;
    padding: 20px;
    width: 280px;
    border-radius: 14px;
    box-shadow: 0 0 10px #d4198eaa;
    color: #9c2a8e;
    font-size: 11px;
    text-align: center;
    z-index: 9999;
    transition: transform 0.3s ease;
  }
  #profilePopup.active {
    transform: translate(-50%, -50%) scale(1);
  }
  #profilePopup button {
    margin-top: 14px;
    background: #f48fb1;
    border: none;
    padding: 6px 12px;
    color: white;
    font-family: 'Press Start 2P', cursive;
    font-size: 11px;
    border-radius: 6px;
    cursor: pointer;
  }
  #profilePopup button:hover {
    background: #9c2a8e;
  }

  /* Translate button */
  #translateBtn {
    position: fixed;
    top: 10px;
    right: 10px;
    background: #f48fb1;
    border: none;
    color: white;
    padding: 8px 14px;
    border-radius: 8px;
    cursor: pointer;
    font-family: 'Press Start 2P', cursive;
    font-size: 10px;
    z-index: 10000;
    transition: 0.3s;
  }
  #translateBtn:hover {
    background: #9c2a8e;
  }

  /* Responsive */
  @media(max-width: 420px){
    main {
      margin: 8px 8px 40px;
      padding: 12px;
    }
    nav button, .season-list button, .episode-list button {
      font-size: 9px;
      padding: 5px 8px;
    }
  }

  /* Animations */
  @keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
  }
</style>
</head>
<body>

<div class="stars-bg"></div>

<header>
  ✨ Magical Horizon ✨ <br/>
  <small>Sunshine Days Fan Site</small>
</header>

<button id="translateBtn">🌐 Translate</button>

<main>
  <nav id="mainNav">
    <button data-target="home">Home</button>
    <button data-target="episodes">Episodes</button>
    <button data-target="characters">Characters</button>
    <button data-target="lore">Lore</button>
    <button data-target="chat">Chat</button>
  </nav>

  <!-- Home -->
  <section id="home" class="active">
    <div class="big-star">★</div>
    <h2>Welcome to Magical Horizon!</h2>
    <p style="text-align:center; font-size:10px; color:#9c2a8e; max-width:400px; margin:auto;">
      This fan site is dedicated to <strong>Sunshine Days</strong>, the magical girl anime created by Himari Kurosawa.<br/>
      The series had 4 seasons with 12 episodes each.<br/>
      Note: The original streaming site closed in late 2014. But the magic lives on here!<br/><br/>
      Click the tabs above to explore episodes, characters, lore, and chat with fellow fans!
    </p>
  </section>

  <!-- Episodes -->
  <section id="episodes">
    <h2>Seasons & Episodes</h2>
    <div class="season-list" id="seasonButtons"></div>
    <div class="episode-list" id="episodeButtons"></div>
    <div id="episodeMessage" style="text-align:center; font-size: 12px; color: #9c2a8e; margin-top: 12px;"></div>
  </section>

  <!-- Characters -->
  <section id="characters">
    <h2>Main Characters</h2>
    <div class="char-card">
      <h3>Sora</h3>
      <p><strong>Age:</strong> 15</p>
      <p><strong>Role:</strong> Protagonist, magical boy</p>
      <p><strong>Favorite Magic:</strong> Sunbeam Light</p>
      <p class="fav-line">"My mission is to protect hope!"</p>
    </div>
    <div class="char-card">
      <h3>Momoka</h3>
      <p><strong>Age:</strong> 16</p>
      <p><strong>Role:</strong> Magical girl, Sora’s best friend</p>
      <p><strong>Favorite Magic:</strong> Blossom Shield</p>
      <p class="fav-line">"Together, nothing can stop us!"</p>
    </div>
    <div class="char-card">
      <h3>Goddess of the Forest</h3>
      <p><strong>Age:</strong> Timeless</p>
      <p><strong>Role:</strong> Guardian spirit</p>
      <p><strong>Favorite Magic:</strong> Nature’s Embrace</p>
      <p class="fav-line">"Feel the life all around you."</p>
    </div>
    <div class="char-card">
      <h3>Goddess of the Sea</h3>
      <p><strong>Age:</strong> Timeless</p>
      <p><strong>Role:</strong> Guardian spirit</p>
      <p><strong>Favorite Magic:</strong> Ocean’s Grace</p>
      <p class="fav-line">"The tides carry our destiny."</p>
    </div>
  </section>

  <!-- Lore -->
  <section id="lore">
    <h2>Lore & World</h2>
    <p style="max-width:600px; margin: 0 auto 14px; font-size: 11px;">
      <strong>Sunshine Days</strong> takes place in a world where magic is woven through everyday life. The four seasons are enchanted, each ruled by a guardian spirit who grants powers to chosen heroes.<br/><br/>
      The story follows Sora, a magical boy chosen by the Goddess of the Forest, and Momoka, his loyal magical girl friend. Together, they fight shadows trying to steal light from the world.<br/><br/>
      The city of <em>Magical Horizon</em> is their home base — a sparkling town where pastel skies meet starry nights.<br/><br/>
      Couples & ships: Sora x Momoka (bff turned lovers), Goddess of the Forest x Goddess of the Sea (eternal guardians).<br/><br/>
      The magic system is based on light, nature, and emotions, with characters growing as they unlock new abilities.
    </p>
  </section>

  <!-- Chat -->
  <section id="chat">
    <h2>Fan Chat</h2>
    <div style="max-width: 700px; margin: auto;">
      <div id="commentsList"></div>
      <div id="commentBox">
        <input type="text" id="commentInput" placeholder="Type your message here..." maxlength="120" />
        <button id="commentSend">Send</button>
      </div>
    </div>
  </section>
</main>

<!-- Profile popup -->
<div id="profilePopup">
  <p><strong>User Profile</strong></p>
  <p id="profileName"></p>
  <p id="profileStatus"></p>
  <button id="closeProfileBtn">Close</button>
</div>

<script>
  // Data
  const seasons = {
    1: "Spring 2009",
    2: "Summer 2010",
    3: "Fall 2012",
    4: "Winter 2014"
  };

  const episodesPerSeason = 12;

  // Fake users
  const fakeUsers = [
    {name:"Miyu", status:"Not available rn"},
    {name:"Kaito", status:"Not available rn"},
    {name:"Lina", status:"Not available rn"},
    {name:"Haru", status:"Not available rn"},
    {name:"Ami", status:"Not available rn"},
    {name:"Taro", status:"Not available rn"},
    {name:"Yuki", status:"Not available rn"},
    {name:"Ren", status:"Not available rn"},
    {name:"Saki", status:"Not available rn"},
    {name:"Kazu", status:"Not available rn"},
  ];

  // Show/Hide sections
  const navButtons = document.querySelectorAll('#mainNav button');
  const sections = document.querySelectorAll('main section');

  navButtons.forEach(btn => {
    btn.addEventListener('click', () => {
      const target = btn.getAttribute('data-target');
      sections.forEach(sec => {
        sec.classList.remove('active');
        if (sec.id === target) sec.classList.add('active');
      });

      if (target === 'episodes') setupSeasons();
      if (target === 'chat') loadComments();
    });
  });

  // Setup season buttons
  const seasonButtonsDiv = document.getElementById('seasonButtons');
  const episodeButtonsDiv = document.getElementById('episodeButtons');
  const episodeMsgDiv = document.getElementById('episodeMessage');

  function setupSeasons() {
    seasonButtonsDiv.innerHTML = '';
    episodeButtonsDiv.innerHTML = '';
    episodeMsgDiv.textContent = '';
    for (const s in seasons) {
      const btn = document.createElement('button');
      btn.textContent = "Season " + s + " (" + seasons[s] + ")";
      btn.dataset.season = s;
      btn.addEventListener('click', () => showEpisodes(s));
      seasonButtonsDiv.appendChild(btn);
    }
  }

  // Show episodes for selected season
  function showEpisodes(season) {
    episodeButtonsDiv.innerHTML = '';
    episodeMsgDiv.textContent = '';
    for(let ep = 1; ep <= episodesPerSeason; ep++) {
      const btn = document.createElement('button');
      btn.textContent = "Ep " + ep;
      btn.dataset.season = season;
      btn.dataset.episode = ep;
      btn.addEventListener('click', () => episodeClick(season, ep));
      episodeButtonsDiv.appendChild(btn);
    }
  }

  // On episode click show "Uh oh, nothing here!"
  function episodeClick(season, episode) {
    episodeMsgDiv.textContent = `Uh oh, Season ${season} Episode ${episode} - Nothing here!`;
  }

  // Chat system with localStorage
  const commentInput = document.getElementById('commentInput');
  const commentSend = document.getElementById('commentSend');
  const commentsList = document.getElementById('commentsList');

  commentSend.addEventListener('click', () => {
    const msg = commentInput.value.trim();
    if (!msg) return;
    addComment('You', msg);
    commentInput.value = '';
  });

  commentInput.addEventListener('keydown', e => {
    if (e.key === 'Enter') commentSend.click();
  });

  function addComment(user, msg) {
    let comments = JSON.parse(localStorage.getItem('sd_comments') || '[]');
    comments.push({user, msg, time: Date.now()});
    localStorage.setItem('sd_comments', JSON.stringify(comments));
    renderComments();
  }

  function renderComments() {
    let comments = JSON.parse(localStorage.getItem('sd_comments') || '[]');
    commentsList.innerHTML = '';
    comments.forEach(c => {
      const div = document.createElement('div');
      div.className = 'comment';
      const time = new Date(c.time).toLocaleTimeString([], {hour: '2-digit', minute: '2-digit'});
      div.innerHTML = `<strong>${c.user}</strong> [${time}]: ${c.msg}`;
      commentsList.appendChild(div);
    });
    commentsList.scrollTop = commentsList.scrollHeight;
  }

  function loadComments() {
    renderComments();
  }

  // Profile popup for fake users
  let profilePopup = document.getElementById('profilePopup');
  let profileName = document.getElementById('profileName');
  let profileStatus = document.getElementById('profileStatus');
  let closeProfileBtn = document.getElementById('closeProfileBtn');

  // We'll add fake users clickable in chat for fun (weird flex but okay)
  // For demo, add clickable fake users in chat section above comments
  const chatSection = document.getElementById('chat');
  const fakeUsersDiv = document.createElement('div');
  fakeUsersDiv.style.margin = "10px auto 20px";
  fakeUsersDiv.style.textAlign = "center";
  fakeUsersDiv.style.fontSize = "10px";
  fakeUsersDiv.innerHTML = `<strong>Fake Users Online:</strong> `;
  fakeUsers.forEach(u => {
    const uSpan = document.createElement('span');
    uSpan.textContent = u.name;
    uSpan.style.color = '#d4198e';
    uSpan.style.cursor = 'pointer';
    uSpan.style.margin = '0 6px';
    uSpan.style.textDecoration = 'underline dotted';
    uSpan.addEventListener('click', () => {
      profileName.textContent = u.name;
      profileStatus.textContent = u.status;
      profilePopup.classList.add('active');
    });
    fakeUsersDiv.appendChild(uSpan);
  });
  chatSection.insertBefore(fakeUsersDiv, commentsList);

  closeProfileBtn.addEventListener('click', () => {
    profilePopup.classList.remove('active');
  });

  // Translate feature (basic manual dictionary, just a fun gag)
  const translations = {
    en: {
      "Welcome to Magical Horizon!": "Welcome to Magical Horizon!",
      "This fan site is dedicated to Sunshine Days, the magical girl anime created by Himari Kurosawa.": "This fan site is dedicated to Sunshine Days, the magical girl anime created by Himari Kurosawa.",
      "The series had 4 seasons with 12 episodes each.": "The series had 4 seasons with 12 episodes each.",
      "Note: The original streaming site closed in late 2014. But the magic lives on here!": "Note: The original streaming site closed in late 2014. But the magic lives on here!",
      "Seasons & Episodes": "Seasons & Episodes",
      "Main Characters": "Main Characters",
      "Lore & World": "Lore & World",
      "Fan Chat": "Fan Chat",
      "Uh oh, Season": "Uh oh, Season",
      "Episode": "Episode",
      "Nothing here!": "Nothing here!",
      "Fake Users Online:": "Fake Users Online:"
    },
    jp: {
      "Welcome to Magical Horizon!": "マジカルホライズンへようこそ！",
      "This fan site is dedicated to Sunshine Days, the magical girl anime created by Himari Kurosawa.": "このファンサイトは黒澤ひまりが作った魔法少女アニメ「サンシャインデイズ」に捧げられています。",
      "The series had 4 seasons with 12 episodes each.": "このシリーズは4シーズン、各12話で構成されています。",
      "Note: The original streaming site closed in late 2014. But the magic lives on here!": "注：元のストリーミングサイトは2014年末に閉鎖されました。でも魔法はここに生き続けています！",
      "Seasons & Episodes": "シーズン＆エピソード",
      "Main Characters": "主要キャラクター",
      "Lore & World": "物語＆世界観",
      "Fan Chat": "ファンチャット",
      "Uh oh, Season": "あれ？ シーズン",
      "Episode": "エピソード",
      "Nothing here!": "何もないよ！",
      "Fake Users Online:": "オンラインの偽ユーザー："
    }
  };

  const translateBtn = document.getElementById('translateBtn');
  let currentLang = 'en';
  translateBtn.addEventListener('click', () => {
    currentLang = currentLang === 'en' ? 'jp' : 'en';
    document.querySelectorAll('h2, header, main p, main small, section p, .char-card p, .fav-line, #seasonButtons button, #episodeButtons button, #mainNav button').forEach(el => {
      const txt = el.textContent;
      if (translations[currentLang][txt]) {
        el.textContent = translations[currentLang][txt];
      }
    });
  });

</script>

</body>
</html>
