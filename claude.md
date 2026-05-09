# CLAUDE.md – Personlig blogg

## Om bloggen

En personlig blogg om det opplyste liv. Innleggene spenner over filosofi, musikk,
teknologi, foto og andre temaer forfatteren er opptatt av. Tonen er reflektert,
varm og intellektuelt nysgjerrig – ikke akademisk eller distansert.

## Stack

- **Astro** (statisk site generator)
- **Markdown** med YAML frontmatter for hvert innlegg
- **GitHub Actions** for automatisk deploy ved push til `main`
- **GitHub Pages** for hosting
- Ingen CMS, ingen database, ingen server

## Prosjektstruktur

```
/
├── src/
│   ├── content/
│   │   └── posts/          ← Alle blogginnlegg som .md-filer
│   ├── layouts/
│   │   ├── Base.astro      ← HTML-skjelett, fonter, globale stiler
│   │   └── Post.astro      ← Layout for enkeltinnlegg
│   └── pages/
│       ├── index.astro     ← Forsiden (liste over innlegg)
│       ├── om-meg.astro    ← Om meg-side
│       └── tags/
│           └── [tag].astro ← Innlegg filtrert per tag
├── public/                 ← Statiske filer (favicon, bilder)
├── .github/
│   └── workflows/
│       └── deploy.yml      ← GitHub Actions deploy til Pages
└── CLAUDE.md
```

## Frontmatter-format

Hvert innlegg bruker dette formatet:

```yaml
---
title: "Tittelen på innlegget"
date: 2026-05-09
description: "En kort, lesbar beskrivelse (brukes i listeoversikten)"
tags: ["filosofi", "musikk"]
draft: false
---
```

- `draft: true` publiserer ikke innlegget
- `tags` er en liste – bruk konsistente, lowercase tag-navn

## Design & Mood

**Overordnet følelse:** Rolig, varm og litterær. Som å lese en gjennomtenkt bok
ved en skrivebordslampe. Maskulint jordfargepallett. Ingenting skal skrike.

**Lesbarhet trumfer alt:**
- Maks tekstbredde ~68 tegn per linje (ca. `68ch`)
- Linjehøyde minst `1.75` for brødtekst
- God vertikal rytme mellom seksjoner og avsnitt

**Typografi:**
- Brødtekst: **Lora** eller **Merriweather** (serif, Google Fonts)
- Overskrifter: samme serif-familie, ikke for stor størrelsesforskjell
- Kode: **JetBrains Mono** eller **Fira Code**
- Ingen sans-serif i innholdssoner

**Fargepalett (CSS-variabler):**
```css
--color-bg:       #f5f0e8;   /* varm off-white, papir */
--color-surface:  #ede8dc;   /* litt mørkere flate */
--color-text:     #2c2416;   /* varm nesten-svart */
--color-muted:    #7a6e5f;   /* dempet tekst, metadata */
--color-accent:   #8b5e3c;   /* varm brun, lenker og aksentdetaljer */
--color-border:   #d4cdc0;   /* diskrete skillelinjer */
```

**UI-prinsipper:**
- Ingen animasjoner eller overraskelser – ro er en feature
- Ingen sidepanel, ingen widgets, ingenting konkurrerer med teksten
- Header er enkel: bloggnavn til venstre, navigasjon til høyre
- Footer er minimal: bare navn og årstall
- Mobil skal leses like komfortabelt som desktop
- Bilder i innlegg får full tekstbredde, ingen fancy rammer

## Brukerhistorier

### Forfatter

- Som forfatter vil jeg opprette et nytt innlegg ved å lage en `.md`-fil i
  `src/content/posts/` med riktig frontmatter
- Som forfatter vil jeg sette `draft: true` for å skjule et innlegg fra publisering
- Som forfatter vil jeg pushe til `main` og se bloggen live på GitHub Pages
  automatisk, uten manuelle steg

### Leser

- Som leser vil jeg se alle publiserte innlegg på forsiden, sortert med nyeste først
- Som leser vil jeg se tittel, dato og beskrivelse for hvert innlegg i listen
- Som leser vil jeg klikke meg inn på et innlegg og lese det i en behagelig,
  fokusert layout
- Som leser vil jeg se hvilke tags et innlegg har, og klikke på en tag for å se
  andre innlegg med samme tag
- Som leser vil jeg finne en "Om meg"-side som forteller litt om forfatteren

## Prioritert backlog

1. Astro-prosjekt med GitHub Actions deploy til Pages
2. Forsidevisning med innleggsliste
3. Enkeltinnlegg-layout med god typografi
4. Tags-system med filtreringsside
5. Om meg-side

## Regler for Claude Code

- Skriv all kode på engelsk (variabelnavn, kommentarer, filnavn)
- Innholdseksempler og UI-tekst kan være på norsk
- Hold komponentene enkle – unngå unødvendig abstraksjon
- Ikke installer avhengigheter uten å begrunne det
- Spør før du gjør store strukturelle endringer
- Kjør `astro check` etter TypeScript-relevante endringer