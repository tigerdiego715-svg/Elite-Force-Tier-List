<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Force Member Ranking</title>
    <style>
/* Stile Generale del Corpo (Body) */
body {
    margin: 0;
    font-family: Arial, sans-serif;
    color: white; 
    min-height: 100vh; 
    display: flex;
    justify-content: center; 
    align-items: flex-start; 
    padding: 20px;
    
    /* CONFIGURAZIONE SFONDO: ASSICURATI CHE IL FILE SIA NELLA STESSA CARTELLA! */
    /* Ho usato il nome che hai fornito l'ultima volta. Se non funziona, rinominalo come suggerito (es. 'sfondo.jpg') */
    background-image: url('Pelican party team.jpeg'); 
    background-size: cover; 
    background-position: center top; 
    background-attachment: fixed; 
    background-repeat: no-repeat;
}

/* Stile del contenitore principale (per centrare il contenuto) */
.container {
    width: 90%;
    max-width: 1200px; 
    background-color: rgba(0, 0, 0, 0.75); /* Sfondo scuro e semi-trasparente */
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.8);
}

/* Header e Titolo */
header {
    display: flex;
    justify-content: space-between; 
    align-items: center;
    margin-bottom: 30px;
    border-bottom: 3px solid gold; 
    padding-bottom: 15px;
}

.main-title {
    font-size: 3em;
    color: gold; 
    text-shadow: 0 0 10px rgba(255, 215, 0, 0.8); 
    margin: 0;
}

/* Pulsante di Download (Ora è un Trigger per il Rendering) */
.download-button {
    text-decoration: none;
    background-color: #d4af37; 
    color: black;
    padding: 10px 20px;
    border-radius: 8px;
    font-weight: bold;
    transition: background-color 0.3s, transform 0.1s;
    cursor: pointer; /* Aggiunto cursore per indicare che è cliccabile */
    display: flex; 
    align-items: center; 
    gap: 8px; 
}

.download-button:hover {
    background-color: #ffcc00; 
    transform: scale(1.05);
}

/* Stile per l'immagine/icona all'interno del pulsante */
.download-icon {
    width: 25px; 
    height: 25px;
    object-fit: cover; 
    border: 1px solid black; 
}


/* Struttura della Tier List */
.tier-list {
    border: 3px solid #d4af37; 
    border-radius: 5px;
    overflow: hidden; 
}

.tier-row {
    display: flex;
    border-bottom: 1px solid #555; 
}

.tier-row:last-child {
    border-bottom: none; 
}

/* Etichetta della Tier */
.tier-label {
    width: 100px;
    padding: 15px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2em;
    font-weight: bold;
    color: black;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
    border-right: 3px solid #d4af37; 
}

/* Sezione dei Giocatori */
.tier-players {
    flex-grow: 1; 
    padding: 15px;
    display: flex;
    flex-wrap: wrap; 
    gap: 15px; 
    align-items: center;
    min-height: 50px; /* Altezza minima per facilitare il drop nelle righe vuote */
}

.tier-players span {
    background-color: rgba(255, 255, 255, 0.1);
    padding: 5px 10px;
    border-radius: 5px;
    font-weight: bold;
    border: 1px solid rgba(255, 255, 255, 0.2);
    white-space: nowrap; 
    cursor: move; 
}


/* COLORI SPECIFICI PER OGNI TIER */

/* TIER S - Rosso */
.tier-row.S .tier-label { background-color: #E60000; }
.tier-row.S { background-color: rgba(255, 0, 0, 0.1); }

/* TIER A - Arancione/Giallo Scuro */
.tier-row.A .tier-label { background-color: #FFA500; }
.tier-row.A { background-color: rgba(255, 165, 0, 0.1); }

/* TIER B - Giallo */
.tier-row.B .tier-label { background-color: #FFD700; }
.tier-row.B { background-color: rgba(255, 215, 0, 0.1); }

/* TIER C - Verde */
.tier-row.C .tier-label { background-color: #3CB371; }
.tier-row.C { background-color: rgba(60, 179, 113, 0.1); }

/* TIER EW - CIANO (AGGIORNATO) */
.tier-row.EW .tier-label { background-color: #00BCD4; }
.tier-row.EW { background-color: rgba(0, 188, 212, 0.1); }

/* NUOVA TIER MEMBERS - GRIGIO (AGGIORNATO) */
.tier-row.MEMBERS .tier-label { background-color: #A9A9A9; }
.tier-row.MEMBERS { background-color: rgba(169, 169, 169, 0.1); }
</style>
</head>
<body>

    <div class="container">

        <header>
            <h1 class="main-title">Elite Force Member Ranking</h1>
            
            <a href="#" id="downloadBtn" class="download-button" onclick="downloadTierList()">
                Download Tier List
                <img src="Ef logo.jpeg" alt="Logo EF Oro" class="download-icon">
            </a>
        </header>

        <main class="tier-list">
            
            <div class="tier-row S">
                <div class="tier-label">S</div>
                <div class="tier-players" id="tier-S" ondragover="allowDrop(event)" ondrop="drop(event)">
                </div>
            </div>
            
            <div class="tier-row A">
                <div class="tier-label">A</div>
                <div class="tier-players" id="tier-A" ondragover="allowDrop(event)" ondrop="drop(event)">
                </div>
            </div>

            <div class="tier-row B">
                <div class="tier-label">B</div>
                <div class="tier-players" id="tier-B" ondragover="allowDrop(event)" ondrop="drop(event)">
                </div>
            </div>

            <div class="tier-row C">
                <div class="tier-label">C</div>
                <div class="tier-players" id="tier-C" ondragover="allowDrop(event)" ondrop="drop(event)">
                </div>
            </div>
            
            <div class="tier-row EW">
                <div class="tier-label">EW</div>
                <div class="tier-players" id="tier-EW" ondragover="allowDrop(event)" ondrop="drop(event)">
                </div>
            </div>
            
            <div class="tier-row MEMBERS">
                <div class="tier-label">MEMBERS</div>
                <div class="tier-players" id="tier-MEMBERS" ondragover="allowDrop(event)" ondrop="drop(event)">
                    
                    <span id="player-1" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Diegotiger</span>
                    <span id="player-2" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Abcde</span>
                    <span id="player-3" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Lichtel</span>
                    <span id="player-4" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Fazobear</span>
                    <span id="player-5" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Hidden Assassin</span>
                    <span id="player-6" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Fanaddt</span>
                    <span id="player-7" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Zeno</span>
                    <span id="player-8" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Ghost</span>
                    <span id="player-9" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 GruvemS</span>
                    <span id="player-10" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Woafdu</span>
                    <span id="player-11" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Starsket</span>
                    <span id="player-12" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 B3</span>
                    <span id="player-13" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Ourson</span>
                    <span id="player-14" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Hyde</span>
                    <span id="player-15" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 TRN</span>
                    <span id="player-16" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Bowblitz</span>
                    <span id="player-17" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Data</span>
                    <span id="player-18" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Benji</span>
                    <span id="player-19" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Lightning</span>
                    <span id="player-20" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Phoenix</span>
                    <span id="player-21" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Aurora</span>
                    <span id="player-22" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 The Hunter</span>
                    <span id="player-23" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Wolfart</span>
                    <span id="player-24" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 IShowSlow</span>
                    <span id="player-25" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Yancy</span>
                    <span id="player-26" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Cyra</span>
                    <span id="player-27" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Artemdinius</span>
                    <span id="player-28" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Arzynx</span>
                    <span id="player-29" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 IKUN ^O^</span>
                    <span id="player-30" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Neon</span>
                    <span id="player-31" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Aloneboy</span>
                    <span id="player-32" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Fat and Juicy</span>
                    <span id="player-33" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Cinematuber</span>
                    <span id="player-34" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Sumwistle</span>
                    <span id="player-35" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Cold frost</span>
                    <span id="player-36" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Luna</span>
                    <span id="player-37" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 W</span>
                    <span id="player-38" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Glockkier</span>
                    <span id="player-39" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Destroyer</span>
                    <span id="player-40" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Huslung</span>
                    <span id="player-41" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 Vash</span>
                    <span id="player-42" class="player-item" draggable="true" ondragstart="drag(event)">É𝓕 J4x</span>
                </div>
            </div>

 </main>
    </div>

    <script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>

    <script>
// =========================================================================
// FUNZIONI DRAG AND DROP (INVARIANTI)
// =========================================================================

function allowDrop(event) {
    event.preventDefault(); 
}

function drag(event) {
    event.dataTransfer.setData("text", event.target.id);
}

function drop(event) {
    event.preventDefault();
    var data = event.dataTransfer.getData("text");
    var draggableElement = document.getElementById(data);
    var dropTarget = event.target.closest('.tier-players');
    
    if (!dropTarget) {
        var tierRow = event.target.closest('.tier-row');
        if (tierRow) {
            dropTarget = tierRow.querySelector('.tier-players');
        }
    }
    
    if (dropTarget) {
        dropTarget.appendChild(draggableElement);
    }
}

// =========================================================================
// FUNZIONE DI DOWNLOAD (RENDERING)
// =========================================================================

function downloadTierList() {
    // 1. Seleziona la parte della pagina da catturare (l'intera Tier List)
    // Selezioniamo il ".container" per includere anche il titolo/header!
    const tierListElement = document.querySelector('.container');
    
    // 2. Converto l'elemento HTML in un "canvas" (un'area grafica)
    html2canvas(tierListElement, {
        // Opzione per escludere il pulsante di download dall'immagine finale
        ignoreElements: (element) => element.classList.contains('download-button'),
        // Aumenta la risoluzione per una migliore qualità del testo
        scale: 2 
    }).then(canvas => {
        // 3. Converto il canvas in un formato dati immagine PNG
        const imageURL = canvas.toDataURL('image/png');
        
        // 4. Creo un link temporaneo per il download
        const a = document.createElement('a');
        a.href = imageURL;
        a.download = 'Elite_Force_Tier_List.png'; 
        
        // 5. Avvio il download simulando un clic e poi pulisco
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
    });
}
    </script>

</body>
</html>
