---
title: "Windows 8 Hibernation/Ubuntu"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by sideffects on 2013-01-25
I had previously been running Windows 7 and Ubuntu 12.10 along side with no issues. I upgraded to Windows 8 and everything is great! Except for one minor detail. Windows 8, even if you shut down the computer, seems to automatically "hibernate," so no matter what I do, when I boot into Ubuntu, I get the error that I cannot mount sda2 because it is in hibernation. Does anyone know of a fix for this? Thanks in advance!

---

### Post by oldfred on 2013-01-25
Best to create a shared NTFS data partition. So you are not writing into the Windows system partition.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

