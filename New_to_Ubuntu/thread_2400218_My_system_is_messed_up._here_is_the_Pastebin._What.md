---
title: "My system is messed up. here is the Pastebin. What can I do to clean this?"
date: 2018-09-03
forum: New to Ubuntu
---

### Post by treetop1212 on 2018-09-03
I have several installations side by side. I just want the latest version. I got a note that my boot files are too far apart from the disk. Not sure what that means.  Can someone guide me as to how to clean this up?  Randomly the computer starts spinning too and the computer freezes for a time.

Thanks

Michael

[http://paste.ubuntu.com/p/ZQGkVRWjWv/](http://paste.ubuntu.com/p/ZQGkVRWjWv/)

---

### Post by wildmanne39 on 2018-09-03
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by TheFu on 2018-09-04
Is there a reason you don't wipe it all and start using virtual machines?  

Multi-boot is an ugly solution, IMHO, especially if Windows is involved.  It is also really, really, inconvenient.

---

### Post by oldfred on 2018-09-04
If the error is from Boot-Repair and boot files far from start of disk, that is mostly obsolete.

That was valid for older BIOS/MBR configurations using IDE to mount drives. All newer drives are now mounted with AHCI and I have yet to see issue with any newer system. Issue was somewhat common with USB drives also, not sure if still valid or not for USB as most are not large enough anyway. But more users are using full drives as a USB drive and not seen any lately with that issue.

---

### Post by Impavidus on 2018-09-05
I understand the system currently works, but there are several OSs you don't need and you want to recover some disk space.

You have two hard drives, using MBR partitioning. The first has Windows, two Zorin 11 (a derivative of Ubuntu) installs, Ubuntu 16.04 and Ubuntu 17.10. Ubuntu 16.04 is in control of the boot loader. On the second drive you have Ubuntu 18.04 in an LVM partition, which is in control of the boot loader on that drive. You must be using bios/legacy booting and you can't change that easily.

So what do you want? If you want just Windows and Ubuntu 18.04, the cleanest solution is to have Windows and a shared data partition on one drive, with the Windows boot loader, and Ubuntu 18.04 on the other hard drive, with the Linux boot loader, so you can boot using either hard drive in case the other drive fails.

---

