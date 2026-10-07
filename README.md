# Offline-Paket – SAP FICO Chatbot

Offline-Installationspaket für PCs, auf denen das Firmennetz den Download des Sprachmodells abbricht
(`wsarecv: Eine vorhandene Verbindung wurde vom Remotehost geschlossen`).

Das Paket ist das Ergebnis von `Offline-Paket erstellen.bat` aus dem SAP-FICO-Chatbot-Ordner und enthält:

| Inhalt | Beschreibung |
|---|---|
| Sprachmodell | `qwen2.5:7b` (Ollama), der große Block in 5 Teilen zu je max. 1 GB |
| Such-Modell | `paraphrase-multilingual-MiniLM-L12-v2` |
| Python-Pakete | 108 Pakete, gebaut für **Python 3.13** (Windows) |

Das Bild-Modell `qwen2.5vl:7b` ist nicht enthalten.

## Download

Alles liegt im Bereich **[Releases](../../releases/latest)** (Dateien über 100 MB können nicht direkt im Repo liegen).
Es werden **6 Dateien** gebraucht:

- `Offline-Paket-Basis.zip` (ca. 700 MB)
- `sha256-2bada8a7450677000f678be90653b85d364de7db25eb5ea54136ada5f3933730.part001` bis `.part005`

## Installation auf dem Ziel-PC

1. `Offline-Paket-Basis.zip` in den Chatbot-Ordner entpacken, direkt neben `Installieren.bat`.
   Es entsteht der Ordner `Offline-Paket`.
2. Die 5 `.part`-Dateien in `Offline-Paket\ollama\blobs\` legen, also in denselben Ordner wie die kleinen `sha256-…`-Dateien.
3. `Installieren.bat` starten. Der Installer setzt die Teile zusammen, prüft die SHA256-Summe und lädt nichts mehr aus dem Internet.
4. Danach kann der Ordner `Offline-Paket` gelöscht werden.

Ordnerstruktur vor dem Start von `Installieren.bat`:

```
Chatbot-Ordner\
├── Installieren.bat
└── Offline-Paket\
    ├── embedding\paraphrase-multilingual-MiniLM-L12-v2\...
    ├── wheels\...
    └── ollama\
        ├── manifests\registry.ollama.ai\library\qwen2.5\7b
        └── blobs\
            ├── sha256-2bada8a7…3730.part001 … .part005
            └── sha256-…  (4 kleine Dateien)
```

## Voraussetzungen

- Windows mit **Python 3.13** (die Pakete passen nur zu dieser Version)
- [Ollama](https://ollama.com) installiert

## Lizenz der Modelle

Qwen2.5 (Alibaba Cloud) steht unter Apache 2.0, das Such-Modell unter Apache 2.0 (sentence-transformers).
