---
title: "Putting computer back to single boot windows"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by Geezer60 on 2012-04-11
I've got a 2nd computer I'm making my dedicated Ubuntu box via a KVM switch.  My current computer is dual boot Win XP and Ubuntu 10.4.  How do I put it back to all windows without losing all the windows data on it?

---

### Post by Elfy on 2012-04-11
Use the XP disc to rewrite it's bootloader before you do anything. 

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

Boot with the Ubuntu livecd - start gparted and remove the linux partitions.

Backup things you don't want to lose - I doubt if you'll have problems, but if you do and don't have backups ...

---

