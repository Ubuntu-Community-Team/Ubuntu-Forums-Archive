---
title: "Installation fails. EDD: Error 1000 reading sector"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by destro2k on 2012-09-20
Dell 4400
Bios Version A06
Pentium 4 1.6Ghz
Memory 256MB
HD 40GB Maxtor 6E040L0 (this is not the original HD. the drive is definitely working and I wiped it with dban)
Optical Drive NEC CD-RW NR-7900A


Here is my error:

EDD: Error 1000 reading sector 347635
EDD: Error 1000 reading sector 346669
gfxboot.c32: not a COM32R image
boot:
_

Eventually the installation reaches the Xubuntu 12.04 .... screen. The dots continue blinking endlessly. I know my xubuntu installation CD is good because I have used it successfully on other computers.

---

### Post by daslinkard on 2012-09-20
I've seen similar errors in the past which were actually caused  by a bad cd/dvd drive.  Chances are the disc is good itself but the drive may be going out.

Do you have the ability to install via USB?

---

### Post by mips on 2012-09-21
Try this [http://askubuntu.com/questions/92631/installation-problem-bootlogo](http://askubuntu.com/questions/92631/installation-problem-bootlogo)

---

### Post by destro2k on 2012-09-21
Wow that worked. I changed the optical drive. Installation has progressed much farther along. Now I'm getting a new error:

The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.


After the desktop session begins I double click on the installation icon. The optical drive spins up and down endlessly. The system seems to be busy so I can't move the mouse. Nothing ever happens. No further progress.


Mips
I don't know what grub is. I will search the forum for how to modify it setting edd=off as your suggest. Thanks.

---

### Post by destro2k on 2012-09-21
I researched grub and now have a beginner's understanding of it. I learned how to update it but how can I update grub prior to installing xubuntu on the system? Do I still need to update grub now that the problem has changed to:


The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.


After the desktop session begins I double click on the installation icon. The optical drive spins up and down endlessly. The system seems to be busy so I can't move the mouse. Nothing ever happens. No further progress.

---

### Post by destro2k on 2012-09-23
I changed the optical drive a second time and I used the xubuntu alternate install CD. Success...xubuntu installed. I don't know which of the two did the trick but I believe it was the alternate install CD because the first time I changed the optical drive the installation made much more progress even though it would not complete.

---

### Post by daslinkard on 2012-09-23
> **destro2k said:**
> I changed the optical drive a second time and I used the xubuntu alternate install CD. Success...xubuntu installed. I don't know which of the two did the trick but I believe it was the alternate install CD because the first time I changed the optical drive the installation made much more progress even though it would not complete.

Glad this was resolved for you....anytime you need anything we're here in the forum for you!  Thanks!

---

