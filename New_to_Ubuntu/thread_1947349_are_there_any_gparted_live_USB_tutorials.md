---
title: "are there any gparted live USB tutorials?"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by chestycuogth on 2012-03-26
hello everyone,
i recently installed ubuntu as a second OS alongside windows vista, however i only gave about 5GB of space to the ubuntu partition.
i am running so low on space that i dont even have room to complete all the necessary updates.
 i looked into how i can resize the partitions and the only way i found was using GParted (if you know any other methods it would be greatly appreciated if you could enlighten me)
i would like to use gparted on a USB but i have no idea how - i dont know which download link i need, how to install it onto the USB and what to do with it then.

if you know of any easy to follow tutorials, or if you could tell me what exactly to do then i would be grateful.
thank you.

i know there are similair threads to this but i would like to know exactly how to use gparted on a USB

EDIT - SOLUTION: nobody ever mentions this but if you used WUBI in windows to install ubuntu then you shouldn't resize the 'normal' way.
instead use this tutorial: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by wildmanne39 on 2012-03-26
Hi, here is one.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

Also need to clarify did you install a true dual boot or using wubi inside windows?
thanks

---

### Post by oldfred on 2012-03-26
You may not have room to download the gparted ISO, but gparted is on the Ubuntu liveCD.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

But with Vista or 7 you should use the Windows tools to shrink the Widnows partition and reboot Windows a couple of times so it can run chkdsk or other fixes on the resize. If you have to use gparted to resize Windows NTFS partitions, only do that and reboot. But you may have to run Windows repairs, so have a Windows repairCD handy.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by chestycuogth on 2012-03-27
> Also need to clarify did you install a true dual boot or using wubi inside windows?
thanks

i used wubi.
that reminder has helped me get things moving.
i will let you know if i succeed and provide instructions for other people like me.

---

### Post by oldfred on 2012-03-27
Ignore all the info on gparted, that is only for partition installs not wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by chestycuogth on 2012-03-30
thanks for the help.
i got it all sorted now.
:)

---

### Post by wildmanne39 on 2012-03-30
Hi, good to know would you please use thread tools at the top of the page to mark the thread solved and post how you solved it for the benefit of the community.
Thanks

---

