You are an expert web developer. Build a fully functional single-page web application called "Shift Calendar" based on the exact input format and requirements below.

---

### SHIFT DEFINITIONS (FIXED — hardcode these)

| Code | Label         | Time            |
|------|---------------|-----------------|
| P    | Pagi          | 07.00 – 14.00   |
| MD   | Middle Day    | 10.00 – 17.00   |
| S    | Siang/Sore    | 14.00 – 21.00   |
| M    | Malam         | 21.00 – 07.00   |
| L    | Libur / Off   | —               |

Each shift code must always render with its own distinct color:
- P  → sky blue (#4FC3F7)
- MD → amber/orange (#FFB74D)
- S  → coral/salmon (#FF8A65)
- M  → deep navy/indigo (#5C6BC0)
- L  → light gray (#B0BEC5) with strikethrough or "OFF" label

---

### INPUT FORMAT

The user pastes data copied from Excel. The table structure is:

- Row 1: Empty cell | dates (numbers only, e.g. 21, 22, 23, 24...)
- Row 2: Empty cell | day names in Indonesian (SENIN, SELASA, RABU, KAMIS, JUMAT, SABTU, MINGGU)
- Row 3+: Employee name | shift codes per date

Example input (tab-separated, as copied from Excel):
	21	22	23	24	25
	KAMIS	JUMAT	SABTU	MINGGU	SENIN
Fida		MD	MD	P	L	P
Latifah		M	M	L	L	P
Talitha		P	P	S	S	MD
Amal		S	S	M	M	S
AYU E		L	L	P	P	M

- Columns highlighted red in Excel = MINGGU (Sunday) — the app should auto-detect MINGGU columns and highlight them red in the calendar too.
- The schedule cycle is: date 21 of current month → date 20 of next month (one full work cycle = 30 days across 2 months).

---

### CORE FEATURES

1. **Input & Parsing**
   - Large textarea for pasting Excel data (tab-separated)
   - Parse employee names from column 0
   - Parse dates from row 0, day names from row 1
   - Parse shift codes from row 2 onward
   - "Parse Data" button triggers rendering

2. **Name Filter**
   - After parsing, show all detected employee names as clickable filter chips
   - User selects one or more names to display on the calendar
   - Default: show all names

3. **Calendar Grid View**
   - Display as a horizontal date-based grid (not a traditional month grid)
   - Columns = dates (21, 22, 23... 20)
   - Rows = selected employee names
   - Each cell shows the shift code + time label on hover/tap
   - MINGGU columns are highlighted with red column header (#E53935)
   - Cells are colored by shift type (see color map above)

4. **Legend**
   - Show color legend: P / MD / S / M / L with their colors and time ranges

5. **HD JPG Export**
   - Button: "⬇ Download Kalender HD"
   - Export using html2canvas (CDN)
   - Output: 1080 × 1920 px JPG (portrait, phone wallpaper size)
   - The exported image must be clean, crisp, and readable on a phone screen
   - Scale the calendar container to fit within 1080×1920 properly
   - Include: title "Jadwal Shift [Bulan]", the grid, and the legend

---

### TECH REQUIREMENTS

- Single .html file — no build tools, no frameworks
- html2canvas via CDN for export
- Google Fonts: "Poppins"
- Mobile-first responsive layout
- Works fully offline after initial load (except fonts CDN)

---

### UI DESIGN DIRECTION

- Clean white card on a soft neutral background
- Bold, colorful shift chips in each cell
- Employee names on the left, bold
- Date headers on top with day name below
- Sunday columns have red header background
- Export button is prominent (full width, dark color)
- The downloaded image should look like a beautiful, shareable schedule card

---

Build the complete, working single-file application now. Include all parsing logic, rendering, filtering, and export. Do not use placeholder or stub code — everything must work end-to-end.