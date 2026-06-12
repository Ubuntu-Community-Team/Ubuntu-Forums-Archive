---
title: "Starterbar and Gnomebar vanished"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Grimmhoff on 2008-06-18
OS: Ubuntu 8.04

I do not know how it happened. I unlocked the computer, and... the gnomebar and starterbar were gone. (Bar on top of screen with apps, system, places + date, time weather and "systray". In addition to the bottombar which shows the windows that are open on that desk. I presume the top one is the... starterbar?)

I still have access to the Terminal, which I put on the Desktop, and can still use Firefox (open random folder and Help -> Get Help Online...) and other programs if there are launchers on the desktop.

How can I get back these bars? I presume there are commands for this I can use in the terminal, but I am not sufficiently experienced with Linux to know which ones.

Another small unrelated thing: Is there a Ubuntu-equivalent for Windows' shortcut "Win+D"?

Thankyou
Grimmhoff

---

### Post by MasterSander on 2008-06-18
I think if you delete the .gnome2 folder in your home dir, it'll recover the bars.

---

### Post by tjwoosta on 2008-06-18
here is a link to another thread that i was just at (i think your solution is there)

[http://ubuntuforums.org/showthread.php?t=833173]("http://ubuntuforums.org/showthread.php?t=833173")

---

### Post by krlhc8 on 2008-06-18
Close all your important stuff and try a softrestart by pressing ctrl+alt+backspace.  May or may not work.

As for win+d, yeah, ubuntu has it:  ctrl+alt+d

:)

---

### Post by Grimmhoff on 2008-06-19
I got it to work again. I reinstalled the packages "gnome-panel", "gnome-panel-data", and installing "gnome-panel-dbg".Then I did a softreset, like krlhc8 suggested. Something that seemed to occur to others on sites I bumped into when searching for a solution to my problem: The wastepaperbin and mastervolume have both gone. Any way of recovering them?

---

### Post by krlhc8 on 2008-06-19
Hehehe, you have some learning to do with Ubuntu, don't you? :)  Right-click on the panel bar and click "Add to panel..."  A window will pop up, and you should be able to add "Trash" and "Volume Control."  While you're add it, add "System Monitor."  It's a really cool visualization of your computer activity (processor, internet, and whatever else you can add from the preferences).

As for icons on the panels, some of them are locked, which is really annoying if you're new and trying to figure out how to move icons around on the panel.  So just right click on the icons and press "k" on the keyboard to unlock them.  Right click on the icons again and press "m" on the keyboard to move them around on the panel.

---

### Post by Grimmhoff on 2008-06-19
Ah yes, I did read that suggestion when searching, but when I click "Add" (not just on trash and volumecontrol, but also sysmonitor) I get this errormessage:

The panel encvountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".

Do you want to delete the applet from your configuration.

When I click "Don't Delete", nothing happens.

---

### Post by krlhc8 on 2008-06-20
You need to install the gnome-applets package along with its dependency: gnome-applets-data.  

Open up a terminal and type:

```

sudo apt-get install gnome-applets gnome-applets-data

```

If it says that you already have them installed, then try reinstalling:

```

sudo apt-get --reinstall gnome-applets gnome-applets-data

```

---

### Post by Grimmhoff on 2008-06-20
Installing gnome-applets did it.

---

