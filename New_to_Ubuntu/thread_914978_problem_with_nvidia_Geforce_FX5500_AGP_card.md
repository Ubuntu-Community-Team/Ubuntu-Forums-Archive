---
title: "problem with nvidia Geforce FX5500 AGP card"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by kachamanandrao on 2008-09-09
I hava a AMD athlon 2800+ processor with an AGP card model: nvidia GEFORCE FX5500, 256 MB. I tried to install 2 versions of linux, one Ubuntu 8.04 and PCQ Linux2008. In both the cases, the system after booting into linux, hangs suddenly after few minutes.
  Without the graphics card on motherboard, I am able to load any Linux version of OS and work without any problem?
  I will be grateful if any one could help to install linux with my AGP card on mother board.

---

### Post by bobnutfield on 2008-09-09
Your post is a little confusing, but I am assuming you have an ob-board video chip on the motherboard, and what you mean is that Linux will install with the on-board but not the AGP card.  If that is the case, you usually have the option to disable the on-board video in the BIOS.  I would try that.  They may be conflicting with each other.

---

### Post by kachamanandrao on 2008-09-10
Dear Bob,
  Thanks for your suggestion. You are right. Linux will install and work fine with the on-board VGA capability. But, with Add on AGP card (Nvidia ____), Linux will install but hangs after booting. I searched to disable the on-board video, But I could not do it. Please let me know, how to disable on-board video.
  Yaa, in PnP --- I got VGA choice as PCI/ AGP. I saw there, AGP was already selected. No where else I have the provision to disable onboard video?

Anand

---

### Post by hayre on 2008-09-10
I had similiar problem with GeForce 8400.  I had to use the "no ACPI" install.  Stop the install when it gives the "esc" key for options as it is loading, by  - duh - hitting the escape key.  It should give three or for options.  

NORMAL
Load if you have display problems
Load if you have ACPI problems.
(Another one?)

Choose the 3rd option and see if that helps.

---

### Post by ubunteira on 2008-10-14
Can someone tell me if this card support resolution 1920x1080 through DVI.
Will be appreciated. Thanks.

---

