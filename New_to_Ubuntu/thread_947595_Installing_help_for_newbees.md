---
title: "Installing help for newbees"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by dennisflysjets on 2008-10-14
Dear Forum experts,

We have a Toshiba Satellite Laptop with XP and no recovery disk.  When we try to boot it up, we get a message "System file is corrupt, press R to repair with disk".  Of course, we can't.

We've tried to install Ubuntu from the CD.  It goes through the 8 steps (the mouse works on the PS2 port)and then it hangs up on the "Installing System" screen at 15%.  The hard drive light is not flashing.  It's locked.

How should we proceed? We don't care about it being partitioned or recovering XP or even reformatting the HD.  Whatever it takes.  We just want to make it a working computer with Ubuntu.

Do we retry or is there another choice in the installation process that we need to make?

Please advise.

Dennis in Texas

---

### Post by hyper_ch on 2008-10-14
if you want to install ubuntu then try it with the alternate install cd.

What are the specs of that notebook? CPU, ram, video card, ...?

---

### Post by LowSky on 2008-10-14
from the ubuntu live CD you can reformate the hard drive, try that first before installing ubuntu.

from the menu, System, Admin, Partition editor (aka Gparted)

---

### Post by ByteJuggler on 2008-10-14
Some further comments/questions to what others have said:

1.) Have you verified the installation CD (MD5 checksum/CD verification option on boot menu)?
2.) Have you run the memory test for a reasonable amount of time (say at least half an hour) with no failures so you have some confidence that the machine's RAM is OK?
3.) I would do some sort of disk test before installation to ensure there's not hidden hard disk problems that might cause trouble.  Ideally you could use a manufacturer diagnostic CD for the type of hard disk in the machine. Alternatively there's several tests you can do even just booted from the Ubuntu liveCD (or a rescue CD.)

As you can tell I'm suspicious of the machine's hardware possibly having developed some problem.  What killed/corrupted the XP in the first place?

---

