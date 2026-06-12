---
title: "dash is broken for me"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jcphil on 2011-10-08
When I open my browser in a workspace, I can't get dash to show by moving my cursor to the left edge of the screen. That used to work, but nothing happens now. And if I press alt-tab, it also does nothing...unless I press that combination thirty or forty times in rapid succession. Then the browser minimizes and I can use dash to switch workspaces, etc. I have loaded updates daily for the past week, but it's been broken each time. It seems like the browser overlays everything and prevents me from seeing dash or the application switching window that comes up with alt-tab. Has anyone else had this problem?

---

### Post by MG&amp;TL on 2011-10-08
IDK, but file a bug on launchpad.

---

### Post by jbicha on 2011-10-08
"Stacking" bugs have been a persistent issue during the Oneiric development cycle. Quite a few of these bugs have been fixed but the launcher on the left still sometimes hides behind everything. There's at least a partial fix coming next week. As a workaround, run unity either from Alt-F2 (if my dash is hiding, I use Ctrl+Alt+arrow keys to switch to an empty workspace) or from a terminal. This will restart Unity and for me at least, that restart helps.

---

