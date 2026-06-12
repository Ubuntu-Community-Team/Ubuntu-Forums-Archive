---
title: "Installation with &quot;Try (hd0,0): EXT2&quot; file system error upon reboot"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by mooseengr on 2016-09-22
I am trying to install Ubuntu 14.04 on a Toshiba 2.0TB portable harddrive I own using my girlfriend's HP Pavilion dm4. Every time I reboot to try and complete the install, I get a blinking cursor with just the message:


Try (hd0,0) EXT2:_


With the underscore marking the blinking cursor.


Attempt 1: left ~1TB partition with the NTFS file system that had my Windows data on it. Created a ~500GB partition with EXT4 file system, 10GB SWAP, installed. Reboot, error message.


Attempt 2: Went nuclear. Wiped the drive. Deleted all partitions. Reformatted a 500GB partition at the start of the drive to mount /, formatted 10GB for SWAP. Installed. Rebooted. Error message.


Did some digging. Used the best Google Fu I have (no better than an acolyte, really).


Attempt 3: Re-wiped the drive. Deleted partitions. Created partitions in the following size and order:


    20 GB to mount /


    10 GB for SWAP


    500 GB for /home


Installed. Reboot. Error message. That same message every single time. I don't know what I'm doing wrong, or where to look to find guidance on how to even learn what I'm doing wrong so I can START trying to find a solution.

Edit: I guess maybe if I ask a question somebody will answer.. what is causing this error, and what do I need to know to try and troubleshoot this problem?

---

