---
title: "RAID 0 Problem"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by soisoisoi on 2008-10-27
Originally I had vista x64 running on one harddrive as my C: drive and two 250gb HDs running RAID 0 as my D: drive. The RAID worked fine at this time. Recently I have needed to install linux to run some software for a project I'm working on.

After much faffing, I managed to get vista x64 and ubuntu 32bit 8.04.1 (software I need doesn't like x64) on the same harddrive. Using easyBCD I managed to get them both to boot properly by pointing menu.lst to the right hds/partitions. However, no matter whether I install linux first or vista first, when I boot into vista after booting linux, the software RAID cannot be accessed.

Whenever I do start->run->D: windows asks me to reformat the HD. Also in disk manager the 2nd of the RAID disks is not initialized.

I must stress that there is data on my RAID that I do not wish to lose and currently the only way to recover the RAID that I know of is to reinstall vista. Obviously this is a less than desirable situation :P 

I am using a Gigabyte GA-965P-DS3 rev 1.0 mobo and the RAID requires drivers from Gigabyte's website to work, so I guess this is a software RAID.

I have read many of the posts related to RAID on these forums but most of them appear to be about starting a new RAID or installing linux on a RAID. My real question is that if I use dmraid or mdadm or whatever it is, will I be formatting the RAID?

To clarify:
1) I do not require the RAID to work on linux, only windows.
2) Initially, after a vista install, the RAID works fine. Once I boot into ubuntu and then back into vista it does not.
3) Do I need to setup a software RAID in ubuntu to fix this problem?

I realise this may be more of a vista question than an ubuntu question but I would appreciate any help you can offer.

---

