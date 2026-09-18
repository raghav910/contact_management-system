# Contact Manager (CLI)

A simple command-line contact manager built while learning Python fundamentals —
classes & inheritance, file I/O, JSON, comprehensions, and modules.

## Features

- Add regular contacts (name, phone) or work contacts (name, phone, company)
- List all saved contacts
- Search by name
- Delete by name
- Contacts persist between runs via a local `contacts.json` file

## Project structure

```
contact-manager/
├── contact.py     # Contact and WorkContact classes
├── manager.py     # add/list/search/delete/save/load functions
├── main.py        # menu-driven entry point
└── contacts.json  # created automatically on first save
```

`WorkContact` inherits from `Contact` and adds a `company` field, overriding
`display()` and `to_dict()`. When contacts are loaded back from JSON, a
`"type"` field in each record decides whether to rebuild a `Contact` or a
`WorkContact`.

## How to run

```bash
cd contact-manager
python main.py
```

Follow the on-screen menu (1–6) to add, list, search, delete, or save & quit.

## What I learned building this

The trickiest part wasn't any single concept — it was keeping multiple
functions consistent about *what* they were storing. My first attempts mixed
storing plain dicts in some functions and expecting full objects in others,
which caused `AttributeError`s that were confusing until I traced through
exactly what type each variable held at each step. The fix was deciding once
(store objects, convert to dicts only when saving to JSON) and keeping every
function consistent with that choice.

## Possible next steps

- Add input validation (e.g., phone number format)
- Add an "edit contact" option
- Split contacts across multiple JSON files or move to a real database
