---
title: "My interface disappeared"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by marinecomm on 2008-08-24
I am using Ubuntu 8.04 LTS and today the bar at the top and bottom of the screen disappeared. I am not sure what you call it and how to search for the problem. I can use the icons that are already on my desktop, but I cannot access anything else on my computer.

---

### Post by Crafty Kisses on 2008-08-24
Try reconfiguring your X, you can do that by doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```
This also sounds like a video card driver issue, post the following output of:
```
glxinfo
```

---

### Post by SunnyRabbiera on 2008-08-24
They are called panels if you are wondering.
Sometimes they dont appear, dont worry as when you hit control-alt-backspace it should log you out and when you log bavck in you may get them back
I have had the panels crash on me a few times, that normally worked.

---

### Post by marinecomm on 2008-08-24
I can't do what you ask because I cannot access any of the applications, files, folders, the terminal, etc on my computer. I only have a couple of icons on my desktop and those are the only programs I can access. I tried to repair the x server by booting up in recovery mode but that didn't work.

---

### Post by marinecomm on 2008-08-24
I have restarted and shut down several times and they still won't appear

---

### Post by meanburrito920 on 2008-08-24
Actually, it sounds more like you just had a problem w/ gnome-panel. can you open a file browser by clicking a link on your desktop? if you can, then navigate to usr/bin/gnome-terminal and run it. then once you have a command line up, run 'gnome-panel'. this should bring back your panel. then go  into your Preferences > Sessions menu and add gnome-panel to have it start with login. That should solve all your problems

---

### Post by SunnyRabbiera on 2008-08-24
> **marinecomm said:**
> I can't do what you ask because I cannot access any of the applications, files, folders, the terminal, etc on my computer. I only have a couple of icons on my desktop and those are the only programs I can access. I tried to repair the x server by booting up in recovery mode but that didn't work.

Well as I said try control-alt-backspace
also try alt-f2

---

### Post by meanburrito920 on 2008-08-24
If you cant access the file browser through a link on your desktop, then right click > add new folder, then open the folder to get a browser.

---

### Post by Flyingjester on 2008-08-24
hit alt+f2, then type in gnome-panel, that should bring it back

---

### Post by meanburrito920 on 2008-08-24
@flyingjester- I dont believe that would work because the TTY terminals are effectively sepparate from the X server- commands run on them that require X will fail because they are not associated with the X server- they are like a completely different login, with nothing but a terminal.

---

### Post by marinecomm on 2008-08-24
somehow it got uninstalled. that's one thing I really don't like about ubuntu, too easy to delete something important to the OS. I resinstalled and it is back but I got three error messages:

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

It's asking me if I want to delete these applets from my configuration

---

### Post by Flyingjester on 2008-08-24
> **meanburrito920 said:**
> @flyingjester- I dont believe that would work because the TTY terminals are effectively sepparate from the X server- commands run on them that require X will fail because they are not associated with the X server- they are like a completely different login, with nothing but a terminal.

ah, i thought his x server was working.. seeing as how he said he can still use the icons on his desktop.

---

### Post by meanburrito920 on 2008-08-24
OK, dont delete them. WHen you restart gdm these errors should go away. try rebooting your computer (this same issue happened to me when gdm had problems).

---

