---
title: "x  windows looks funky"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by saintj0n on 2011-12-04
I typed startx on my new ubuntu 10.04 server and get a white square on the upper left hand corner of the screen.  You can also see a prompt on the screen but it doesn't let you enter anything and shouldn't be there anyway!  I installed x just previous to running startx but didn't configure video.  How can I troubleshoot this?:confused:

---

### Post by saintj0n on 2011-12-04
*UPDATE

I booted off of a Linux Mint Live CD and the GUI came right up.  Is there a way to copy the video configuration from the Linux Mint CD to USB pen drive and boot into Ubuntu server and copy it over?  It doesn't seem too complicated, I just don't know exactly how to do it.  

Btw, I looked for xorg.conf on the Linux Mint CD and didn't find it.  However, I am a Limnux Noob and may not know where to look.

---

### Post by lolpenguin on 2011-12-05
Firstly, X Windows is a misspelling of _X Window System_. Don't worry, many people do this. I don't think Ubuntu uses startx anymore...try this
```
sudo gdm
```

---

### Post by The Cog on 2011-12-05
I don't think xorg.conf is used any more - it should all aoutoconfigure these days.

Since you are new to Linux, I would suggest that you install a desktop version which will get you a working system quickly.

If you really want to proceed with the server installation, you could try installing a desktop package. For servers, Lubuntu will probably do you - I guess you only want the GUI for occasional management, and LXDE is said to be th emost lightweight. This may do the trick:
**sudo apt-get install lubuntu-desktop**

---

### Post by aeiah on 2011-12-05
startx will launch whatever it finds in ~/.xinitrc. if ~/.xinitrc is empty it'll try and launch a desktop environment / window manager you have installed. if you haven't got one installed, it'll launch X just with XTerm, a terminal (the white square you see).

you could install a window manager for xinit to pick up and use (such as openbox, awesomewm, etc) but things will be less painful if you install a standard desktop environment. either the default one, or something more lightweight like lxde or xfce. it'll install a lot of other apps as well though (office software, file browser, web browser, music player etc), so if you really dont want this, have a look at some tutorials for installing just a bare-bones desktop environment without the additional software.

---

### Post by saintj0n on 2011-12-05
So if I install a desktop environment I still have the server capability right?  It won't wipe anything out will it?

---

### Post by The Cog on 2011-12-05
Server capability is a Microsoft invention to charge more for their "server" version than their deliberately crippled desktops.

In Ubuntu, the server version does actually have a slightly tweaked task scheduler to make it more optimised for server type loads than desktop loads - the GUI is slightly less responsive as a result, but I doubt it's anything you would notice. But the desktop version isn't crippled like windows - no artificial limits on how many connections/processes whatever. The main difference is that the server version doesn't come with a GUI, and the installer asks if you want to install web, sql servers etc. In the desktop version you install those after completing the basic install.

---

### Post by saintj0n on 2011-12-05
ahh..perfect. Loaded Lubuntu and it fired right up.  Now all I have to do is read and learn and experiment until I am the server master.:D

---

