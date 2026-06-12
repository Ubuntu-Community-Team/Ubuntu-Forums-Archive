---
title: "Hibernate not working in windows 8 after Ubuntu install"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by kevpple on 2013-02-23
I have recently installed Ubuntu 12.10 on my UEFI computer with OEM windows 8 preinstalled however windows will no longer resume from hibernate after it hibernates and i boot again it will just reboot as if it wasnt hibernated also if I hibernate then boot Ubuntu it will show my windows drive as hibernated and wont allow me to mount it

---

### Post by oldfred on 2013-02-23
If you are hibernated an attempt something from Ubuntu it may damage the hibernated system. Linux did not used to prevent you from mounting and users posted that files disappeared or they could not boot Windows.

Hibernation has to have everything as it was when it hibernated. Generally best to not use hibernation when dual booting. 

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by kevpple on 2013-02-23
OK i guess i will have to use sleep instead of hibernate in windows thanks

---

