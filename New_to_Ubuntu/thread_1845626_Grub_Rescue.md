---
title: "Grub Rescue"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Hendodude on 2011-09-17
I have a Gateway LT31 netbook.  It has a Ubuntu 11.04 60 gb partition and a 130 gb Windows Vista Partitition.

Two problems

A.  Suddenly when booting, I get
error: no such partition
grub rescue>

I have tried to boot off the recovery DVD/CD but Gateway did not give you a way to get to a command prompt to run FIXMBR.  There is just 3 options, 1) Recover Windows, 2) Restore Disk (which just does the Windows Partition, it doesn't fix the boot partition) 3) Exit.

How can I fix Grub or simply remove Grub and start the Computer without Ubuntu?


B.  When in Ubuntu 11.04, the screen is all messed up.  Cursor is a big box.  Screen flashes and sections disappear.  You can barely get out of Ubuntu as the screen graphics are so bad you can't really see what you are doing.  

Any suggestions on this?

Thank you.
:confused:

---

### Post by Blasphemist on 2011-09-17
> **Hendodude said:**
> I have a Gateway LT31 netbook.  It has a Ubuntu 11.04 60 gb partition and a 130 gb Windows Vista Partitition.

Two problems

A.  Suddenly when booting, I get
error: no such partition
grub rescue>

I have tried to boot off the recovery DVD/CD but Gateway did not give you a way to get to a command prompt to run FIXMBR.  There is just 3 options, 1) Recover Windows, 2) Restore Disk (which just does the Windows Partition, it doesn't fix the boot partition) 3) Exit.

How can I fix Grub or simply remove Grub and start the Computer without Ubuntu?


B.  When in Ubuntu 11.04, the screen is all messed up.  Cursor is a big box.  Screen flashes and sections disappear.  You can barely get out of Ubuntu as the screen graphics are so bad you can't really see what you are doing.  

Any suggestions on this?

Thank you.
:confused:
Welcome to the forums! From what you describe I'm going to assume that you are on another computer now right? The first thing is to do the grub troubleshooting. Here is the link you need for that. [https://help.ubuntu.com/community/Grub2#GRUB_2_Troubleshooting_Preparation](https://help.ubuntu.com/community/Grub2#GRUB_2_Troubleshooting_Preparation)

This should get you booted into ubuntu. Then I'd install boot-repair if the grub2 troubleshooting doesn't help you know what to do. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-repair gives you an option to create a boot-info summary if you'd like to use that to give us information for helping. It will put the summary up and you just need to give us the url.

---

