---
title: "My external hard drive is read-only"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Tutoka on 2011-11-04
My Toshiba external hard drive works fine in Windows but not in Ubuntu. In Ubuntu it's read-only. Is there any universal, smooth. compact or coherent tool which would help me and others with this sort of problem? 

I do not want to format the device or move the files in it all around. The file format is NTFS, the properties of the filesystem are not able to accept a change towards the "write" capacity, the restart with the hdd hooked up to computer did not work neither...
Thanks.

---

### Post by lolpenguin on 2011-11-04
In file manager, enter the device, right-click on empty space and select properties. In the permissions tab, if the owner is root or another account you cannot modify the contents. There is a workaround and a permanent solution.
Workaround:
Every time you wish to access the folder, hit [alt]+[f2] then enter "gksu nautilus" (without quotation marks), enter your password then browse to the drive. You will be able to modify its contents.
Solution:
Hit [alt]+[f2], enter "gksu nautilus" (without quotation marks), enter your password then browse to the drive, right-click on empty space, select properties from the menu. On the permissions tab, change entry for file access and folder under "Others" access to "create and delete files" and "read and write" respectively. You will be able to modify the contents normally.
Hope it helps!

---

### Post by ajgreeny on 2011-11-04
Make sure you have ntfs-3g installed in your system and also that you do not have ntfs-utils installed as well;  that can cause problems in 11.10 which were not seen in previous versions of Ubuntu.

With the disk attached and mounted please run the command ```
mount
``` and report back here the output.  Also have a read through [http://ubuntuforums.org/showthread.php?t=1874174](http://ubuntuforums.org/showthread.php?t=1874174) which seems very similar to your situation.

---

### Post by Tutoka on 2011-11-04
Problem solved.

The problem was solved by **installation of ntfs-3g**. The terminal and the command "mount" did not have to be used at all. 

Thanks you, guys!

---

