---
title: "Ubuntu 16.04 LTS crash and internal error"
date: 2016-12-06
forum: New to Ubuntu
---

### Post by soumyarupchoudhury on 2016-12-06
My ubuntu 16.04 lts crashes saying it experienced an internal error. The error reads as 'gnome software crash, please try restarting your computer'. The error has been occurring for sometime now especially after I did an sudo apt-get upgrade. How do I solve it ?

---

### Post by bcschmerker on 2016-12-06
What kind of hardware your system, and how old?  I've a new CPU slated for the Hot Rod gPG&#8482;, as the Advanced Micro Devices® Athlon 64® X2 5600+ that served me faithfully through three ubuntu® LTS dist-upgrades (from 10.04 to 12.04 to 14.04 to 16.04) finally hurled - bad memory manager.  (I've an Athlon 64® 3500+ as a stand-in until I can acquire an upgrade CPU for the ASUS® CM1630-06, as the Athlon II® X2 220 currently therein has the same clocks as the failed X2 5600+ and should run as lag-free once transferred - Microsoft® Windows® 10 Build 1607 10.0.14393.451 really needs more cores in the form of the Phenom II® X4 840, as two can't hack the additional Processes over 6.1.7601.)  Make note of the pattern of memory errors in MemTest86+ version 5.01, as I see either the main memory or your rig's memory manager as toast.  Too regular addresses and error bits across the memory range would pin it toward the memory manager rather than any one module; addresses limited to a small portion of the range with fairly dissimilar error bits should indicate which bank needs replacement as a function of the address range.

---

### Post by soumyarupchoudhury on 2016-12-07
Well my processor is core i5 4460 on an asus H81m motherboard with 4 x 2 gb ddr3 corsair vengeance. I also have a graphics card of nvidia Gtx 650, and as about the hardware they are fairly new with an age of not more than 7 months other than the graphics card which is near about 3 years.

---

### Post by bcschmerker on 2016-12-07
Any problems reported in Memtest86+?  A CPU as young as an Intel® 4th-Generation Core Processor™ (FCLGA 1150) shouldn't have a memory manager problem shout of serious overheating.  If the RAM proves error-free, GNOME® Software™ may already have an open thread at Bugzilla.GNOME.org; or the problem may be deeper -  I've been tripped up by crashes in high-level apps that were eventually traced to a Kernel bug.

---

