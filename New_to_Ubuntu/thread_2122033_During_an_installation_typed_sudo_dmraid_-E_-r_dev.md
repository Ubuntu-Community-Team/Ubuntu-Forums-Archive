---
title: "During an installation typed sudo dmraid -E -r /dev/sda, now windows 8 cannot start"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Zestorer on 2013-03-03
During my installation of ubuntu from a usb drive it couldn't detect my  hard drive. I researched and learned that it I deleted my raid(or  whatever sudo dmraid -E -r /dev/sda does) then ubuntu would detect the  hard drive. It worked! However, when I try to start windows 8 I get a  message at startup saying that one of my drives (raid0) is disabled and  then windows 8 crashes. Windows 8 tried to fix the problem but it  couldn't. Is there anything I can do to fix this?

---

### Post by Zestorer on 2013-03-03
During my installation of ubuntu from a usb drive it couldn't detect my   hard drive. I researched and learned that it I deleted my raid(or   whatever sudo dmraid -E -r /dev/sda does) then ubuntu would detect the   hard drive. It worked! However, when I try to start windows 8 I get a   message at startup saying that one of my drives (raid0) is disabled and   then windows 8 crashes. Windows 8 tried to fix the problem but it   couldn't. Is there anything I can do to fix this?

---

### Post by oldfred on 2013-03-04
Someone posted this on reinabling. Did you turn off the auto hibernating and fast boot in Windows and UEFI?

 Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by ronparent on 2013-03-04
The way a raid0 works is by having a raid bios on the MB use two disks as one by writing alternate sectors on each of the drive. This speeds up data reads and writes but distributed data between the drives such that the integrity of that setup has to be maintained or the data is essentially lost. When you break the raid0 and write to one disk only you overwrite one continuous sector of one disk so that the original data written to the disk under raid0, let alone the partition tables are no longer intact. After breaking the raid and installing Ubuntu to one drive I doubt the original raid set is recoverable!

Your best options probably are:
1) To keep the drives separate as a non-raid and completely re-install Win8 and Ubuntu side by side.
2) Reformat the drives and initiate the raid bios (thus restoring  the raid0 metadata). And then completely reinstalling both OS on the raid.

I doubt that any data recovery is at all promising since we don't know which has been overwritten and is recoverable at all. If you had data in a separate partition from windows it might be recoverable if valuable enough for expending great effort (maybe sector by sector recovery fro sound raid0 sectors). Unfortunately raid systems are very dangerous to any one who doesn't fully understand how they work and how they can be used - I speak with firsthand experience of my own disasters. Good luck to you.

---

### Post by oldfred on 2013-03-04
Please do not create duplicate threads. We need to know what others have already replied to not duplicate effort. 
We all are volunteers.

---

