---
title: "Do I need to know anything to run drives RAID(1) mirrored (at hardware)"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-07-17
I’m learning Linux primarily to use a computer as a NAS device. My test box is comprised of salvaged parts (e.g., P-III, single PATA drive). Once I’m ready and comfortable with Linux, I’ll be getting a new batch of equipment, including two SATAs and a RAID-ready board. Since RAID will be done at the hardware level, will the Linux install/services need to be any different? (If it’s not obvious, I’ve never run a RAID array on a desktop before (there’s on in my Linksys NAS200) so please forgive me if this is painfully obvious). 

Thanks, 

Rhythm

---

### Post by cariboo on 2008-07-17
Have a look at this howto:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I used it when I set up a raid array on my server.

Jim

---

### Post by Rhythmdvl on 2008-07-17
> **cariboo907 said:**
> Have a look at this howto:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I used it when I set up a raid array on my server.

Jim

Fascinating. It looks like there are very few true hardware raid options (from following links in there). The links did refer mostly to RAID cards -- is a RAID capable motherboard basically the same thing? Since I'll be using this for accessing >50 MB files, is the speed difference between true and software raids significant?

---

### Post by cariboo on 2008-07-17
Most raid cards have a separate processor and onboard software utilities, plus they allow hotswapping if a drive goes bad. Have a look at this link, it explains the differences between hardware and software raid.

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-raid-approaches.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-raid-approaches.html)

I've had a raid array setup on my server for about a year now, on a discarded computer from a former employer, the only problem I've run into is a flaky built in network card, which has been a problem from day 1. I just replaced it with a cheap pci nic, it happily serves all my media files with out a glitch.

Jim

---

