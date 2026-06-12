---
title: "k9copy not showing in Unity launcher"
date: 2011-07-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by watsbe on 2011-07-29
I tried to raise a bug, but ubuntu-bug crashed.
I installed k9copy, but it does not appear in the Unity menu. Works OK from a terminal.
I'm not sure if it is related, but when I run k9copy --assistant, the dialog box appears off the top left hand corner of the screen and I can't get it down into the screen. Any ideas?

---

### Post by mc4man on 2011-07-29
If you want to add one or the other to the launcher then browse to /usr/share/applications/kde4 and d. click on the .desktop, then pin in launcher
Otherwise you could add as quicklist entries to existing 'icon' or make a .desktop for both

If wanting to see in the dash > multimedia then ATM easiest to copy one or both desktops to an application dir.,   ~/.local/share/applications would work fine, will show after a log out/in

The opening in the corner stuff is probably from a compiz plugin, you can disable, no big loss. Run ccsm and disable the "Dialog Handler" plugin

Edit: 
for a standalone icon that did k9copy on the left click and both available from the r click I'd just do this

 ```
mkdir -p  ~/.local/share/applications && \
gedit ~/.local/share/applications/copydvd.desktop
```

Paste this into gedit, save and close gedit
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=k9copy
Exec=k9copy -caption "%c" %i %m  %u
Comment=DVD9 to DVD5 backup tool
MimeTypes=
Terminal=false
Icon=k9copy
X-DocPath=k9copy/index.html
Categories=Qt;KDE;AudioVideo;DiscBurning;
X-Ayatana-Desktop-Shortcuts=K9CopyAssistant;

[K9CopyAssistant Shortcut Group]
Name=K9Copy Assistant
Exec=k9copy --assistant -caption "%c" %i %m  %u
TargetEnvironment=Unity

```

```
chmod u+x ~/.local/share/applications/copydvd.desktop
```
```
nautilus  ~/.local/share/applications
```
D. left click on the k9 icon - then pin to launcher when icon shows
 A log out/in will set the quicklist

---

### Post by watsbe on 2011-07-29
Fabulous. All my problems solved! Thank you.

---

