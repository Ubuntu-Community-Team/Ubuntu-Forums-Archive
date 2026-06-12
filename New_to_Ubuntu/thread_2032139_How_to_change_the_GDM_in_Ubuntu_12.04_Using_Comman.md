---
title: "How to change the GDM in Ubuntu 12.04 Using Command Line Terminal"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Invectus on 2012-07-23
Hi, I've been trying to figure out by myself for quite some time how to change the GDM to the Ubuntu 12.04 login screen. I'd like to use one of the few themes I've found.

I'm using gnome 3, instead of unity since I don't really like or prefer the Unity interface that much. I would have no idea how to change my GDM outside of using the Command Line, and prefer to use it either way.

Thanks in advance for your answers. :)

---

### Post by NikTh on 2012-07-23
Hi , 
i think modifying GDM 3.04 on Ubuntu 12.04 its not easy.. 
however i found a way.. with Gui , but if you want to try it , do it with your own risk .
[http://www.webupd8.org/2011/07/gdm3setup-gui-to-change-gdm3-wallpaper.html](http://www.webupd8.org/2011/07/gdm3setup-gui-to-change-gdm3-wallpaper.html)
If you decide to give it a try , i  will wait for feedback. 
Thanks

---

### Post by Cheesemill on 2012-07-23
Are you actually using GDM?

Ubuntu now uses LightDM as it's display manager.

---

### Post by Invectus on 2012-07-23
[FONT=Verdana]Ah, I figured out how to do this in a different way from what the guide was telling me. I don't think it was concise enough on the installation of GDM if you didn't even have it, though I will admit that it was pretty easy to figure out the next part. >>

```
linuxbox@boxy:~$ sudo apt-get install gdm
```Then it installed and I issued the command:

```
linuxbox@boxy:~$ sudo dpkg-reconfigure gdm
```

I'm about to restart now and figure out if it actually worked. :popcorn:
[/FONT]

---

### Post by Invectus on 2012-07-23
Mkay, the only problem now is that, the process of selecting a theme is impossible here on 12.04.

So what do I do now? I need a specific file known as "gnome-appearance-properties.desktop" located in /usr/share/applications. It doesn't seem to be there.

Though, here's what I found with the ls command.

gnome-appearance-properties.desktop
gnome-background-panel.desktop
gnome-color-chooser.desktop
gnome-color-panel.desktop
gnome-contacts.desktop
gnome-control-center.desktop
gnome-datetime-panel.desktop
gnome-display-panel.desktop
gnome-do.desktop
gnome-font-viewer.desktop
gnome-info-panel.desktop
gnome-keyboard-panel.desktop
gnome-mouse-panel.desktop
gnome-nettool.desktop
gnome-network-panel.desktop
gnome-online-accounts-panel.desktop
gnome-panel.desktop
gnome-power-panel.desktop
gnome-power-statistics.desktop
gnome-printers-panel.desktop
gnome-region-panel.desktop
gnome-screen-panel.desktop
gnome-screenshot.desktop
gnome-search-tool.desktop
gnome-shell.desktop
gnome-shell-extension-prefs.desktop
gnome-sound-nua-panel.desktop
gnome-sound-panel.desktop
gnome-sound-recorder.desktop
gnome-sudoku.desktop
gnome-system-log.desktop
gnome-system-monitor.desktop
gnome-terminal.desktop
gnome-tweak-tool.desktop
gnome-universal-access-panel.desktop
gnome-user-accounts-panel.desktop
gnome-user-share-properties.desktop
gnome-wacom-panel.desktop
gnome-wm.desktop

Came straight out of the terminal. :D

---

### Post by Toz on 2012-07-23
Isn&#8217;t' that it? The first one in the list?

---

### Post by Invectus on 2012-07-23
:o...

Thanks! :DDD!

//Slow.

---

