---
title: "Boot Issue - Win7 Installed after Ubuntu"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by Bialetti741 on 2014-04-22
Hi, i'm a new user of Linux using Ubuntu for first time.

I'm using Ubuntu 13.10 (Kernel: 3.0.11.19) as my main OS on my primary HDD (SATA 0 - on Motherboard).

Worried i'd delete my new Ubuntu OS, i disconnected my primary HDD and then installed Windows 7 on another HDD (just as a backup just in case i can't do something on Linux that i know how to do on Windows while i'm learning Linux).

I reconnected my primary drive and rebooted my PC expecting to see the uBuntu screen, but Windows has now taken over as 1st OS to boot.

I've been into my BIOS and told it to boot Ubuntu 1st, then Win7, then DVD drive.

It's still booting Windows with no easy way of getting Ubuntu to boot.

I have managed to get ubuntu to boot by going into BIOS and double clicking the HDD i know it's stored on.

Is there a way for me to get Ubuntu to start first again with Win 7 (as a listed option in Grub) without going into the BIOS every time?

Note: I would like to keep both OS's on separate HDD's for now, so i don't really want to use Dual Booting off same HDD or use Virtual box.

Any assistance would greatly be appreciated.

---

### Post by migs73 on 2014-04-22
Have you tried removing the Win7 HDD and see if you can still boot Ubuntu? This will tell us if Grub ( the Linux bootloader) is still Okay.

Mike :)

---

### Post by Bialetti741 on 2014-04-22
Thanks Mike (migs73), i'll try that tonight and let you know.

Thanks,

Robert

---

### Post by nns2006 on 2014-04-22
I would suggest to use "live cd" method. I think if you reinstall "grub" it will solve this problem.

---

### Post by migs73 on 2014-04-22
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
:)

---

### Post by Vladlenin5000 on 2014-04-22
IMO, you don't need to go live... Here's why:
Considering you installed Windows in a second physical drive - hopefully with the primary disconnected because, you know, Windows... - then it should be possible to boot Ubuntu directly by having the boot order in BIOS with the first HDD as the first boot device -> It should boot into Ubuntu directly without giving you the change to choose. Don't worry... As long as you can boot into Ubuntu and having both drives connected just do in a terminal:
```
sudo update-grub
```

By now GRUB should have been updated in order to include the newly installed OS - Windows - in its list.

---

### Post by Bialetti741 on 2014-04-22
Hi Vladlenin5000, many thanks for your suggestion. Unfortunately it's just the same....Windows still taking over.

---

### Post by Bialetti741 on 2014-04-22
Hi Mike, I removed the HDD with Windows installed and rebooted.....Ubuntu boots no problem.

---

### Post by Bialetti741 on 2014-04-22
Thanks nns2006, i tried this and it got Ubuntu back as the default OS at startup, but because i had forgot to re-connect the HDD with windows on it from trying the suggestion form migs73 it didn't give Windows as an option in grub. I reconnected the Windows HDD and repeated your method but if failed during the Terminal commands (forgot which one). But long story short i managed to fix it with a program called "Boot Repair" that i came across when googling for a resolution. Problem now solved. Thanks again to eveyone for their help, much appreciated. Robert

---

### Post by migs73 on 2014-04-22
Solved = Good Result no matter how you get there.

Welcome to the Forum (and Ubuntu) by the way :)

---

