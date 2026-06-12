---
title: "Does Wubi even work, at all?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by dacium on 2008-07-22
I have not got wubi to work on 3 different system I have tried.

The first system (a HP pavilion laptop core2duo) refused to boot windows xp. It would seem to find NTldr, but the boot up process would freeze just after that. Went away as soon as I fixmbr, fixboot. I could get to ubuntu ok though.

Second system a desktop PC (sata2 HDD, amd4800+x2, A8NSLI) loads windows XP ok, but fails to load ubuntu claiming it cant find a partition. After this if you select winxp without rebooting, it cant find ntloader. I can run windows XP fine though.

3rd system completely fails to even find a master boot record at all after wubi installed, it is a xp2000+ ga7dx with IDE 120gb drive. Had to fixboot/fixmbr to get windows to boot again.

---

### Post by fidamehran on 2008-07-22
That is not supposed to happen. Are you sure that your Windows XP installation was healthy? If so, it should have been worked okay.
I'd advise you to reinstall Windows XP through an installation disk and reinstall Ubuntu through Wubi from Ubuntu CD (Wubi is there in the CD). That should fix your Windows system files (if any of them were corrupted) and then give a clean platform for Wubi and Ubuntu to work on. There should not be any issue of partitions as it is a virtualized partition inside the Windows partition, not an actual physical one.

P.S.: Where you are being able to boot into Windows, first unintall Ubuntu from Add/Remove before reinstalling Windows and Ubuntu. If that is not possible, delete the X:\Ubuntu folder (X is the drive where you installed Ubuntu) and all entries of Ubuntu in Registry (Start-->Run-->regedit) before reinstalling Windows and Ubuntu.

---

### Post by L Campbell on 2008-07-22
> **dacium said:**
> I have not got wubi to work on 3 different system I have tried.

The first system (a HP pavilion laptop core2duo) refused to boot windows xp. It would seem to find NTldr, but the boot up process would freeze just after that. Went away as soon as I fixmbr, fixboot. I could get to ubuntu ok though.

Second system a desktop PC (sata2 HDD, amd4800+x2, A8NSLI) loads windows XP ok, but fails to load ubuntu claiming it cant find a partition. After this if you select winxp without rebooting, it cant find ntloader. I can run windows XP fine though.

3rd system completely fails to even find a master boot record at all after wubi installed, it is a xp2000+ ga7dx with IDE 120gb drive. Had to fixboot/fixmbr to get windows to boot again.

FWIW, it worked absolutely faultlessly for me, on a PC and, trust me, I am a REAL dunce at computer stuff.

---

### Post by Paqman on 2008-07-22
Have you confirmed that all those systems run a LiveCD session of Ubuntu happily?

---

### Post by halitech on 2008-07-22
I've used it flawlessly on an old compaq armada to install Ubuntu and Xubuntu so it should work fine on your systems with them all being newer. Only one I could see giving a problem would be the machine with the SATA drives

---

### Post by dacium on 2008-07-23
The only thing I can think of is that they are all xp sp3. Two of them fresh and one of them updated from sp2. They all run the live CD ok.


From what i could work out wubi chucks a fit if you don't pick ubuntu to the load the first 3 or 4 times. After that its ok.

---

### Post by dacium on 2008-07-23
THese were unattended installs so each time they rebooted they defaulted to windows XP and loaded windows XP even for the two reboots inbetween for wabi installing ubuntu. Maybe this is why.

---

