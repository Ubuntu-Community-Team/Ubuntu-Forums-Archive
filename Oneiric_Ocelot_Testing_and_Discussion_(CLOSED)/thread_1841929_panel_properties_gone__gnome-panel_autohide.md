---
title: "panel properties gone? / gnome-panel autohide"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chrb on 2011-09-10
I give up. I updated to Oneiric. I'm running classic Gnome (or fallback or whatever it's called). All I want to do is to autohide the top and bottom gnome-panel. Right click on the panel no longer does anything. I don't see any options in gnome-control-center or ccsm. The following command line does not work ```
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide" --type boolean "true"
```

In fact, '/apps/panel/toplevels' does not exist in gconf-editor.

Hopefully I'm just missing something obvious. But what could that be?

SOLVED! Found it: you now have to hold Alt when you right-click on the panel to get to Properties. I have no idea why they made this change. Hours of my life wasted.. Grumble..

---

