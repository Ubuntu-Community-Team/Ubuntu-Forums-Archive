---
title: "Problem installin ubuntu studio 8.04"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by rajaram_s on 2008-05-27
I am trying to install ubuntu studio 8.04 using the 800+ MB DVD image that I downloaded from the one of the ubuntu mirrors. When I tried installing in the text installation mode, it was able to install the base system properly. The next step of installing additional softwares returned an error saying it could not be read from the disk. I hence skipped the step and installed the GRUB boot loader (I dual boot it with windows xp). The GRUB also got installed properly. When I tried to boot through ubuntu, it started to boot in the text mode, as if I was booting in the recovery mode. It asked for the user name and password and I gave it too. Once the prompt came I gave the command startx to start the x window system and it said, command not found. Does it mean my ubuntu is not installed properly? Is there any way I can boot into the system? or if I cant how do I remove the GRUB?

---

### Post by Drunky on 2008-05-27
First I would try:

```
sudo apt-get install ubuntu-desktop
```

If this doesn't not get you the desktop then I would try to re-install.

Boot into Windows XP and checksum the ISO image.

If the ISO is okay, then re-burn the DVD at a slow speed.

If not, then re-download the ISO and start from the top again, i.e. check the iso, burn the iso).

Re-install Ubuntu Studio on the same partition that is already there.

---

### Post by rajaram_s on 2008-05-27
The problem is I dont have the iso with me... I only have the disk instead.... Possibly the disk is corrupted....I will try downloading a new image and check it out...

---

### Post by sayakb on 2008-05-27
It's better that you download and install Ubuntu and install Ubuntustudio desktop upon it. That would provide you a proper LiveCD + official support + Ubuntustudio apps. 
Ubuntustudio = ubuntu + some media apps + dark themes ;)

---

### Post by rajaram_s on 2008-06-02
I then got a new image (ubuntu 8.04 Hardy), wrote it on a CD/RW disk... (will there possibly be any problem if I write it to a CD/RW?) I checked the CD for defects and it said no defects... when I start the install, beyond an extent while copiying files, it just gets hung... It doesnt even get me an error message... any solutions?

---

