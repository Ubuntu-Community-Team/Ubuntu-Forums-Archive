---
title: "Handbrake keeps crashing Ubuntu 11.10"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by cajunlibra on 2012-01-15
Is anyone else having issues with handbrake crashing Ubuntu 11.10?
It keeps happening within just a few minutes of starting the process.

Handbrake 4405SVN (i686) Installed from the snapshots PPA.
Ubuntu 11.10 full install.

---

### Post by washakie on 2012-01-18
Ditto. Checking logs, and digging.

All I can say is it is a hard, cold, ugly crash.

Handbrake seems to run just fine, but somewhere during the process, the entire system crashes -- not just Handbrake.

---

### Post by JohnAStebbins on 2012-01-18
> **washakie said:**
> Ditto. Checking logs, and digging.

All I can say is it is a hard, cold, ugly crash.

Handbrake seems to run just fine, but somewhere during the process, the entire system crashes -- not just Handbrake.

System crashes of this sort are almost always a hardware problem.  HandBrake stresses the system more than most apps because it is heavily multi-threaded and very CPU intensive. Usually this kind of failure is due to insufficient cooling or dodgy memory.  Make sure all your vents are clear.  Blow out any dust from inside the cabinet. I recommend running prime95 to heat things up a bit to test for heat issues and memtest86 to check your memory.

---

### Post by syerges on 2012-01-18
Handbrake always crashed for me too... DeVeDe is ok and works but I'm hoping something better comes around.

---

### Post by OliW on 2012-07-26
Did you ever get anywhere with this?

I'm also getting crashes after a few minutes of encoding and have been for a long time. Some points of reference from me (does any of this ring true with you?):

[LIST]
[*]Intel i7 920
[*]DMRAID-using SSD (OCZ Revodrive)
[*]mdadm-using long term storage (RAID5)
[*]CPU gets hot but not too hot (~80°C)
[*]Using ffmpeg for encoding
[*]Nvidia graphics (580, binary blob driver)
[/LIST]

---

### Post by Bufeu on 2012-07-26
What version? When I installed 0.9.6 from source (there was no binary package at that time) to my 12.04-installation, it only crashed at first startup. Try 0.9.6 (or eventually 0.9.7) instead of 0.9.8.

---

### Post by OliW on 2012-07-27
Well after resurrecting this thread, it seems only fair to point out that I've found *my* problem.

It turns out heat was the issue but it wasn't the CPU temperature (by the look of things). The northbridge chipset (which has a combined passive heatsink with the southbridge) was getting too hot and it wasn't letting me know.

I fixed the whole problem by just changing how my case is cooled. It was actually just one fan that needed reversing so air could be pulled across the chipsets' heatsink.

---

