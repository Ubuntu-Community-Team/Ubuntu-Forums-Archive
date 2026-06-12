---
title: "not quite Installing yet"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by ERGOtruth on 2008-06-30
I'm trying to install World of Warcraft, following this guide,

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I have installed wine, and have copied the relevant files from all the disks into a folder called wow_install, including DirectX, Autorun.inf, Installer.exe, Installer.ico, Installer Tome.mpq, installer Tome 2.mpq, Installer Tome 3.mpq, Installer Tome 4.mpq, and Installer Tome 5.mpq.



I paste

cd /desktop>wow_install/
wine Installer.exe

into terminal, and it immediately gives me

cd /desktop>wow_install/
bash: wow_install/: Is a directory
ergo@ergo-laptop:~$ wine Installer.exe

this is looking pretty good to a new guy like me so far, but when I run it I get

cd /desktop>wow_install/
bash: wow_install/: Is a directory
ergo@ergo-laptop:~$ wine Installer.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
ergo@ergo-laptop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report







thanks for any help anyone might be able to offer.  This is the first time I have tried to use wine for something, and I am very new to ubuntu in general.  The computer was running OS X before I installed ubuntu.  It's one of the newer white laptops.

---

### Post by Marshal0505 on 2008-06-30
If i were you i'd check the wine section of this forum for additional tips regarding running WoW under wine.Solved all my problems.

---

### Post by coolaj86 on 2008-06-30
> **ERGOtruth said:**
> 
cd /desktop>wow_install/
wine Installer.exe


that should be cd ~/Desktop/wow_install, I'm pretty sure.

cd - change directory
/ - ROOT (not root the user)
~/ - HOME, ie /home/YOU_USER_NAME
> - puts information into a file
CaPS maTTer! 'Desktop' is not the same as 'desktop'

You need to 'cd' into the directory where the WoW installer is and then run
wine Installer.exe

Where did you create the wow_install folder? Is it on your desktop.

If you want to become more familiar with the way Linux works try taking a look at this: [http://www.linuxcommand.org/lts0020.php](http://www.linuxcommand.org/lts0020.php) . 

There is a better guide, but I can't find it ATM.


I don't know how much you understand about using a terminal or the way Unix (OS X) and Linux work so if this isn't helpful I'll post again and try to make it simpler.

---

