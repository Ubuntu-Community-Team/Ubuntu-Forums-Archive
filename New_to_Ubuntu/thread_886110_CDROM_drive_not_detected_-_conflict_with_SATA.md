---
title: "CDROM drive not detected - conflict with SATA?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by RICARDO MENDES on 2008-08-10
Trying to install Ubuntu 8.04, using alternate CD. Can't even check CD for defects. I heard you can check md5sum from windows but I don't know how. Anyway, here's what happens when I try to install.   

Boots OK, select language and enter. After, the install starts detecting hardware and drives. 

The installation stops and says "no common CD-ROM drive detected" It offers me option to install drives from floppy, or manually. 

I don't have floppy drive. 

I also read there can be some conflicts with SATA hds. I have a 250GB HD sata, running windows XP on an AMD Athlon 64 x2 3800 with 1Gb ram. 

What can I do?

---

### Post by Pro-reason on 2008-08-10
Perhaps you could boot from the live CD, open a terminal, and enter the following command:

```

sudo lshw -C disk

```

Then post the output of it here.  If you want to put the output into a file, then add "*> ~/Desktop/diskinfo.txt*" to the end of the command.

---

### Post by tinker312 on 2008-08-10
I did a google search and came up with this 

> 
Okay found a work around for this I had the same issue. If you hit f6 prior to starting the install cd and append the following to the line.

hw-detect/start_pcmcia=false

This will disable pcmcia and allow the installer to continue finding yoru cdrom. I have no idea why you need to disable pcmcia I don't even have pcmcia but this fixed the issue for me. I saw a bug on launchpad about the var/log/message getting the same error messages. Well this worked for the installer as well.


courtesy of [http://ubuntuforums.org/archive/index.php/t-331224.html](http://ubuntuforums.org/archive/index.php/t-331224.html)

Maybe it will work ? :)

---

### Post by spiderbatdad on 2008-08-10
also you might try booting with the f6 option all_generic_ide

delete --quiet splash from the end of the line and type in all_generic_ide

---

### Post by RICARDO MENDES on 2008-08-10
Tried boot with both options: hw-detect/start_pcmcia=off and all_generic_ide. The install went two steps forward and then got stuck with similar problem. 

So i started installation, after the initial screen, went to the language selection step and after keyboard selection. After selecting appropriate keyboard, then install tries to detect and mount CD rom and then I go to the same as before. I can continue trying and acesss the menu with all of the install steps, including "detect and mount cd", "install deb...", "abort installation", etc.

But it all rounds up to the cdrom not detected again. 

Anything now?

---

### Post by tinker312 on 2008-08-10
> **RICARDO MENDES said:**
> Tried boot with both options: hw-detect/start_pcmcia=off and all_generic_ide. The install went two steps forward and then got stuck with similar problem. 

So i started installation, after the initial screen, went to the language selection step and after keyboard selection. After selecting appropriate keyboard, then install tries to detect and mount CD rom and then I go to the same as before. I can continue trying and acesss the menu with all of the install steps, including "detect and mount cd", "install deb...", "abort installation", etc.

But it all rounds up to the cdrom not detected again. 

Anything now?


You may have done this but instead of hw-detect/start_pcmcia=off . . . try . . .  hw-detect/start_pcmcia=[COLOR="Blue"]false[/COLOR]

---

### Post by RICARDO MENDES on 2008-08-11
yeah, Ithink I was typing off... sorry. 

Anyway, tried install with pcmicia=[COLOR="RoyalBlue"]false[/COLOR] and it goes to the "select language" screen, but then the keyboard isn't working...

---

