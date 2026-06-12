---
title: "Ubuntu NAS Hard Drive Configuration"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by jmf421 on 2015-10-09
[COLOR=#000000]I am looking to run Ubuntu Desktop on a NAS I built. I am not too good with command line stuff so I prefer this over the Ubuntu Server. [/COLOR]

[COLOR=#000000]Currently I have (2) 2TB Hard Drives and was curious to the best setup that can also scale if I were to add an additional hard drive.[/COLOR]

[COLOR=#000000]Do I install Ubuntu on one of these drives or do you recommend getting a small 64GB SSD to install the OS on? Then I could use the larger drives for storage only. [/COLOR]

[COLOR=#000000]Or do I just pool everything together with some type of RAID setup? I am pretty new to all of this and mainly use my NAS for streaming media throughout the house and holding backups from multiple computers.[/COLOR]

---

### Post by TheFu on 2015-10-09
Desktop code introduces extra RAM, CPU, and security considerations. Whatever. Sounds like you've considered those risks already.

Don't use RAID. RAID is for high availability and NOT useful in a home environment, unless you just want to do it for knowledge - as a career skill.  RAID is a good way to have corrupt data written in 2 places concurrently. RAID solves about 3 problems. Backups solve about 1000 problems. Hope that makes sense.

I would partition the two disks with 1G swap, 25G for / and the rest for LVM.  Be careful using LVM to span disks. That is a good way to lose all the data on both drives. Backups are fine, but don't forget that we need 3 copies of really important data on different media and 2 copies of nice-to-have data on different media to be a useful backup.

By keeping the drives partitioned identically, life will be easier when 1 of these disks fail. Think through what will happen if/when 1 disk fails. They always fail - my goal is to be done using a disk before it fails with important data on it.  ;)

---

### Post by jmf421 on 2015-10-09
Thanks for the reply! I am sure Ubuntu server is better for low end systems and use less resources but I feel with my hardware and limited knowledge and patience for command line, I will be fine. Here is my setup:

Fractal Design Node 304
ASUS H87I-PLUS Motherboard
2 x WD Red 2TB NAS Hard Drive (2 x 4TB to be added later)
Seasonic 360W 80PLUS Gold
Crucial Ballistix Sport 8GB Kit (2 x 4GB)
Intel I5-4440 Processor

I am glad to hear you say that RAID is overkill for my use. I plan to have media in two places (local machines and then the NAS) and my important data and some backups will backed up to Crashplan or another similar service that will run on the NAS.

I will do some reading on LVM and take your recommendations into consideration. Thanks again!

---

