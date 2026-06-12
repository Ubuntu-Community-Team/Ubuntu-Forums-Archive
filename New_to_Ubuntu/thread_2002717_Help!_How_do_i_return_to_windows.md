---
title: "Help! How do i return to windows?"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by zeke1234 on 2012-06-13
So I recently installed ubuntu about 2 days ago, it was great but now I'm feeling a bit homesick and want to return back to the windows OS. I've been trying really hard but to no success, can someone help?

What I've done: 
- Tried to use the windows 7 cd to reinstall but it was unable "windows was unable to create a required installation folder error code 0x8007007a".

-Tried to use windows system recovery, got no where, in fact I think it didn't do anything cause ubuntu just started itself right after trying that.

-Tried using Boot Repair advanced options>other options but "repair windows boot files was greyed out and unclickable. 

*I'm pretty much an amateur at this so please help.
**If I could return to windows completely that would be great but if not dual boot is just as fine.

---

### Post by fantab on 2012-06-13
You need to tell us more.

How did you install Ubuntu? Are you Dual Booting Windows and Ubuntu? If you explain these things is some detail it will help us to help you.

Also give some details about your computer and its hardware, like Hard Disk.

---

### Post by mastablasta on 2012-06-13
you can return to windows. completely. how did you install Ubuntu? full disk? if so just backup all data and format the disk into NTFS. if you can't do it with windows use ubuntu live disk run gparted and reformat the disk or just delete all partitions.

---

### Post by Mark Phelps on 2012-06-13
Windows 7 does not come on a CD -- it is too large to fit.

If what you have is really a CD, and if your PC came preinstalled with Win7, then most likely, that CD is a Restore CD furnished with your PC.  In that case, when you boot from it, it is going to look for a (possibly hidden) Recovery partition, where it expects to find a compressed Win7 Image file -- and will try to use that file to restore your PC to its original condition.

However ... if you have removed the Recovery partition, then you are out of luck because you then have no image to be used for the restoration.

Also, some restore programs have serious problems if they encounter non-Windows partitions on the drive -- which would be the case when you have both Windows and Ubuntu installed in separate partitions.

In that case, you would have to boot from an Ubuntu LiveCD or LiveUSB, and remove the Ubuntu partitions -- and try the restore again.

---

### Post by YannBuntu on 2012-06-14
Hello

> **zeke1234 said:**
> -Tried using Boot Repair advanced options>other options but "repair windows boot files was greyed out and unclickable.

It will appear if you tick the "Restore MBR" option.

However, don't try it now. You may have some Windows files missing as suggested by Mark, so please run Boot-Repair's "Create BootInfo report" button and indicate us the URL that will appear.

---

