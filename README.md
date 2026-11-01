# PsychEvidenz

Statische Web-App mit Fachinformationen zu Psychiatrie, Psychotherapie und Kinder- und Jugendpsychiatrie (KJP) – nur zur privaten Information von Fachpersonal. Live über GitHub Pages, ohne Konto nutzbar.

- **Neuigkeiten:** jeden Montag automatisch eine neue Ausgabe mit ausführlichen Besprechungen aktueller Studien
- **Wissensblog:** vertiefende Übersichten zu Krankheitsbildern, Pharmakotherapie und Leitlinien
- **Merkliste, Lesestatus, Hell-/Dunkelmodus:** pro Person, nur im eigenen Browser gespeichert (kein Konto, kein Tracking)

Jeder Beitrag nennt seine Quellen (Zitation, DOI, Link).

## Aufbau

```
index.html          die komplette App (HTML, CSS, JS in einer Datei)
posts/index.json    Liste aller Beitrags-IDs, neueste zuerst: {"posts": ["id-1", "id-2", …]}
posts/<id>.json     ein Beitrag pro Datei
.nojekyll           verhindert Jekyll-Verarbeitung durch GitHub Pages
```

## Neuen Beitrag hinzufügen

1. Datei `posts/<id>.json` anlegen (`<id>`: Kleinbuchstaben, Ziffern, Bindestriche).
2. Die ID vorne in `posts/index.json` eintragen.
3. Commit auf `main` – GitHub Pages veröffentlicht automatisch.

### Format eines Beitrags

```json
{
  "id": "beispiel-studie-2026",
  "section": "news",
  "issue": "2026-11-02",
  "order": 1,
  "areas": ["Psychiatrie", "Pharmakotherapie"],
  "tags": ["Wirkstoff", "Diagnose"],
  "readMinutes": 8,
  "title": "Titel",
  "subtitle": "Unterzeile",
  "summary": "Kurzfassung für die Übersichtskarte",
  "facts": [{"label": "Journal", "value": "JAMA Psychiatry (2026)"}],
  "keyPoints": ["Kernaussage mit **Fettdruck**"],
  "body": "## Abschnitt\nAbsatz …\n\n- Aufzählung",
  "practice": "Einordnung für die Praxis",
  "sources": [{"citation": "Autoren. Titel. Journal. Jahr;Band:Seiten.", "doi": "10.xxxx/…", "url": "https://…"}]
}
```

- `section`: `news` (Neuigkeiten) oder `wissen` (Wissensblog)
- `issue`: Datum der Ausgabe (JJJJ-MM-TT); Neuigkeiten werden danach gruppiert
- `order`: Reihenfolge innerhalb einer Ausgabe (Wissensbeiträge ab 10)
- `areas`: Teilmenge von `Psychiatrie`, `Psychotherapie`, `KJP`, `Pharmakotherapie`
- `body`: einfaches Markdown (`##`, `###`, `- `, `**fett**`, Leerzeile = neuer Absatz), kein HTML

## Hinweis

Die Beiträge fassen veröffentlichte Literatur zusammen und ersetzen weder Fachinformation, Leitlinien noch die individuelle ärztliche Entscheidung.
