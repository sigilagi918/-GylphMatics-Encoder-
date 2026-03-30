GlyphMatics • SigilAGI Agent

Universal File Transport via Braille Unicode Steganography

[![Version](https://img.shields.io/badge/version-1.7-emerald)]()
[![License](https://img.shields.io/badge/license-MIT-blue)]()
[![Compression](https://img.shields.io/badge/zlib-deflate--raw-cyan)]()

What is this?

GlyphMatics is a browser-based steganographic file encoding system that transforms any file or folder into transportable text sigils using Braille Unicode characters (U+2800-U+28FF). It combines zlib compression , TAR archiving, and visual glyph rendering to enable file transport through text-only channels—email, chat, QR codes, or even printed paper.

Core Capabilities

Feature	Status	Technology	
Any File Type	✅	Binary-safe byte→Braille mapping	
Folder Preservation	✅	USTAR TAR format with metadata	
Compression	✅	`deflate-raw` via CompressionStream API	
Visual Verification	✅	Canvas-based glyph emulator	
Python Execution	✅	Pyodide WASM runtime	
Round-trip Fidelity	✅	Lossless byte-perfect reconstruction	

How It Works

```
┌─────────────┐    ┌──────────┐    ┌──────────┐    ┌─────────────┐
│   Files/    │───→│   TAR    │───→│  zlib    │───→│   Braille   │
│   Folders   │    │ Archive  │    │compress  │    │  Unicode    │
└─────────────┘    └──────────┘    └──────────┘    └─────────────┘
                                                         │
                              Transport via:             ↓
                         • Email/Slack/Discord    ┌─────────────┐
                         • Paste bins             │  U+2800+byte │
                         • QR codes               │  (256 chars) │
                         • Printed text           └─────────────┘
```

The Sigil Format

```
GLYPH_SIGIL_v1.7:{compressed_length}:{braille_glyphs}
```

Each byte (0-255) maps directly to a Braille Unicode character (U+2800-U+28FF), providing 1:1 encoding efficiency with zero ambiguity .

Glyph Runtime Emulator (v1.7)

The built-in emulator provides actual image testing capabilities:

- 4 Render Modes: Braille dots, grid lines, heatmap, binary visualization
- Pattern Analysis: Hex dumps, frequency analysis, entropy calculation
- Verification Suite: Round-trip testing, byte coverage analysis
- Export: PNG generation for physical sigil creation

Use Cases

- Secure Transport: Move files through text-only channels (corporate firewalls, sanitized environments)
- Air-gapped Systems: Transfer data via printable, human-transcribable glyphs
- Digital Preservation: Store binary data in plain text formats guaranteed to survive encoding changes
- Steganography: Hide files in plain sight as "decorative" Braille patterns

Technical Stack

- Compression: `CompressionStream('deflate-raw')` — raw DEFLATE without headers  
- Archive: Pure-JS USTAR TAR implementation (POSIX compliant)
- Encoding: Braille Unicode block (256 code points, 0x2800-0x28FF)
- Execution: Pyodide v0.26.1 (WASM Python runtime)
- Rendering: HTML5 Canvas API with pixel-perfect scaling

Limitations

Constraint	Detail	
Browser Storage	500MB-2GB depending on device	
Native Execution	Requires external launcher (browser security sandbox)	
Non-Python Code	WASM-only execution in-browser	

Installation

No build required. Single HTML file—open in any modern browser:

```bash
git clone https://github.com/918technologies/glyphmatics.git
cd glyphmatics
# Open glyphmatics_v1.7_emulator.html in browser
```

Or use directly via GitHub Pages: `https://918technologies.github.io/glyphmatics/`

Version History

Version	Features	
v1.5	Binary file support, drag-and-drop	
v1.6	Folder bundling, TAR archives, metadata preservation	
v1.7	Glyph Runtime Emulator, canvas rendering, pattern analysis	

License

MIT © 918 Technologies / Matthew Blake Ward

---

Status: Production-ready for text-based file transport. Not for illegal use. Follow responsible disclosure
