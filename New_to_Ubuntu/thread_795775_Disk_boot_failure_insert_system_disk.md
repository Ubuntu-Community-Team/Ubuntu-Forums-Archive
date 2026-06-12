---
title: "Disk boot failure insert system disk"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by 4ph3x7w1n on 2008-05-15
I succesfully loaded the Live cd...Ubuntu fully installed and asked me to remove the CD and Restart, i did just that and as my computer restarted instead of loading ubuntu w/o the disk it says 
DISK BOOT FAILURE INSERT SYSTEM DISK
i have read that it could be my bios is out of date, but i dont no how to update my bios...
any solutions?

---

### Post by logos34 on 2008-05-15
did you try setting the hard disk first in the Bios device boot order?  Even though there's no media present in the cdrom it may be refusing to skip to the next drive.

Or maybe you moved the hard disk and forgot to set the jumper correctly?

After that try reinstalling grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Patb on 2008-05-15
4ph3x7w1n, two possible reasons.

1.  You set the bios to boot from the CD but have not enabled it to boot from the hard drive.  Solution: reset the bios.  Example: first boot device CD, second floppy (if you have one), third hard drive.  

2.  Your grub is defective.  Did you install grub to the MBR?  You might have to reinstall.  Before that though, try booting from the live CD and reinstalling grub by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If that fails, post your specs.  

Cheers, Pat.

PS:  Sorry, Logos posted while I was composing a reply.  But you can see great minds think alike (Logos more aptly, actually:)).

---

