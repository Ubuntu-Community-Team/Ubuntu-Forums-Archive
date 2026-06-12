---
title: "Windows flash boot"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by diesel909 on 2011-11-13
I have a Lenovo IBM ThinkPad Z61t that I just installed ubuntu on but i cant boot ubuntu unless the disk is in while it boots. How do I add ubuntu to the boot screen?

---

### Post by BillyBoa on 2011-11-13
If you cannot see the Grub screen 

[IMG]http://ubuntuforums.org/picture.php?albumid=2448&pictureid=8291[/IMG]

you failed during the installation.
I'm sorry but you have to redo it.

---

### Post by Mark Phelps on 2011-11-13
HOW did you install Ubuntu? Was it from the CD while Windows was running (using Wubi)? Or, did you shrink the Windows partition yourself and install Ubuntu to its own partitions?

When in Ubuntu, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one). That will list out the partitions on your drive so we can see if you have any Linux filesystems.

---

