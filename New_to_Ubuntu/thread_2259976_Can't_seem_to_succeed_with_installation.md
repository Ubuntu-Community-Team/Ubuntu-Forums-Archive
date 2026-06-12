---
title: "Can't seem to succeed with installation"
date: 2015-01-08
forum: New to Ubuntu
---

### Post by Hugg on 2015-01-08
Hi.  New to linux, new to ubuntu.


[LIST]
[*]My specs home PC x64 with new Samsung 120Gb SSD. 
[*]I downloaded ubuntu 14.04.1 & burned image to Disc. 
[*]Set about installing on new SSD.  Get as far as- 'install complete - remove CD & press enter'. 
[*]On re-boot a crimson border flashes on monitor, Ubuntu logo appears for a flickering moment  - then a never-ending errie quiet.  Same result twice now. 
[/LIST]

What am i doing wrong?

---

### Post by 0N3 on 2015-01-08
What graphics card have you? AMD / Nvidia / Intel?

---

### Post by Hugg on 2015-01-08
> **0N3 said:**
> What graphics card have you? AMD / Nvidia / Intel?  Its using Nvidia

---

### Post by Hugg on 2015-01-08
Nvidia GEForce 7300 GS

---

### Post by ajgreeny on 2015-01-08
Single or dual booting?
Do you have any version of Windows as well?
UEFI or MBR system?
If you see a grub menu when you boot hit "e" to edit the correct Ubuntu entry and scroll to the line ending with something like "quiet splash". Either delete those two words and replace with **nomodeset** or just add **nomodeset** after the word splash,
Hit Ctrl+X to boot, and with luck you will get to a GUI (possibly low-res) from where you can install the nvidia properietary driver for your card.

---

### Post by Hugg on 2015-01-08
I have win 7 home premium x64.  But for ubuntu I am trying to install on new virgin SSD with win7 HDD disconnected from PC.  Install of ubutu seems to go OK.  just when i reboot first time the screen gives a quick blink or two then zilch.  From googling seems its maybe nvidea.  But I can't figure out the cure.

---

### Post by ajgreeny on 2015-01-08
Do you reboot with the HDD still disconnected?

---

### Post by whitesmith on 2015-01-08
Shot in the dark: when you installed, did you go with the option that gives Ubuntu the entire disk, or did you do the manual install and choose the parameters yourself? You still haven't replied to ajgreeny's question: UEFI or MBR system? We can't help if we have to guess! Regards.

---

### Post by Hugg on 2015-01-08
Q: Do you reboot with the HDD still disconnected?   >>>>>>>The HDD was always disconnected.  Only the new SSD is connected.  Q: Shot in the dark: when you installed, did you go with the option that gives Ubuntu the entire disk, or did you do the manual install and choose the parameters yourself?   >>>>>>>The installation was the 'express' standard way.  Never changed any parameters.  Q: UEFI or MBR system?   >>>>>I wouldn't have a clue.  I just inserted the disk & booted it & set about installing Ubuntu.  N.B. I've since installed ubuntuMATE with no problems.  Just this rosy colored version.  My question - "Does it include Nvidia drivers in the CD?  Could this b the problem?"

---

### Post by mooreted on 2015-01-08
It sort of includes Nividia drivers. More specifically, the open-source version of the Nvidia driver called "Nouveau". 

I had the same problem and disconnecting the power from my computer and plugging it back in fixed it. No idea why.

In the past when I've run into that problem I added "nomodeset" to the boot options which allowed me to load the desktop after which, I installed the Nividia driver.

---

### Post by monkeybrain20122 on 2015-01-09
Optimus machine?

---

