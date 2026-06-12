---
title: "problem with panels"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Brianspilner on 2008-05-12
hey i m using ubuntu hardy,

every time i start it, I cant find the panels the way i left. I adjust and move them, but every time i restart their positions are changed. what can i do to fix them properly?

thanks

---

### Post by zvacet on 2008-05-12
If I understand you correctly just right click and lock on panel.Did you think of something else?

---

### Post by wayno on 2008-05-12
Try right clicking on each separate icon and making sure the "Lock to Panel" box is checked, it worked somewhat for me

---

### Post by Brianspilner on 2008-05-12
well no icons are fixed &#305; am talking about whole panel. let me put it this way, ihave both panel at the bottom of the screen, when i start the panel with applications-places-sstem etc. is at the top of the panel with tray where apps are minimized. so i change them upside down, but when i re login they re back to same postions

---

### Post by N.N. on 2008-05-12
That's odd. If you use the session dialogue to shut down the computer, your panel configuration should be saved. If that doesn't work out, however, you could try editing the configuration to your liking using [FONT="Courier New"]gconftool[/FONT]:

[LIST=1]
[*]Open a terminal and type the following command to place the "bottom panel" at the top of the screen: ```
gconftool --type string --set /apps/panel/toplevels/bottom_panel_screen0/orientation "top"
```
[*]Then type the following command to place the "top panel" at the bottom of the screen: ```
gconftool --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "bottom"
```
[*]Close the terminal, log out using the session dialogue, and log in again to see if the panel configuration is still to your liking.
[/LIST]

If the panel configuration hasn't been saved, a temporary solution to your problem could be to make a backup of your configuration which you could then load once GNOME reverts to the default configuration:
[LIST=1]
[*]First, configure the panels to your liking.
[*]Then open a terminal and type the following command to backup your panel configuration: ```
gconftool --dump /apps/panel > my-panel-settings.xml
```
[*]If GNOME later reverts to the default panel configuration, run the following command in a terminal to make it use your backup file instead: ```
gconfool --load < my-panel-settings.xml
```
[/LIST]

---

### Post by Brianspilner on 2008-05-15
unfortunately not working...

---

### Post by rune0077 on 2008-05-15
This seems to be a recurring problem these days. I think the fix is, note down everything that is on the panel that is bothering you (all the icons and apps and menus on it), then right-click and delete the panel.

Then right click your other panel and select "New Panel". Place the panel where you want it, and then add everything to it that you have noted down (right click it and select "add to panel").

Weird way to go about it, but it might help.

---

