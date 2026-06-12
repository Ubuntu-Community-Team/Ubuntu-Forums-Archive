---
title: "win8"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-10-31
i actually installed win7 after i installed ubuntu. has anyone upgraded win7 to win8 with a double boot. thinking about upgrading to win8 but want to make sure this secure boot thing wont mess up my current ubuntu/win7 dual boot. tks

---

### Post by rburkartjo on 2012-10-31
cause if it is going to mess up my double boot not worth messing with.

---

### Post by oldfred on 2012-10-31
Secure boot is only with new UEFI systems from a new purchased computer. The vendors are required to turn it on. But if you install yourself that is not a requirement.

Is your system UEFI/gpt or BIOS/MBR? It should work either way but you must install the same way as currently configured.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

Boot-Repair fixed BIOS boot Windows 8 & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2056561](http://ubuntuforums.org/showthread.php?t=2056561)

---

### Post by rburkartjo on 2012-10-31
old tks for the info. might wait awhile no hurry

---

