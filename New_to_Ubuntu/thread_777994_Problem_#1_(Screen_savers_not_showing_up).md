---
title: "Problem #1 (Screen savers not showing up)"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Digital Hick on 2008-05-01
My first post, greetings to all.

I recently installed Xubuntu 8.04 LTS and the screen savers are not displaying.  The amount of time I set before they come on seems irrelevant as the computer waits 10 minutes and then turns the screen black no matter what I set it too.  The power management settings are not the problem as they are set way to high to cause trouble.  Any suggestions would be appreciated.  :popcorn:

Update:
I tried what I found in this [thread]("http://ubuntuforums.org/showthread.php?t=777274") but it did no good at all.

---

### Post by Digital Hick on 2008-05-01
Bump

---

### Post by Digital Hick on 2008-05-01
I went on another search and found this [thread]("http://ubuntuforums.org/showthread.php?t=773492").  I checked my Xorg log file for warnings or errors but there was nothing like what that thread showed. 
:confused:
My card is listed as a 
```
VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```

---

### Post by Wangsta on 2008-05-05
I have the same problem.
I see all these freakin awesome screensavers, but my computer never goes to a screensaver, no matter how long I wait....

---

### Post by Digital Hick on 2008-05-06
[INDENT][/INDENT]I checked the configuration files, thinking that the -root switch on the one command was wrong but that is not it.  The screen savers appear and work in the screen saver config gui from the xfce control panel but when it comes show time its all fizzle.  
[INDENT][/INDENT]While I am on my podium I have to say that my xubuntu experience in general has been a bit of a let down.  I was expecting xfce to be totally different than GNOME, but it appears that it is some kind of mix of GNOME and xfce.  And just to put it on the record I am not referring to the fact that both are built with GTK, I understand that, but xfce's own native apps aren't used.  It seems to me that kubuntu and xfce are just the neglected children, if you want it all and want it to work you have to have GNOME-based Ubuntu:neutral::-?:-|:-(

---

### Post by cwgatling on 2008-05-06
I was having the same problem too (xubuntu 8.04). I chose a screensaver from 'Settings, Settings Manager, Screensaver' and kept getting a black screen when I should have been seeing Metaballs :popcorn:
If I go through the menus 'Settings, Screensaver' instead, and choose it there, it works. They're completely different menus and this (the xscreensaver one) seems to take precedence, because mine is working now. 
You may have tried it already but just in case...

---

### Post by RumorsOfWar on 2008-05-07
Thanks cwgatling.:)
I had that problems too, when I went through the applications menu, it found the screensaver daemon was not running and started it.

---

### Post by Digital Hick on 2008-05-09
Well thank you for posting ROW and cwgatling, I'll have to try that sometime.  As it is now I got frustrated with Xubuntu and switched to the Ubuntu.  Screensavers work, fonts are not weird and low resolution and no need to download a half dozen apps after each install.  Xubuntu is nice but I don't know how it is 'smaller' than the main distro,:confused: it eats as much RAM and takes up nearly as much hard drive space on the machine i tried it on.  I know that doesn't sound logical but that is what it looked like.  The only thing that is smaller is the iso file.  Things are better in Linuxville now.:)

---

