---
title: "Ubuntu 8.04 type"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-08-11
I am trying to install ubuntu on my machine that is currently running only windows. I am trying to partition my harddrive so that i will have my Ubuntu space. I have the free space, and i am trying to create something there so that i can make a swap space as well. What is ubuntu? ext3, ext2, fat32, fat16, jfs, linux swap, ntfs, or xfs? Btw i am using qtparted on a knoppix live cd if that matters at all.

---

### Post by halitech on 2008-08-11
I normally use gparted to do my partition work but the knoppix cd should do it as well. Instead of worrying about creating the partitions (normally ext3), why not just leave the space empty and then tell Ubuntu to use that area?

---

### Post by sandysandy on 2008-08-11
here is link for dual booting windows & ubuntu

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

regards

---

### Post by run1206 on 2008-08-11
i have ext3 on my Linux partition for Ubuntu, and am using the NTFS configuration tool to work with my Windows partition while in Linux mode. Leave some room for swap space, i have 600MB for that.

edit: Sandy, i got "bad request" on your link :(

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
found it :D

---

### Post by ranger5664 on 2008-08-11
awesome thanks guys

---

### Post by ranger5664 on 2008-08-11
However one thing... will i be able to dual boot by just telling it to use the free space?

---

### Post by run1206 on 2008-08-11
> **ranger5664 said:**
> However one thing... will i be able to dual boot by just telling it to use the free space?

You can put however much space you want. If you're installing from a LiveCD, there's a step that lets you do that.  I know some users who triple-boot XP,Ubuntu, and Mac all in one HDD :shock:

after installation is complete, you'll see the GRUB bootup screen asking which partition you'd like to run

---

### Post by sandysandy on 2008-08-11
have a look here

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

regards

---

