---
title: "USB's mounting as read only.  Unable to change to read write"
date: 2016-06-26
forum: New to Ubuntu
---

### Post by 1squigles1 on 2016-06-26
Hi,
I am running Ubuntu 14.04 LTS.  I mainly use the system to download files that I then transfer by USB to a Windows 10 system.
Somehow most of my USBs have become locked as "read only" on both systems.
I think the problem is originating in Ubuntu.
I have tried following many other threads on similar problems but find I am getting lost with the language/instructions/understanding.
Could anyone help please?

---

### Post by sudodus on 2016-06-26
Welcome to the Ubuntu Forums :-)

1. If the partition table or file system of a USB pendrive is damaged, it can be repaired. If this is the case, you should be able to repair it with ***mkusb***, and its wipe menu.

2. If some memory cells are damaged (or worn out), they can be replaced by built-in software in the USB pendrive. But this works only to a certain limit, and after that there are problems. When pendrives behave like you explain, they might be ***'gridlocked'***, and cannot be restored (by methods available to regular users (you and me)). The next step is often that the pendrive is completely dead.

See the following links for more details,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")
[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

