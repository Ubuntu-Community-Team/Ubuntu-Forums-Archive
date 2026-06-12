---
title: "[SOLVED] Terminal Screen after Installing Ubuntu!"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by J_R_Jurman on 2008-11-22
I have a PPC iMac G4, and have been running Mac OS X for a really long while. I wanted to get Linux and have spent the greater part of the last few weeks looking for the right version and partitioning my drive.

I was able to install Ubuntu 8.10 through an installation disk, however whenever I boot Linux I get Terminal!

After searching the forums I found out I need to install the xserver-xorg, however after rebooting, I still got the terminal. I then tried to reconfigure xserver-xorg, but when I get to the keyboard options it pops up a postinst warning "possible overwriting-customized configuration file;" and puts me back in terminal! What do I do from here, and am I doing anything wrong!

---

### Post by NT4usB on 2008-11-22
Are you running reconfigure as root?```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
It will overwrite xorg.conf but it makes a backup copy first so it's not lost.
You might have better luck over in the Apple group (Mac is still an Apple, isn't it?)
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by apothecaryaaron on 2008-11-22
Did you get the Live desktop when you booted with the CD?

---

### Post by J_R_Jurman on 2008-11-22
> **apothecaryaaron said:**
> Did you get the Live desktop when you booted with the CD?

No

---

### Post by Elfy on 2008-11-22
Did you possibly download the server version or did you get the alternate desktop installer.

If you got the server then you can install the desktop form the terminal - run this

```
sudo apt-get install ubuntu-desktop
```

---

### Post by J_R_Jurman on 2008-11-22
> **forestpixie said:**
> Did you possibly download the server version or did you get the alternate desktop installer.

If you got the server then you can install the desktop form the terminal - run this

```
sudo apt-get install ubuntu-desktop
```

Thanks, works A-OK now! :)

---

