---
title: "Why are some text characters missing after boot?"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by numeric2 on 2015-06-12
Hi,

When I boot to Ubuntu 14.04.2 LTE 64 bit some text characters are missing in the icon description. As an example, the icon for desk top may have show "De k op" rather than "Desktop". This is true for almost all icons. The missing characters seem to re-appear if I mouse over the text area. I solve the problem by re-booting with "Additional options?" (forget actual terminology) and selecting "Restore boot?" (again forget actual terminology).  A normal grub boot will not eliminate the problem. I am using a Sandisk USB 3 Extreme 64 GB flash drive. The entire OS for Linux is mounted on this USB 3 flash drive. No SATA drive is used for Linux.

Computer: Dell laptop Insprion 13 7000 series.
Memory: 7.7 GiB
Processor: Intel® Core™ i7-5500U CPU @ 2.40GHz × 4
Graphics: Intel® HD Graphics 5500 (Broadwell GT2) 
OS type: 64-bit
Disk: 53.2 GB (Sandisk USB 3 Extreme 64 GB flash drive)

Suggestions welcome,
Thank you.

---

### Post by chopra on 2015-06-12
That's very odd.  Your disk size seems awfully small.  Did you check to make sure enough space is alloted for Ubuntu?  Also, maybe try booting from the external drive you installed it from, and see if the problem remains. If it doesn't, and you've recently installed it, re-installing might be worth a try.

---

### Post by numeric2 on 2015-06-12
Hi chopra,
Thank you for your suggestion. The total space used, so far, is 16.6 GB out of a total of 52.7 GB. Only about 1/3 of the total space used. This should be more than enough drive space left. I also have the same problem with a Sandisk Ultra 64 GB USB 3 drive. The extreme version is faster than the ultra version. It seems though, the problem is not USB 3 related. The problem seems to be caused by a "normal" boot sequence. Even then, some times it works with no problems, other times the missing character problem surfaces. It works 100% when boot using alternative options and selecting the second item down (boot refresh?). Too bad there is no easy way to copy the boot screen.    

> **chopra said:**
> That's very odd.  Your disk size seems awfully small.  Did you check to make sure enough space is alloted for Ubuntu? 

---

### Post by monkeybrain20122 on 2015-06-13
I don't think that has anything to do with space, probably a glitch in the graphic system or session is somehow corrupted. I have the same issue sometimes on my Dell machine (intel ironlake mobile) It happens occasionally (rarely) and rebooting usually fixes it.

---

