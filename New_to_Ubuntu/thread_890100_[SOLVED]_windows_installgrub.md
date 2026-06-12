---
title: "[SOLVED] windows install/grub???"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-14
i installed windows after installing kubuntu,then ran supergrub to restore the mbr,now all iget is kubuntu no boot screen just starts into kubuntu.
how do i make it so i can boot both,im lost!please help
rick

---

### Post by erickghint on 2008-08-14
This is the best tutorial I've found on the subject. 


[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by bodhi.zazen on 2008-08-14
You need to add windows to /boot/grub/menu.lst

In order to do this you need to know your windows partition and how grub identifies partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Then :

```
sudo gedit /boot/grub/menu.lst
```

Near the bottom, where your Ubuntu "stanzas" are listed, add in one for Windows :

```
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
boot
```

See also : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by rixtr66 on 2008-08-14
thank you!!!!
rick

---

