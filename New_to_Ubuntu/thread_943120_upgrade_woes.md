---
title: "upgrade woes"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by hfnd on 2008-10-09
upgraded to "8.04" now we don't have permission for our ntfs drive and it doesn't auto mount

---

### Post by adam_kimber on 2008-10-10
Hmmm. Have you tried going to "Computer" and double clicking on the drive of size that matches your NTFS partition? If there is any problems a box should popup with them. Otherwise it should mount automagically. 

If this does not work, try installing ntfs-3g from synaptic as that is the driver for reading NTFS partitions. Should already be there.... But you never know. 

If this does not work we can look at some other config options that might be putting a spanner in the works. :D

---

### Post by bumanie on 2008-10-10
8.04 installs ntfs-3g by default. You can however install ntfs configuration tool > sudo apt-get install ntfs-config Then go to Applications --> System Tools --> Ntfs configuration tool. Fill out the box that appears and then your ntfs drive should auto mount and will be added to /etc/fstab with read/write permissions.

---

### Post by PierreDeKat on 2008-10-10
I'm guessing your old /etc/fstab file is to blame: that you or whoever previously edited fstab to automount your NTFS partition, and now Ubuntu's confused about the automount. I know that I've run into that problem a time or two.

[HOW TO Automount NTFS in Hardy]("http://ubuntuforums.org/showthread.php?t=802699")

[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

But basically you need to re-edit fstab to reflect your current setup.

---

### Post by hfnd on 2008-10-10
Thanks to all who replied, I think I have found the problem. Apparently flomertens and sitesweetsite doesn't work with Hardy. Does anyone have any suggetions.

---

