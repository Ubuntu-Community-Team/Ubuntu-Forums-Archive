---
title: "[SOLVED] Dvd won't play"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by misswham on 2008-07-28
I have dual boot XP and Linux.  My dvd's play in xp with all software even VLC but i cant get them to play with any sofware in Linux even VLC.  When I try to open the dvd drive i get an error message saying 

Cannot unmount volume

An application is preventing the volume 'SERIAL_MOM' from being unmounted.

This is happening with ALL dvd's.  Also i tried to RIP dvd's using Acidrip and other ripping software and those applications just stalls and freezes my pc.  I am sure that's because they arent being read for some reason.  I have to reboot in XP to get my dvd's to eject from my computer.

Can someone shed some light on this.

---

### Post by anotherdisciple on 2008-07-28
Were those cd's mounted in xp? Maybe that has something to do with it. My bet is that if you mounted it in ubuntu you could unmount it in ubuntu.

---

### Post by anotherdisciple on 2008-07-28
Oh... and about getting them to play... I would suggest you go to the terminal and type sudo aptitude install ubuntu-restricted-extras. It installs all the restricted codecs.

---

### Post by halitech on 2008-07-28
when you try to use VLC, are you clicking the X to close it or do you go File - Exit?

also, have you installed all the multimedia codecs and restricted extras?

---

### Post by WRDN on 2008-07-28
If DVD playback fails, run the following command in the Terminal:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

You should also install the restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

---

