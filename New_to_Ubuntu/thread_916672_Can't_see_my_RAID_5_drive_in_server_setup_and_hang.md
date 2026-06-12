---
title: "Can't see my RAID 5 drive in server setup and hanging at 33%"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by WolfieZero on 2008-09-11
I'm doing a first time install on a system and I'm quiet new to RAID.

The server has 4x500GB drives that I've setup in the Intel Bios to be one RAID 5 drive. When I go to partition the drive in the Ubuntu Server set up, it can only see the 4 drives as SCSI (is that right? I'm not at the machine as we speak) but no RAID.

To add another issue, when I first tried to partition it, it hung at 33% and through the various types of set up (going to turn off RAID altogether to make them the default IDE) it starts and hangs at 33% no matter how I partition the drives.

Thanks for any help that any contributes!

---

### Post by srt4play on 2008-09-11
> **WolfieZero said:**
> (going to turn off RAID altogether to make them the default IDE)

Have you done this and does it still hang?  

If you are trying to use RAID features of your motherboard (and not a dedicated RAID controller card), you may be better off using Ubuntu's built-in software RAID.

---

### Post by WolfieZero on 2008-09-12
Set the SATA to use the IDE type (default) and it still hangs at 33%; it oddly starts at 33%.

Not sure how to set up the RAID 5 through the partition option on install TBH. I set all the drives to be RAID, then create the MD (?) but the guided seems to have issues with it.

---

