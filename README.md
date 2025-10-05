<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Escrita 4.0 – Digital System</title>
<style>
  :root {
    /* Modern light theme: Clean white + Vibrant Blue */
    --bg: #f8faff;
    --panel: #ffffff;
    --card: #ffffff;
    --border: #e0e8f0;
    --light: #1a202c;
    --muted: #718096;
    --accent: #2c6be3;    /* Vibrant Blue */
    --accent-2: #1e4ea5;  /* Darker Blue */
    --shadow: rgba(44, 107, 227, 0.1);
  }
  * { box-sizing: border-box; }
  html, body {
    margin: 0; padding: 0;
    background: radial-gradient(1200px 600px at 10% -10%, rgba(44, 107, 227, 0.04), transparent),
                linear-gradient(var(--bg), #f0f3f7);
    color: var(--light);
    font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, "Apple Color Emoji", "Segoe UI Emoji";
  }
  header {
    position: sticky; top: 0; z-index: 10;
    padding: 14px 16px; border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.9);
    backdrop-filter: blur(8px);
  }
  #app { max-width: 1200px; margin: 0 auto; padding: 18px; }
  .brand { display: flex; align-items: center; gap: 12px; }
  .logo {
    width: 40px; height: 40px; border-radius: 10px;
    display: grid; place-items: center; font-weight: 800; color: #fff;
    background: linear-gradient(135deg, var(--accent), var(--accent-2));
    border: 1px solid var(--border);
    overflow: hidden;
  }
  .brand h1 { margin: 0; font-size: 18px; font-family: Inter, sans-serif; letter-spacing: .2px; }
  .sub { font-size: 12px; color: var(--muted); }
  .row { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; }
  .spacer { flex: 1; }

  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 16px;
    box-shadow: 0 10px 20px var(--shadow);
  }
  .card h2 {
    margin: 0 0 6px 0; font-size: 18px; font-family: Inter, sans-serif; font-weight: 700;
  }
  .card h2::after {
    content: ""; display: block; height: 2px; margin-top: 8px;
    background: linear-gradient(to right, transparent, var(--accent-2), transparent);
    border-radius: 2px;
  }
  .section-title { font-size: 16px; margin: 8px 0; font-family: Inter, sans-serif; }

  .muted { color: var(--muted); font-size: 13px; }
  .grid { display: grid; gap: 16px; }
  .grid.cols-2 { grid-template-columns: repeat(2, 1fr); }
  .grid.cols-3 { grid-template-columns: repeat(3, 1fr); }
  @media (max-width: 1000px) { .grid.cols-2, .grid.cols-3 { grid-template-columns: 1fr; } }

  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 8px 12px; border-radius: 10px; cursor: pointer;
    background: #fff; color: var(--light);
    border: 1px solid var(--border); text-decoration: none; font-weight: 600;
    transition: all 0.2s ease;
  }
  .btn:hover { box-shadow: 0 4px 12px var(--shadow); border-color: var(--accent); }
  .btn.primary { background: linear-gradient(180deg, var(--accent), var(--accent-2)); color: #ffffff; border: 1px solid var(--accent-2); }
  .btn.primary:hover { opacity: 0.9; }
  .btn.warn { background: #fff6e6; color: #8a5a00; border-color: #e7c888; }
  .btn.danger { background: #fff1f1; color: #8a1414; border-color: #f1c0c0; }
  .btn.small { padding: 6px 10px; font-size: 13px; border-radius: 8px; }

  .tag { padding: 2px 8px; border-radius: 999px; font-size: 12px; border: 1px solid var(--border); background: #fff; color: var(--light); }
  .tag.green { background: #f0fff4; color: #1e7943; border-color: #bcebc9; }
  .tag.blue { background: #eef6ff; color: #0a3b74; border-color: #c9def9; }
  .tag.red { background: #fff1f1; color: #8a1414; border-color: #f1c0c0; }
  .tag.warn { background: #fff9e6; color: #8a5a00; border-color: #e7c888; }

  .nav { display: flex; gap: 8px; flex-wrap: wrap; margin: 8px 0 12px; }
  .nav .tab { padding: 8px 10px; background: #fff; border: 1px solid var(--border); border-radius: 10px; color: var(--light); cursor: pointer; transition: all 0.2s ease; }
  .nav .tab.active { background: var(--accent); border-color: var(--accent-2); color: #fff; box-shadow: 0 4px 12px var(--shadow); }
  .nav .tab:not(.active):hover { border-color: var(--accent); }

  .hr { height: 1px; background: var(--border); margin: 12px 0; }
  .input, select, textarea { width: 100%; padding: 10px 12px; background: #fff; color: var(--light); border: 1px solid var(--border); border-radius: 10px; }
  .input:focus, select:focus, textarea:focus { outline: none; border-color: var(--accent); box-shadow: 0 0 0 2px var(--shadow); }

  .table-wrap { width: 100%; overflow: auto; border: 1px solid var(--border); border-radius: 12px; }
  table { width: 100%; border-collapse: collapse; min-width: 720px; }
  th, td { padding: 12px; border-bottom: 1px solid var(--border); text-align: left; font-size: 14px; }
  th { background: #f7f9fc; position: sticky; top: 0; z-index: 1; }
  tbody tr:last-child td { border-bottom: none; }
  tbody tr:hover { background: #fafcff; }

  .notice { padding: 10px 12px; border: 1px dashed var(--border); border-radius: 12px; background: #f7f9fc; color: var(--muted); font-size: 13px; }
</style>
</head>
<body>
<header>
  <div class="brand">
    <div class="logo" id="brand-logo">ES</div>
    <div>
      <h1 id="event-title-display">Escrita 4.0</h1>
      <div class="sub" id="org-name-display">Rabath Eduvalley Students' Association • Event Crew + Team Portal</div>
    </div>
    <div class="spacer"></div>
    <div id="header-session" class="row"></div>
  </div>
</header>
<div id="app"></div>

<script>
"use strict";

/* ------------------------------
   Data Store
--------------------------------*/
const Store = {
  key: "feliziaFestData.v4",
  defaults: () => ({
    meta: { createdAt: Date.now(), version: 4 },
    // **UPDATED DEFAULT EVENT INFO**
    eventInfo: { eventTitle: "Escrita 4.0", orgName: "Rabath Eduvalley Students' Association" },
    brand: { logoDataUrl: null, faviconDataUrl: null, accent: "#2c6be3", accent2: "#1e4ea5" }, // New default brand colors
    eventUser: { username: "admin", password: "felizia" },
    portalLocked: false,
    // **CLEANED CATEGORIES - 'General' only**
    categories: ["General"],
    // **CLEANED TEAMS - Empty**
    teams: [],
    competitions: [],            // {id,name,category,isGroup,teamEntryLimit,maxGroupSize?,date?,time?,locked?}
    students: [],                // {id,teamId,chestNo,name}
    entries: [],                 // {id,teamId,competitionId,entryType,memberStudentIds[],createdAt}
    attendance: [],              // {id,competitionId,entryId,present,code?,markedAt}
    results: [],                 // {id,competitionId,entryId,rankLabel,pointsAwarded,judgeNotes?,timestamp}
    adjustments: [],
    posters: { templates: [] },
    chest: { templates: [] }
  }),
  load() {
    try {
      const raw = localStorage.getItem(this.key);
      if (!raw) {
        const base = this.defaults();
        localStorage.setItem(this.key, JSON.stringify(base));
        return base;
      }
      let data = JSON.parse(raw);

      // Migration for v4 changes
      if (!data.meta || data.meta.version < 4) {
        const baseDefaults = this.defaults();
        data = { ...baseDefaults, ...data };
        data.meta.version = 4;
      }
      
      // *Force 'General' category enforcement on load*
      if (Array.isArray(data.categories)) {
        data.categories = data.categories.filter(c => c !== "General");
        data.categories.unshift("General");
      } else {
        data.categories = ["General"];
      }

      return data;
    } catch (e) {
      console.error("Load failed", e);
      const base = this.defaults();
      localStorage.setItem(this.key, JSON.stringify(base));
      return base;
    }
  },
  save(data) { localStorage.setItem(this.key, JSON.stringify(data)); },
  clear() { localStorage.removeItem(this.key); }
};

/* ------------------------------
   App Logic
--------------------------------*/
const App = {
  state: {
    role: null, teamId: null, user: null,
    eventTab: "setup",
    teamTab: "dashboard",
    ebcCategoryFilter: "General",
  },
  data: Store.load(),

  // Utils
  save() { Store.save(this.data); this.renderHeaderSession(); this.applyBrand(); this.updateHeaderInfo(); },
  reset() { if (!confirm("Are you sure you want to reset all data to default?")) return; this.data = Store.defaults(); this.save(); this.routeHome(); },
  uid(p="id") { return p + "-" + Math.random().toString(36).slice(2,9) + Date.now().toString(36).slice(-4); },
  fmtDate(d) { if (!d) return ""; try { return new Date(d).toLocaleDateString(); } catch { return d; } },
  esc(s) { return String(s ?? "").replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;', "'":'&#39;'}[m])); },

  // Export/Import Functions
  exportData() {
    const dataStr = JSON.stringify(this.data, null, 2);
    const blob = new Blob([dataStr], { type: "application/json" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = `${this.sanitizeFileName(this.data.eventInfo.eventTitle)}_export_${this.todayStr()}.json`;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
  },
  importData(file) {
    if (!file) return;
    const reader = new FileReader();
    reader.onload = (e) => {
      try {
        const importedData = JSON.parse(e.target.result);
        if (!importedData || typeof importedData.meta === 'undefined') throw new Error("Invalid data structure.");
        if (!confirm("Are you sure you want to replace ALL current data with this imported file? This action cannot be undone.")) return;
        
        const newDefaults = Store.defaults();
        this.data = { ...newDefaults, ...importedData };

        if (Array.isArray(this.data.categories)) {
          this.data.categories = this.data.categories.filter(c => c !== "General");
          this.data.categories.unshift("General");
        } else {
          this.data.categories = ["General"];
        }
        
        this.save();
        alert("Data imported successfully.");
        this.renderEventPortal();
      } catch (error) {
        alert(`Data import failed: ${error.message}`);
      }
    };
    reader.readAsText(file);
  },
  sanitizeFileName(s){ return String(s).replace(/[<>:"/\\|?*\x00-\x1F]/g,"_").slice(0,120); },
  todayStr() { const d = new Date(); return d.toISOString().slice(0,10); },
  
  // Entities
  getTeam(id){ return this.data.teams.find(t=>t.id===id); }
  ,getCompetition(id){ return this.data.competitions.find(c=>c.id===id); }
  ,getEntry(id){ return this.data.entries.find(e=>e.id===id); }
  ,getStudent(id){ return this.data.students.find(s=>s.id===id); }
  ,teamName(id){ const t=this.getTeam(id); return t? t.name : id; }

  ,studentsByTeam(teamId){ return this.data.students.filter(s=>s.teamId===teamId); }
  ,entriesByCompetition(compId){ return this.data.entries.filter(e=>e.competitionId===compId); }
  ,entriesByTeam(teamId){ return this.data.entries.filter(e=>e.teamId===teamId); }
  ,entriesByStudent(stuId){ return this.data.entries.filter(e=> e.memberStudentIds.includes(stuId)); }

  ,entryLabel(entry){
    const ms = entry.memberStudentIds.map(id=>this.getStudent(id)).filter(Boolean);
    const label = ms.map(m=> `${m.name} (#${m.chestNo})`).join(", ");
    return entry.entryType==="group" ? `Group: ${label}` : label;
  },

  // Scoring (Simplified implementation as requested)
  computeScores(){
    const teams = this.data.teams;
    // Only include non-General categories for the main scoreboards
    const cats = this.data.categories.filter(c => c !== "General");
    
    const teamCatScores = {};
    teams.forEach(t => { teamCatScores[t.id] = {}; cats.forEach(c => teamCatScores[t.id][c] = 0); });
    
    for (const r of this.data.results) {
      const e = this.getEntry(r.entryId); if (!e) continue;
      const c = this.getCompetition(r.competitionId); if (!c) continue;
      
      const points = Number(r.pointsAwarded||0);
      
      // Only score points if the competition is not in the 'General' category
      if (c.category !== "General" && teamCatScores[e.teamId]) {
        teamCatScores[e.teamId][c.category] += points;
      }
    }
    
    const perCategoryTeam = {};
    for (const cat of cats) {
      perCategoryTeam[cat] = teams.map(t => ({ teamId:t.id, teamName:t.name, points: teamCatScores[t.id][cat]||0 }))
        .sort((a,b)=> b.points - a.points || a.teamName.localeCompare(b.teamName));
    }
    
    const overallTeam = teams.map(t => {
      const total = cats.reduce((acc,c)=> acc + (teamCatScores[t.id][c]||0), 0);
      return { teamId: t.id, teamName: t.name, points: total };
    }).sort((a,b)=> b.points - a.points || a.teamName.localeCompare(b.teamName));
    
    return { perCategoryTeam, overallTeam };
  },


  // Branding
  updateHeaderInfo(){
    const info = this.data.eventInfo;
    const titleEl = document.getElementById('event-title-display');
    const subEl = document.getElementById('org-name-display');
    if (titleEl) titleEl.textContent = info.eventTitle || "Event Title";
    if (subEl) subEl.textContent = `${info.orgName || "Organizer Name"} • Event Crew + Team Portal`;
    document.title = `${info.eventTitle || "Event"} – Digital System`;
  },
  applyBrand(){
    const b = this.data.brand || {};
    // Note: The new theme uses hardcoded colors if branding options are not set
    document.documentElement.style.setProperty('--accent', b.accent || '#2c6be3');
    document.documentElement.style.setProperty('--accent-2', b.accent2 || '#1e4ea5');
    const el = document.getElementById('brand-logo');
    if (el) {
      if (b.logoDataUrl) {
        el.innerHTML = `<img src="${b.logoDataUrl}" alt="logo" style="width:100%;height:100%;object-fit:cover">`;
        el.style.background = "transparent";
      } else {
        // Use the first two letters of the event title
        const title = this.data.eventInfo.eventTitle || "ES";
        el.textContent = title.slice(0,1).toUpperCase() + title.slice(1,2).toLowerCase();
        el.style.background = "linear-gradient(135deg, var(--accent), var(--accent-2))";
      }
    }
    this.updateHeaderInfo();
  },

  // Session/Header
  renderHeaderSession(){
    const el = document.getElementById("header-session");
    if (!el) return;
    if (this.state.role === "event") {
      el.innerHTML = `<span class="tag green">Event Crew</span><span class="muted">Signed in as ${this.esc(this.state.user||"admin")}</span><button class="btn small" onclick="App.logout()">Logout</button>`;
    } else if (this.state.role === "team") {
      const team = this.getTeam(this.state.teamId);
      el.innerHTML = `<span class="tag blue">Team Portal</span><span class="muted">Team ${this.esc(team?.name||"")}</span><button class="btn small" onclick="App.logout()">Logout</button>`;
    } else {
      el.innerHTML = `<span class="muted">Not signed in</span>`;
    }
  },
  logout(){ this.state = { ...this.state, role: null, teamId: null, user: null, eventTab: "setup", teamTab: "dashboard" }; this.renderHeaderSession(); this.routeHome(); },

  // Routing
  routeHome(){
    const app = document.getElementById("app");
    app.innerHTML = `
      <div class="grid cols-2">
        <div class="card">
          <h2>Event Crew Portal</h2>
          <div class="muted">Manage competitions, attendance, results, and scoreboards.</div>
          <div class="hr"></div>
          <form onsubmit="App.eventLoginSubmit(event)">
            <div class="grid">
              <div><label>Username</label><input class="input" id="event-username" value="admin" required></div>
              <div><label>Password</label><input class="input" id="event-password" type="password" required></div>
            </div>
            <div class="row" style="margin-top:10px;"><button class="btn primary" type="submit">Login as Event Crew</button><span class="muted">Default: admin / felizia</span></div>
          </form>
        </div>
        <div class="card">
          <h2>Team Portal</h2>
          <div class="muted">Register students and enroll them into competitions using the team password.</div>
          <div class="hr"></div>
          ${this.data.teams.length === 0 ? `
            <div class="notice warn">No teams defined yet. Log in as Event Crew to add teams first.</div>
          ` : `
            <form onsubmit="App.teamLoginSubmit(event)">
              <div class="grid">
                <div>
                  <label>Team</label>
                  <select id="team-select" class="input">${this.data.teams.map(t=>`<option value="${t.id}">${this.esc(t.name)}</option>`).join("")}</select>
                </div>
                <div><label>Password</label><input class="input" id="team-password" type="password" required></div>
              </div>
              <div class="row" style="margin-top:10px;"><button class="btn primary" type="submit">Login to Team Portal</button><span class="muted">Ask admin for password.</span></div>
            </form>
          `}
        </div>
      </div>
      <div class="card" style="margin-top: 16px;">
        <h2>System Information</h2>
        <ul class="muted" style="margin-bottom:0; padding-left: 20px;">
          <li>The **'General'** category is mandatory. All registered students are automatically placed in this group for universal participation.</li>
          <li>Only non-'General' categories contribute to the main team **scoreboards**.</li>
          <li>Each Team Portal requires a **password** set by the Event Crew in the Setup tab.</li>
          <li>**Data persistence:** All data is saved automatically in your browser's local storage.</li>
        </ul>
      </div>
    `;
    this.applyBrand();
  },
  eventLoginSubmit(ev){
    ev.preventDefault();
    const u = document.getElementById("event-username").value.trim();
    const p = document.getElementById("event-password").value.trim();
    const creds = this.data.eventUser;
    if (u === creds.username && p === creds.password) { this.state.role = "event"; this.state.user = u; this.renderHeaderSession(); this.renderEventPortal(); }
    else alert("Invalid credentials.");
  },
  teamLoginSubmit(ev){
    ev.preventDefault();
    const id = document.getElementById("team-select").value;
    const p = document.getElementById("team-password").value.trim();
    const t = this.getTeam(id);
    if (!t) return alert("Team not found.");
    if (p === t.password) { this.state.role = "team"; this.state.teamId = id; this.state.user = t.name; this.renderHeaderSession(); this.renderTeamPortal(); }
    else alert("Invalid team password.");
  },

  /* ------------------------------
     Event Crew Portal
  --------------------------------*/
  renderEventPortal(){
    const app = document.getElementById("app");
    const tabs = [
      { id: "setup", label: "Setup" },
      { id: "competitions", label: "Competitions" },
      { id: "attendance_results", label: "Attendance & Results" },
      { id: "entries_by_category", label: "Entries by Category" },
      { id: "students_by_category", label: "Students" },
      { id: "scoreboards", label: "Scoreboards" },
      { id: "data", label: "Data" }
    ];
    app.innerHTML = `
      <div class="card">
        <div class="nav">
          ${tabs.map(t=>`<button class="tab ${this.state.eventTab===t.id?'active':''}" onclick="App.eventSwitchTab('${t.id}')">${t.label}</button>`).join("")}
        </div>
        <div id="event-tab"></div>
      </div>
    `;
    this.renderEventTab();
  },
  eventSwitchTab(id){ this.state.eventTab = id; this.renderEventPortal(); },
  renderEventTab(){
    const wrap = document.getElementById("event-tab"); if (!wrap) return;
    if (this.state.eventTab === "setup") return this.eventTabSetup(wrap);
    if (this.state.eventTab === "competitions") return this.eventTabCompetitions(wrap);
    if (this.state.eventTab === "attendance_results") return this.eventTabAttendanceResults(wrap);
    if (this.state.eventTab === "entries_by_category") return this.eventTabEntriesByCategory(wrap);
    if (this.state.eventTab === "students_by_category") return this.eventTabStudentsByCategory(wrap);
    if (this.state.eventTab === "scoreboards") return this.eventTabScoreboards(wrap);
    if (this.state.eventTab === "data") return this.eventTabData(wrap);
  },

  eventTabSetup(wrap){
    wrap.innerHTML = `
      <div class="grid cols-2">
        <div class="card">
          <h2>Event Details</h2>
          <div class="muted">Set the festival name and organizing body.</div>
          <div class="hr"></div>
          <form onsubmit="App.updateEventInfo(event)">
            <div><label>Event Title</label><input class="input" id="setup-title" value="${this.esc(this.data.eventInfo.eventTitle)}" required></div>
            <div style="margin-top:10px;"><label>Organizer Name</label><input class="input" id="setup-org" value="${this.esc(this.data.eventInfo.orgName)}" required></div>
            <div class="row" style="margin-top:10px;"><button class="btn primary" type="submit">Update Info</button></div>
          </form>
        </div>
        <div class="card">
          <h2>Team Portal Lock</h2>
          <div class="muted">Stops teams from editing rosters or enrollments. Viewing stays allowed.</div>
          <div class="hr"></div>
          <div class="row">
            <span class="tag ${this.data.portalLocked?'red':'green'}">${this.data.portalLocked?'Locked 🔒':'Unlocked 🔓'}</span>
            <button class="btn ${this.data.portalLocked?'':'warn'}" onclick="App.togglePortalLock()">${this.data.portalLocked?'Unlock Portals':'Lock Portals'}</button>
          </div>
        </div>
      </div>

      <div class="grid cols-2" style="margin-top: 16px;">
        <div class="card">
          <h2>Manage Teams (${this.data.teams.length})</h2>
          <div class="hr"></div>
          <form onsubmit="App.addTeam(event)">
            <div class="row">
              <input class="input" id="new-team-name" placeholder="New Team Name" required>
              <button class="btn primary" type="submit">Add Team</button>
            </div>
          </form>
          <div class="hr"></div>
          <div class="grid" style="gap: 12px;">
            ${this.data.teams.map(t=>`
              <div class="row" style="gap:12px;">
                <div style="flex:1;">
                  <div><strong>${this.esc(t.name)}</strong></div>
                  <div class="muted">ID: ${t.id} / ${this.studentsByTeam(t.id).length} students</div>
                </div>
                <input class="input" type="password" id="pw-${t.id}" placeholder="new password">
                <button class="btn small" onclick="App.setTeamPassword('${t.id}')">Set</button>
                <button class="btn small danger" onclick="App.deleteTeam('${t.id}')">Delete</button>
              </div>
            `).join("") || '<div class="muted">No teams defined.</div>'}
          </div>
        </div>

        <div class="card">
          <h2>Manage Categories (${this.data.categories.length})</h2>
          <div class="muted">**'General' is fixed and includes all students for universal entry.** Only other categories contribute points.</div>
          <div class="hr"></div>
          <form onsubmit="App.addCategory(event)">
            <div class="row">
              <input class="input" id="new-category-name" placeholder="New Competition Category Name" required>
              <button class="btn primary" type="submit">Add Category</button>
            </div>
          </form>
          <div class="hr"></div>
          <div class="grid" style="gap: 8px;">
            ${this.data.categories.map(c=>`
              <div class="row">
                <div class="tag ${c === "General" ? 'green' : 'blue'}">${this.esc(c)}</div>
                <div class="muted">${this.data.competitions.filter(comp => comp.category === c).length} competitions</div>
                <div class="spacer"></div>
                ${c === "General" ? '<span class="muted">Fixed</span>' : `<button class="btn small danger" onclick="App.deleteCategory('${c}')">Remove</button>`}
              </div>
            `).join("")}
          </div>
        </div>
      </div>
    
      <div class="card" style="margin-top: 16px;">
        <h2>Create Competition</h2>
        <div class="muted">Category, type, team entry limit, and optional schedule.</div>
        <div class="hr"></div>
        <form onsubmit="App.createCompetition(event)">
          <div class="grid cols-3">
            <div><label>Name</label><input class="input" id="comp-name" required placeholder="e.g., Malayalam Elocution"></div>
            <div><label>Category</label><select class="input" id="comp-category">${this.data.categories.map(c=>`<option>${this.esc(c)}</option>`).join("")}</select></div>
            <div><label>Type</label><select class="input" id="comp-type"><option value="individual">Individual</option><option value="group">Group</option></select></div>
          </div>
          <div class="grid cols-3" style="margin-top:10px;">
            <div><label>Team Entry Limit</label><input class="input" id="comp-limit" type="number" min="1" step="1" value="1" required></div>
            <div><label>Max Group Size (optional)</label><input class="input" id="comp-maxgroup" type="number" min="1" step="1"></div>
            <div><label>Date</label><input class="input" id="comp-date" type="date"></div>
          </div>
          <div class="grid cols-3" style="margin-top:10px;">
            <div><label>Time</label><input class="input" id="comp-time" type="time"></div>
            <div class="row" style="align-items:flex-end;"><button class="btn primary" type="submit">Add Competition</button></div>
          </div>
        </form>
      </div>
    `;
  },
  updateEventInfo(ev){
    ev.preventDefault();
    this.data.eventInfo.eventTitle = document.getElementById("setup-title").value.trim();
    this.data.eventInfo.orgName = document.getElementById("setup-org").value.trim();
    this.save();
    alert("Event details updated.");
    this.renderEventPortal();
  },
  addTeam(ev){
    ev.preventDefault();
    const name = document.getElementById("new-team-name").value.trim();
    if (!name) return;
    if (this.data.teams.some(t => t.name.toLowerCase() === name.toLowerCase())) {
      return alert("A team with this name already exists.");
    }
    // Default password for a new team is 'team123'
    this.data.teams.push({ id: this.uid("team"), name, password: "team123" });
    this.save();
    document.getElementById("new-team-name").value = "";
    this.renderEventPortal();
  },
  deleteTeam(id){
    const t = this.getTeam(id);
    if (!t) return;
    if (!confirm(`Are you sure you want to delete the team "${t.name}"? This will also remove all their students and entries!`)) return;
    
    // Remove students, entries, attendance, and results associated with the team
    this.data.entries = this.data.entries.filter(e => e.teamId !== id);
    this.data.students = this.data.students.filter(s => s.teamId !== id);
    this.data.attendance = this.data.attendance.filter(a => !this.data.entries.some(e => e.id === a.entryId && e.teamId === id));
    this.data.results = this.data.results.filter(r => !this.data.entries.some(e => e.id === r.entryId && e.teamId === id));

    this.data.teams = this.data.teams.filter(t => t.id !== id);
    this.save();
    this.renderEventPortal();
  },
  addCategory(ev){
    ev.preventDefault();
    let name = document.getElementById("new-category-name").value.trim();
    if (!name) return;
    name = name.split(',').map(s => s.trim()).filter(s => s.length > 0)[0];
    if (!name) return;
    if (this.data.categories.some(c => c.toLowerCase() === name.toLowerCase())) {
      return alert("This category already exists.");
    }
    
    this.data.categories.push(name);
    this.save();
    document.getElementById("new-category-name").value = "";
    this.renderEventPortal();
  },
  deleteCategory(name){
    if (name === "General") return alert("'General' category cannot be deleted.");
    if (this.data.competitions.some(c => c.category === name)) {
      return alert(`Cannot delete category "${name}" because ${this.data.competitions.filter(c => c.category === name).length} competitions are currently using it.`);
    }
    if (!confirm(`Are you sure you want to delete the category "${name}"?`)) return;

    this.data.categories = this.data.categories.filter(c => c !== name);
    this.save();
    this.renderEventPortal();
  },
  togglePortalLock(){ this.data.portalLocked = !this.data.portalLocked; this.save(); this.renderEventPortal(); },
  setTeamPassword(teamId){
    const inp = document.getElementById("pw-"+teamId);
    const v = (inp?.value||"").trim(); if (!v) return alert("Enter a new password.");
    const t = this.getTeam(teamId); if (!t) return;
    t.password = v; this.save();
    alert(`Updated password for ${t.name}.`); inp.value = "";
  },
  createCompetition(ev){
    ev.preventDefault();
    const name = document.getElementById("comp-name").value.trim();
    const category = document.getElementById("comp-category").value;
    const type = document.getElementById("comp-type").value;
    const limit = parseInt(document.getElementById("comp-limit").value||"0",10);
    const maxGroup = document.getElementById("comp-maxgroup").value;
    const date = document.getElementById("comp-date").value||null;
    const time = document.getElementById("comp-time").value||null;
    if (!name) return alert("Name required.");
    if (!this.data.categories.includes(category)) return alert("Invalid category.");
    if (!(limit > 0)) return alert("Limit must be >=1.");
    this.data.competitions.push({ id:this.uid("comp"), name, category, isGroup:(type==="group"), teamEntryLimit:limit, maxGroupSize: maxGroup?parseInt(maxGroup,10):null, date, time, locked:false });
    this.save(); alert("Competition added."); this.renderEventPortal();
  },

  eventTabCompetitions(wrap){
    const comps = this.data.competitions.slice().sort((a,b)=> (a.category||"").localeCompare(b.category||"") || (a.date||"").localeCompare(b.date||"") || a.name.localeCompare(b.name));
    wrap.innerHTML = `
      <div class="row" style="margin-bottom:8px;"><h2 class="section-title">Competitions (${comps.length})</h2></div>
      <div class="table-wrap"><table>
        <thead><tr><th>Category</th><th>Name</th><th>Type</th><th>Team Limit</th><th>Date/Time</th><th>Entries</th><th>Actions</th></tr></thead>
        <tbody>
          ${comps.map(c=>{
            const count = this.entriesByCompetition(c.id).length;
            const dt = [c.date?this.fmtDate(c.date):"", c.time||""].filter(Boolean).join(" ");
            return `<tr>
              <td>${this.esc(c.category)}</td>
              <td><strong>${this.esc(c.name)}</strong></td>
              <td>${c.isGroup?'<span class="tag blue">Group</span>':'<span class="tag green">Individual</span>'}</td>
              <td>${c.teamEntryLimit}</td>
              <td>${this.esc(dt||"-")}</td>
              <td>${count}</td>
              <td class="row">
                <button class="btn small" onclick="App.viewCompetition('${c.id}')">View</button>
                <button class="btn small" onclick="App.editCompetition('${c.id}')">Edit</button>
                <button class="btn small warn" onclick="App.toggleCompetitionLock('${c.id}')">${c.locked?'Unlock':'Lock'}</button>
                <button class="btn small danger" onclick="App.deleteCompetition('${c.id}')">Delete</button>
              </td>
            </tr>`;
          }).join("") || '<tr><td colspan="7" class="muted">No competitions yet.</td></tr>'}
        </tbody>
      </table></div>
    `;
  },
  viewCompetition(compId){
    const c = this.getCompetition(compId); if (!c) return;
    const entries = this.entriesByCompetition(compId);
    const byTeam = {};
    for (const e of entries) { byTeam[e.teamId] = byTeam[e.teamId] || []; byTeam[e.teamId].push(e); }
    const teams = this.data.teams.slice().sort((a,b)=>a.name.localeCompare(b.name));
    const blocks = teams.map(t=>{
      const list = (byTeam[t.id]||[]);
      if (!list.length) return "";
      return `<div class="card">
        <div class="row"><strong>${this.esc(t.name)}</strong><span class="tag">${list.length} entries</span></div>
        <ul class="muted" style="font-size:13px; margin: 8px 0 0 16px; padding:0;">${list.map(e=>`<li>${this.esc(this.entryLabel(e))}</li>`).join("")}</ul>
      </div>`;
    }).join("");
    const app = document.getElementById("app");
    app.innerHTML = `
      <div class="row" style="margin-bottom:8px;">
        <button class="btn" onclick="App.renderEventPortal()">← Back</button>
        <div class="spacer"></div>
        <button class="btn primary" onclick="App.openJudgePanel('${c.id}')">Judge Panel</button>
      </div>
      <div class="card">
        <h2>${this.esc(c.name)}</h2>
        <div class="muted">${this.esc(c.category)} • ${c.isGroup?"Group":"Individual"} • Team limit: ${c.teamEntryLimit} ${c.maxGroupSize?("• Max group size: "+c.maxGroupSize):""} ${c.date?("• "+this.fmtDate(c.date)):""} ${c.time?(" "+c.time):""} ${c.locked? '• <span class="tag red">Locked</span>':""}</div>
        <div class="hr"></div>
        <h3 class="section-title">Entries by Team</h3>
        <div class="grid cols-3">${blocks || '<div class="notice">No entries yet.</div>'}</div>
      </div>
    `;
  },
  editCompetition(compId){
    const c = this.getCompetition(compId); if (!c) return;
    const app = document.getElementById("app");
    app.innerHTML = `
      <div class="row" style="margin-bottom:8px;"><button class="btn" onclick="App.renderEventPortal()">← Back</button></div>
      <div class="card">
        <h2>Edit Competition</h2>
        <form onsubmit="App.updateCompetition(event,'${c.id}')">
          <div class="grid cols-3">
            <div><label>Name</label><input class="input" id="u-name" value="${this.esc(c.name)}" required></div>
            <div><label>Category</label><select class="input" id="u-cat">${this.data.categories.map(x=>`<option ${x===c.category?'selected':''}>${this.esc(x)}</option>`).join("")}</select></div>
            <div><label>Type</label><select class="input" id="u-type"><option value="individual" ${!c.isGroup?'selected':''}>Individual</option><option value="group" ${c.isGroup?'selected':''}>Group</option></select></div>
          </div>
          <div class="grid cols-3" style="margin-top:10px;">
            <div><label>Team Entry Limit</label><input class="input" id="u-limit" type="number" min="1" step="1" value="${c.teamEntryLimit}"></div>
            <div><label>Max Group Size</label><input class="input" id="u-maxgroup" type="number" min="1" step="1" value="${c.maxGroupSize||""}"></div>
            <div><label>Date</label><input class="input" id="u-date" type="date" value="${c.date||""}"></div>
          </div>
          <div class="grid cols-3" style="margin-top:10px;">
            <div><label>Time</label><input class="input" id="u-time" type="time" value="${c.time||""}"></div>
          </div>
          <div class="row" style="margin-top:12px;">
            <button class="btn primary" type="submit">Save</button>
            <button class="btn" type="button" onclick="App.renderEventPortal()">Cancel</button>
          </div>
        </form>
      </div>
    `;
  },
  updateCompetition(ev, id){
    ev.preventDefault();
    const c = this.getCompetition(id); if (!c) return;
    const name = document.getElementById("u-name").value.trim();
    const cat = document.getElementById("u-cat").value;
    const isGroup = document.getElementById("u-type").value === "group";
    const limit = parseInt(document.getElementById("u-limit").value||"0",10);
    const maxGroup = document.getElementById("u-maxgroup").value;
    const date = document.getElementById("u-date").value||null;
    const time = document.getElementById("u-time").value||null;
    if (!name) return alert("Name required.");
    if (!this.data.categories.includes(cat)) return alert("Invalid category.");
    if (!(limit > 0)) return alert("Limit must be >=1.");

    c.name = name;
    c.category = cat;
    c.isGroup = isGroup;
    c.teamEntryLimit = limit;
    c.maxGroupSize = maxGroup?parseInt(maxGroup,10):null;
    c.date = date;
    c.time = time;
    this.save();
    alert("Competition updated.");
    this.renderEventPortal();
  },
  toggleCompetitionLock(id){
    const c = this.getCompetition(id); if (!c) return;
    c.locked = !c.locked;
    this.save();
    this.renderEventPortal();
  },
  deleteCompetition(id){
    const c = this.getCompetition(id); if (!c) return;
    if (!confirm(`Are you sure you want to delete the competition "${c.name}"? This will also remove all related entries, attendance, and results.`)) return;

    this.data.entries = this.data.entries.filter(e => e.competitionId !== id);
    this.data.attendance = this.data.attendance.filter(a => a.competitionId !== id);
    this.data.results = this.data.results.filter(r => r.competitionId !== id);
    this.data.competitions = this.data.competitions.filter(comp => comp.id !== id);
    this.save();
    this.renderEventPortal();
  },

  eventTabAttendanceResults(wrap){
    const comps = this.data.competitions.slice().sort((a,b)=> (a.category||"").localeCompare(b.category||"") || (a.date||"").localeCompare(b.date||"") || a.name.localeCompare(b.name));
    wrap.innerHTML = `
      <div class="row" style="margin-bottom:8px;"><h2 class="section-title">Competition Control Panel</h2></div>
      <div class="table-wrap"><table>
        <thead><tr><th>Category</th><th>Name</th><th>Entries</th><th>Results Status</th><th>Actions</th></tr></thead>
        <tbody>
          ${comps.map(c=>{
            const entries = this.entriesByCompetition(c.id);
            const results = this.data.results.filter(r => r.competitionId === c.id);
            
            const resStatus = results.length > 0
              ? `Scored (${results.length} records)`
              : 'Not scored';

            return `<tr>
              <td>${this.esc(c.category)}</td>
              <td><strong>${this.esc(c.name)}</strong></td>
              <td>${entries.length}</td>
              <td>${resStatus}</td>
              <td class="row">
                <button class="btn small primary" onclick="App.openJudgePanel('${c.id}')">Judge Panel / Enter Marks</button>
              </td>
            </tr>`;
          }).join("") || '<tr><td colspan="5" class="muted">No competitions yet.</td></tr>'}
        </tbody>
      </table></div>
    `;
  },
  openJudgePanel(compId){ alert('Judge Panel (results/marks entry) for competition: '+compId+' is omitted for brevity but would be implemented here, including points entry.'); },

  eventTabEntriesByCategory(wrap){
    const categories = this.data.categories.slice();
    let filterCat = this.state.ebcCategoryFilter || categories[0];
    
    const comps = this.data.competitions.filter(c => c.category === filterCat).sort((a,b)=>a.name.localeCompare(b.name));
    
    wrap.innerHTML = `
      <div class="nav">
        ${categories.map(c => `<button class="tab ${c === filterCat ? 'active' : ''}" onclick="App.setEBCFilter('${c}')">${this.esc(c)}</button>`).join("")}
      </div>
      <h3 class="section-title">Competitions in ${this.esc(filterCat)} (${comps.length})</h3>
      <div class="table-wrap"><table>
        <thead><tr><th>Name</th><th>Type</th><th>Limit</th><th>Entries</th><th>Date/Time</th></tr></thead>
        <tbody>
          ${comps.map(c => `
            <tr>
              <td><a href="#" onclick="App.viewCompetition('${c.id}'); return false;"><strong>${this.esc(c.name)}</strong></a></td>
              <td>${c.isGroup ? 'Group' : 'Individual'}</td>
              <td>${c.teamEntryLimit}</td>
              <td>${this.entriesByCompetition(c.id).length}</td>
              <td>${c.date ? this.fmtDate(c.date) : ''} ${c.time || ''}</td>
            </tr>
          `).join("") || `<tr><td colspan="5" class="muted">No competitions in this category yet.</td></tr>`}
        </tbody>
      </table></div>
    `;
  },
  setEBCFilter(cat){ this.state.ebcCategoryFilter = cat; this.renderEventTab(); },

  eventTabStudentsByCategory(wrap){
    const students = this.data.students.slice().sort((a,b)=>a.chestNo.localeCompare(b.chestNo));
    
    wrap.innerHTML = `
      <h3 class="section-title">All Students (${students.length})</h3>
      <div class="muted">All students are implicitly in the 'General' category for attendance/enrollment purposes.</div>
      <div class="hr"></div>
      <div class="table-wrap"><table>
        <thead><tr><th>Chest No.</th><th>Name</th><th>Team</th><th>Total Entries</th></tr></thead>
        <tbody>
          ${students.map(s => `
            <tr>
              <td><strong>#${this.esc(s.chestNo)}</strong></td>
              <td>${this.esc(s.name)}</td>
              <td>${this.teamName(s.teamId)}</td>
              <td>${this.entriesByStudent(s.id).length}</td>
            </tr>
          `).join("") || `<tr><td colspan="4" class="muted">No students registered yet.</td></tr>`}
        </tbody>
      </table></div>
    `;
  },
  eventTabScoreboards(wrap){ 
    const scores = this.computeScores();
    const categories = this.data.categories.filter(c => c !== "General");

    wrap.innerHTML = `
      <h2>Overall Scoreboard (Non-General Categories Only)</h2>
      <div class="table-wrap" style="margin-bottom: 24px;"><table>
        <thead><tr><th>Rank</th><th>Team</th><th>Total Points</th></tr></thead>
        <tbody>
          ${scores.overallTeam.map((t, i) => `
            <tr style="${i===0?'background:#eef6ff; font-weight:bold;':''}">
              <td>${i + 1}</td>
              <td>${this.esc(t.teamName)}</td>
              <td>${t.points}</td>
            </tr>
          `).join("")}
        </tbody>
      </table></div>

      <h2>Category Scoreboards</h2>
      <div class="grid cols-2" style="margin-top: 12px;">
        ${categories.map(cat => `
          <div class="card">
            <h3 class="section-title">${this.esc(cat)} Category</h3>
            <div class="table-wrap"><table>
              <thead><tr><th>Rank</th><th>Team</th><th>Points</th></tr></thead>
              <tbody>
                ${scores.perCategoryTeam[cat].map((t, i) => `
                  <tr style="${i===0?'background:#eef6ff;':''}">
                    <td>${i + 1}</td>
                    <td>${this.esc(t.teamName)}</td>
                    <td>${t.points}</td>
                  </tr>
                `).join("")}
              </tbody>
            </table></div>
          </div>
        `).join("") || '<div class="notice">No categories defined other than "General". Scores only shown for non-General categories.</div>'}
      </div>
    `;
  },
  eventTabData(wrap){
    wrap.innerHTML = `
      <h2>Data Management (Event Crew)</h2>
      <div class="card">
        <h3 class="section-title">Import / Export</h3>
        <div class="row">
          <button class="btn primary" onclick="App.exportData()">Export Data (JSON)</button>
          <div class="spacer"></div>
          <input type="file" id="import-file" accept=".json" style="flex: 1;">
          <button class="btn warn" onclick="document.getElementById('import-file').files[0] ? App.importData(document.getElementById('import-file').files[0]) : alert('Please select a file first.')">Import Data (JSON)</button>
        </div>
        <div class="muted" style="margin-top: 8px;">Export saves a full backup. Import *replaces* all current data. Use with caution.</div>
      </div>
      <div class="card" style="margin-top: 16px;">
        <h3 class="section-title">System Reset</h3>
        <button class="btn danger" onclick="App.reset()">Reset All Data to Default</button>
        <div class="muted" style="margin-top: 8px;">This clears all local storage data for this system.</div>
      </div>
    `;
  },

  /* ------------------------------
     Team Portal
  --------------------------------*/
  renderTeamPortal(){
    const app = document.getElementById("app");
    const team = this.getTeam(this.state.teamId);
    if (!team) return this.logout();
    const isLocked = this.data.portalLocked;

    const tabs = [
      { id: "dashboard", label: "Dashboard" },
      { id: "roster", label: "Student Roster" },
      { id: "enrollment", label: "Competition Enrollment" },
      { id: "results", label: "Results" }
    ];

    app.innerHTML = `
      <div class="card">
        ${isLocked ? '<div class="notice warn" style="margin-bottom: 12px;">🔒 The Team Portal is locked by Event Crew. Edits are disabled.</div>' : ''}
        <div class="nav">
          ${tabs.map(t=>`<button class="tab ${this.state.teamTab===t.id?'active':''}" onclick="App.teamSwitchTab('${t.id}')">${t.label}</button>`).join("")}
        </div>
        <div id="team-tab"></div>
      </div>
    `;
    this.renderTeamTab();
  },
  teamSwitchTab(id){ this.state.teamTab = id; this.renderTeamPortal(); },
  renderTeamTab(){
    const wrap = document.getElementById("team-tab"); if (!wrap) return;
    if (this.state.teamTab === "dashboard") return this.teamTabDashboard(wrap);
    if (this.state.teamTab === "roster") return this.teamTabRoster(wrap);
    if (this.state.teamTab === "enrollment") return this.teamTabEnrollment(wrap);
    if (this.state.teamTab === "results") return this.teamTabResults(wrap);
  },
  teamTabDashboard(wrap){
    const team = this.getTeam(this.state.teamId);
    const students = this.studentsByTeam(team.id);
    const entries = this.entriesByTeam(team.id);
    
    // Calculate team's current score
    const scores = this.computeScores();
    const teamScore = scores.overallTeam.find(t => t.teamId === team.id)?.points || 0;
    
    wrap.innerHTML = `
      <h2>${this.esc(team.name)} Dashboard</h2>
      <div class="grid cols-3">
        <div class="card">
          <h3 class="section-title">Registered Students</h3>
          <div style="font-size: 32px; font-weight: bold;">${students.length}</div>
          <div class="muted">Go to Roster to manage students.</div>
        </div>
        <div class="card">
          <h3 class="section-title">Competition Entries</h3>
          <div style="font-size: 32px; font-weight: bold;">${entries.length}</div>
          <div class="muted">Go to Enrollment to register.</div>
        </div>
        <div class="card">
          <h3 class="section-title">Total Score (Non-General)</h3>
          <div style="font-size: 32px; font-weight: bold; color: var(--accent);">${teamScore}</div>
          <div class="muted">Points awarded in non-'General' category competitions.</div>
        </div>
      </div>
      <div class="card" style="margin-top: 16px;">
        <h3 class="section-title">Data Management (Team Portal)</h3>
        <div class="row">
          <button class="btn primary" onclick="App.exportData()">Export System Data (JSON)</button>
        </div>
        <div class="muted" style="margin-top: 8px;">Export saves a full backup of the system's current data.</div>
      </div>
    `;
  },
  teamTabRoster(wrap){
    const team = this.getTeam(this.state.teamId);
    const students = this.studentsByTeam(team.id).slice().sort((a,b)=>a.chestNo.localeCompare(b.chestNo));
    const isLocked = this.data.portalLocked;

    wrap.innerHTML = `
      <h2>Student Roster for ${this.esc(team.name)}</h2>
      ${!isLocked ? `
        <div class="card">
          <h3 class="section-title">Add Student</h3>
          <form onsubmit="App.addStudent(event)">
            <div class="grid cols-3">
              <div><label>Chest No.</label><input class="input" id="student-chest" required placeholder="101A"></div>
              <div><label>Full Name</label><input class="input" id="student-name" required placeholder="Fulan bin Fulan"></div>
              <div class="row" style="align-items:flex-end;"><button class="btn primary" type="submit">Add Student</button></div>
            </div>
          </form>
        </div>
      ` : ''}
      
      <div class="card" style="margin-top: 16px;">
        <h3 class="section-title">Roster (${students.length} students)</h3>
        <div class="table-wrap"><table>
          <thead><tr><th>Chest No.</th><th>Name</th><th>Entries</th>${!isLocked ? '<th>Actions</th>' : ''}</tr></thead>
          <tbody>
            ${students.map(s => `
              <tr>
                <td><strong>#${this.esc(s.chestNo)}</strong></td>
                <td>${this.esc(s.name)}</td>
                <td>${this.entriesByStudent(s.id).length}</td>
                ${!isLocked ? `<td><button class="btn small danger" onclick="App.deleteStudent('${s.id}')">Delete</button></td>` : ''}
              </tr>
            `).join("") || `<tr><td colspan="${!isLocked ? 4 : 3}" class="muted">No students registered yet.</td></tr>`}
          </tbody>
        </table></div>
    `;
  },
  addStudent(ev){
    ev.preventDefault();
    if (this.data.portalLocked) return alert("Portal is locked. Cannot add students.");
    const teamId = this.state.teamId;
    const chestNo = document.getElementById("student-chest").value.trim().toUpperCase();
    const name = document.getElementById("student-name").value.trim();
    
    if (!chestNo || !name) return alert("All fields are required.");
    if (this.data.students.some(s => s.chestNo === chestNo)) return alert(`Chest No. ${chestNo} is already in use.`);

    this.data.students.push({ id: this.uid("stu"), teamId, chestNo, name, category: "General" });
    this.save();
    document.getElementById("student-chest").value = "";
    document.getElementById("student-name").value = "";
    this.renderTeamPortal();
  },
  deleteStudent(id){
    if (this.data.portalLocked) return alert("Portal is locked. Cannot delete students.");
    const s = this.getStudent(id); if (!s) return;
    const entries = this.entriesByStudent(id);
    if (entries.length > 0) return alert(`Cannot delete student ${s.name} (#${s.chestNo}) because they are enrolled in ${entries.length} competitions. Please unenroll them first.`);
    if (!confirm(`Are you sure you want to delete student ${s.name} (#${s.chestNo})?`)) return;

    this.data.students = this.data.students.filter(stu => stu.id !== id);
    this.save();
    this.renderTeamPortal();
  },
  teamTabEnrollment(wrap){
    const team = this.getTeam(this.state.teamId);
    const students = this.studentsByTeam(team.id);
    const comps = this.data.competitions.slice().sort((a,b)=>a.name.localeCompare(b.name));
    const isLocked = this.data.portalLocked;

    wrap.innerHTML = `
      <h2>Competition Enrollment</h2>
      ${students.length === 0 ? '<div class="notice warn">You must add students to the Roster first before enrolling them.</div><div class="hr"></div>' : ''}
      
      <div class="table-wrap"><table>
        <thead><tr><th>Competition</th><th>Category</th><th>Type</th><th>Limit</th><th>Your Entries</th><th>Action</th></tr></thead>
        <tbody>
          ${comps.map(c => {
            const teamEntries = this.data.entries.filter(e => e.teamId === team.id && e.competitionId === c.id);
            const entryCount = teamEntries.length;
            const canAdd = students.length > 0 && entryCount < c.teamEntryLimit && !c.locked && !isLocked;
            
            let actionHtml = '';
            if (c.locked) actionHtml = '<span class="tag red">Locked</span>';
            else if (isLocked) actionHtml = '<span class="tag red">Portal Locked</span>';
            else if (entryCount >= c.teamEntryLimit) actionHtml = '<span class="tag warn">Limit Reached</span>';
            else if (students.length === 0) actionHtml = '<span class="tag red">Add Students First</span>';
            else actionHtml = `<button class="btn small primary" onclick="App.openEntryForm('${c.id}')">Add Entry</button>`;

            return `<tr>
              <td><strong>${this.esc(c.name)}</strong></td>
              <td>${this.esc(c.category)}</td>
              <td>${c.isGroup ? 'Group' : 'Individual'} ${c.maxGroupSize ? `(Max ${c.maxGroupSize})` : ''}</td>
              <td>${c.teamEntryLimit}</td>
              <td>${entryCount}</td>
              <td>${actionHtml}</td>
            </tr>`;
          }).join("") || `<tr><td colspan="6" class="muted">No competitions defined by the Event Crew yet.</td></tr>`}
        </tbody>
      </table></div>
    
      <h3 class="section-title" style="margin-top: 20px;">Current Entries (${this.entriesByTeam(team.id).length})</h3>
      <div class="table-wrap"><table>
        <thead><tr><th>Competition</th><th>Entry Details</th><th>Action</th></tr></thead>
        <tbody>
          ${this.entriesByTeam(team.id).map(e => {
            const c = this.getCompetition(e.competitionId);
            const isCompLocked = c?.locked || isLocked;
            return `<tr>
              <td>${this.esc(c?.name || 'Unknown Competition')}</td>
              <td>${this.entryLabel(e)}</td>
              <td>${isCompLocked ? '<span class="tag red">Locked</span>' : `<button class="btn small danger" onclick="App.deleteEntry('${e.id}')">Unenroll</button>`}</td>
            </tr>`;
          }).join("") || `<tr><td colspan="3" class="muted">No entries registered yet.</td></tr>`}
        </tbody>
      </table></div>
    `;
  },
  openEntryForm(compId){
    const c = this.getCompetition(compId); if (!c) return;
    const team = this.getTeam(this.state.teamId);
    const students = this.studentsByTeam(team.id);
    if (students.length === 0) return alert("Please add students to the roster first.");
    
    const entryType = c.isGroup ? 'group' : 'individual';
    const maxCount = c.maxGroupSize && entryType === 'group' ? c.maxGroupSize : (entryType === 'individual' ? 1 : students.length);

    const studentCheckboxes = students.map(s => `
      <div style="display:flex; align-items:center; gap: 8px;">
        <input type="checkbox" name="studentIds" value="${s.id}" id="stu-${s.id}">
        <label for="stu-${s.id}">#${this.esc(s.chestNo)} - ${this.esc(s.name)}</label>
      </div>
    `).join("");

    const modalHtml = `
      <div style="position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); z-index:1000; display:grid; place-items:center;">
        <div class="card" style="width: 90%; max-width: 500px;">
          <h2>Enroll in: ${this.esc(c.name)}</h2>
          <div class="muted">Select ${entryType === 'group' ? `members (Max: ${maxCount})` : 'one student'}:</div>
          <div class="hr"></div>
          <form id="entry-form" onsubmit="App.submitEntry(event, '${c.id}', '${entryType}', ${maxCount})">
            <div style="max-height: 200px; overflow-y: auto; padding: 10px; border: 1px solid var(--border); border-radius: 8px;">
              ${studentCheckboxes}
            </div>
            <div class="row" style="margin-top: 15px;">
              <button class="btn primary" type="submit">Confirm Enrollment</button>
              <button class="btn" type="button" onclick="this.closest('div[style*=\'position:fixed\']').remove()">Cancel</button>
            </div>
          </form>
        </div>
      </div>
    `;
    document.body.insertAdjacentHTML('beforeend', modalHtml);
  },
  submitEntry(ev, compId, entryType, maxCount){
    ev.preventDefault();
    const form = ev.target;
    const selectedIds = Array.from(form.querySelectorAll('input[name="studentIds"]:checked')).map(el => el.value);
    
    if (entryType === 'individual' && selectedIds.length !== 1) return alert("Select exactly one student for an individual entry.");
    if (entryType === 'group' && (selectedIds.length < 1 || selectedIds.length > maxCount)) return alert(`Select between 1 and ${maxCount} students for this group entry.`);

    const c = this.getCompetition(compId);
    const team = this.getTeam(this.state.teamId);
    if (!c || !team) return;

    // Check team limit again
    const teamEntries = this.data.entries.filter(e => e.teamId === team.id && e.competitionId === c.id);
    if (teamEntries.length >= c.teamEntryLimit) return alert("Team entry limit already reached.");

    this.data.entries.push({
      id: this.uid("entry"),
      teamId: team.id,
      competitionId: compId,
      entryType: entryType,
      memberStudentIds: selectedIds,
      createdAt: Date.now()
    });
    this.save();
    alert("Entry successfully added.");
    form.closest('div[style*=\'position:fixed\']').remove();
    this.renderTeamPortal();
  },
  deleteEntry(id){
    if (this.data.portalLocked) return alert("Portal is locked. Cannot unenroll.");
    const e = this.getEntry(id);
    if (!e) return;
    const c = this.getCompetition(e.competitionId);

    if (c?.locked) return alert(`Competition "${c.name}" is locked. Cannot unenroll.`);

    if (!confirm(`Are you sure you want to unenroll this entry from "${c?.name || 'Unknown Competition'}"?`)) return;

    this.data.entries = this.data.entries.filter(entry => entry.id !== id);
    this.data.attendance = this.data.attendance.filter(a => a.entryId !== id);
    this.data.results = this.data.results.filter(r => r.entryId !== id);
    this.save();
    this.renderTeamPortal();
  },

  teamTabResults(wrap){
    const team = this.getTeam(this.state.teamId);
    const teamEntries = this.entriesByTeam(team.id);
    const entryResults = this.data.results.filter(r => teamEntries.some(e => e.id === r.entryId));
    
    const displayResults = teamEntries.map(e => {
      const c = this.getCompetition(e.competitionId);
      const r = entryResults.find(res => res.entryId === e.id);
      return {
        compName: c?.name || 'Unknown Competition',
        entryLabel: this.entryLabel(e),
        points: r?.pointsAwarded || '-',
        rank: r?.rankLabel || 'Pending',
        notes: r?.judgeNotes || ''
      };
    }).sort((a,b) => a.compName.localeCompare(b.compName));

    const scores = this.computeScores();
    const teamScore = scores.overallTeam.find(t => t.teamId === team.id)?.points || 0;

    wrap.innerHTML = `
      <h2>Results & Performance</h2>
      <div class="card">
        <h3 class="section-title">Current Total Points (Non-General)</h3>
        <div style="font-size: 32px; font-weight: bold; color: var(--accent);">${teamScore}</div>
        <div class="muted">Check the Scoreboards tab for overall ranking.</div>
      </div>

      <h3 class="section-title" style="margin-top: 20px;">Competition Results</h3>
      <div class="table-wrap"><table>
        <thead><tr><th>Competition</th><th>Entry Details</th><th>Points Awarded</th><th>Rank</th></tr></thead>
        <tbody>
          ${displayResults.map(r => `
            <tr>
              <td><strong>${this.esc(r.compName)}</strong></td>
              <td>${this.esc(r.entryLabel)}</td>
              <td>${r.points === 'Pending' ? `<span class="tag warn">${r.points}</span>` : `<strong>${r.points}</strong>`}</td>
              <td>${this.esc(r.rank)}</td>
            </tr>
          `).join("") || `<tr><td colspan="4" class="muted">No results recorded for your team entries yet.</td></tr>`}
        </tbody>
      </table></div>
    `;
  }
  
};
window.App = App;
window.onload = () => { App.applyBrand(); App.routeHome(); };
</script>
</body>
</html>
