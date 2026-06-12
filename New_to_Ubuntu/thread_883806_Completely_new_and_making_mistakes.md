---
title: "Completely new and making mistakes"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by i3igi3yrd on 2008-08-08
So I bore with the Windows that I work on everyday at my job. I've grabbed a copy of Ubuntu (8.04) and got it installed on an old Dell. Getting straight to the point - I've attempted to do some customizing on the desktop and I've deleted the top panel. I have recreated the panel, but can't figure out how to get "Applications" and the other drop downs back up on the panel. Help for the n00b anyone?

---

### Post by drs305 on 2008-08-08
Right click on the panel, then Add to Panel. You can add individual items or select Main Menu, etc. You can also open any of the main menus and simply drag them to the panel and release to create a shortcut.

Welcome to ubuntu!

---

### Post by silkstone on 2008-08-08
Right-click on the panel and select Add to Panel. Then you can look through the list of applications and add what you want to the panel.

Most applications (as opposed to utilities) are in the Applications Launcher section of 'Add to Panel'.

---

### Post by tuxxy on 2008-08-08
Just right click on your panel and select **add to panel** now from here you can add all your old menus, for example to add the main applications menu again, double click **Main Menu** icon

---

### Post by decoherence on 2008-08-08
if you ever mess up GNOME so badly you want to start from a clean slate, press Alt F2 and type gnome-terminal

in the prompt that comes up type

```
mv ~/.gnome2 ~/.gnome2BACKUP
```

log out and log back in and you have fresh, clean gnome! If you want to restore your old messed up settings, just do the above command in reverse 

```
mv ~/.gnome2BACKUP ~/.gnome2
```

You can also do this from the GUI. In a Nautilus window, under the View menu select "Show Hidden Files" then rename the .gnome2 directory.

---

### Post by SunnyRabbiera on 2008-08-08
Sure.
In the top panel add these following apps by right clicking on the panel and selecting "add to panel":
Menu bar (the main menu)
Notification area
Clock
Quit

That will set you up with most of the default apps in the top panel.
Additionally you can add:
Volume control
Deskbar applet
User switcher
and you can create a quicklaunch of sorts in your panel by going into you applications menu and selecting your favorite app and right clicking it and dragging it to the panel.

---

### Post by i3igi3yrd on 2008-08-08
I've got the application Icon back up there, but how do I get the actual word "Application" back up there? I know this seems rather elementary, but if I can figure out the simple stuff now, I'll be able to expand on it later (so is my thinking....)_

---

### Post by i3igi3yrd on 2008-08-08
Additionally, if i wanted to link directly to what would be an exe, where would these be located?

Comparison to windows: C:/Program Files/(insert program name)

---

### Post by Vorian Grey on 2008-08-08
> **i3igi3yrd said:**
> I've got the application Icon back up there, but how do I get the actual word "Application" back up there? 

There are two menus in there, the main menu and the main menu bar (or something like that, they're called different things in different distros). The other one puts applications, places, and system back on there.

---

