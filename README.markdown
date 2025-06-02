# r00tM1ndLab - Multifunctional Vulnerability Practice Lab

## Overview
**r00tM1ndLab**, created by **r00tM1nd > Abdullah**, is a professional, web-based lab for practicing web vulnerability exploitation. It features six vulnerability types (XSS, SQL Injection, CSRF, File Inclusion, Command Injection, Broken Authentication), each with 20 levels of increasing difficulty (120 total challenges). The tool has a sleek, dark-themed interface with Tailwind CSS, level progression tracking, and "Level Complete" popups. It runs on Termux, Windows, Linux, and is optimized for GitHub hosting.

## Features
- 6 vulnerability categories, each with 20 levels (120 challenges).
- Professional, responsive interface with a dark theme.
- Level progression: Complete a level to unlock the next.
- "Level Complete" popup with a button to proceed.
- Cross-platform: Runs on any system with Python 3.x.
- Extensible: Easily add new vulnerability types.
- Created by **r00tM1nd > Abdullah**.

## Requirements
- Python 3.x
- Flask (`pip install flask`)
- SQLite (included with Python)

## Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/r00tm1ndlab.git
   cd r00tm1ndlab
   ```
2. Install dependencies:
   ```bash
   pip install flask
   ```
3. Run the server:
   ```bash
   python r00tm1ndlab.py
   ```
4. Open your browser and navigate to `http://localhost:5000`.

## Usage
- Visit `http://localhost:5000` to see the vulnerability categories and levels.
- Select a category (e.g., XSS, SQLi) and complete levels by exploiting vulnerabilities.
- Success conditions (e.g., `alert('XSS')` for XSS, database error for SQLi) trigger a "Level Complete" popup.
- Levels are locked until previous ones are completed.
- Use hints provided to craft payloads.

## Vulnerability Types
1. **Cross-Site Scripting (XSS)**: Inject JavaScript payloads (e.g., `<script>alert('XSS')</script>`).
2. **SQL Injection (SQLi)**: Manipulate database queries (e.g., `admin' OR '1'='1`).
3. **Cross-Site Request Forgery (CSRF)**: Forge unauthorized requests.
4. **File Inclusion (LFI/RFI)**: Access unauthorized files or execute remote scripts.
5. **Command Injection**: Execute system commands (e.g., `127.0.0.1; whoami`).
6. **Broken Authentication**: Bypass login or session mechanisms.

## Level Overview
- **Levels 1–3**: Implemented for each vulnerability type (see code).
- **Levels 4–20**: Placeholders to extend with complex challenges (e.g., CSP bypass for XSS, blind SQLi, advanced LFI).

## Extending the Tool
To add levels or new vulnerability types:
- Edit `VULN_TEMPLATES` in `r00tm1ndlab.py` to define new challenges.
- Add routes or logic in the `/<vuln>/level/<int:level>` endpoint.
- Example new vulnerability type (e.g., SSRF):
  ```python
  'ssrf': {
      1: '''
      <h1 class="text-2xl font-bold mb-4">SSRF Level 1: Basic</h1>
      <p>Fetch URL:</p>
      <form method="GET" class="mb-4">
          <input type="text" name="url" class="bg-gray-700 text-white p-2 rounded">
          <input type="submit" value="Fetch" class="bg-green-600 p-2 rounded hover:bg-green-500">
      </form>
      <p>{{ content }}</p>
      <p class="text-gray-400">Hint: Try <code>http://localhost:5000/secret</code>.</p>
      '''
  }
  ```
- Update the `level` route to handle the new vulnerability’s logic.

## Notes
- Runs on Termux, Windows, or Linux with minimal setup.
- Host on GitHub for public access, but ensure users run in controlled environments.
- Uses cookies to track progress; clear cookies to reset.
- File Inclusion and Command Injection levels may require additional setup (e.g., file permissions) on some systems.

## License
MIT License

## Credits
Created by **r00tM1nd > Abdullah** for the cybersecurity community.