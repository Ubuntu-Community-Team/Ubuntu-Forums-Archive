---
title: "Installing over different Distro?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Desert Sailor on 2008-11-17
Greetings, Total Linux Noob here, I feel so lost.  I am very glad to be free from the clutches of the evil Redmond Empire, but will have lots of questions as we go along.  

First question...  I am going to replace an XandRos install with Ubuntu.  Will the Ubuntu install replace the old files, or should I fdisk the partition before I install.  Also will the Lilo be replaced by Ubuntu, I am dual booting with a Win-2000 install, and don't particuarly want the XANDROS lilo message at boot up.  

Thanks....  :)

---

### Post by LowSky on 2008-11-17
Ubuntu can handle a reformat, and LILO will be replaced with GRUB which will allow dual booting

---

### Post by sirjoebob on 2008-11-17
Just go throught the Ubuntu installer and select to format the Xandros partition and mount as "/" you can do this through the installer which is ncie and graphical. That should be all you need to do as Ubuntu will replace LiLo with GRUB. 

Freedom is great. I gave up Windoez and have not looked back!

---

### Post by mikewhatever on 2008-11-17
If you install Ubuntu on an existing partition, all data on that partition will be lost because it gets formatted in the process. The installer will not replace the old files, it will format the partition and install Ubuntu. Backup all personal data before you start.

By default, Ubuntu uses GRUB boot loader. Whatever boot loader you have will be replaced with GRUB, which should also detect other OSs installed.

You'd also need to manually point the installer to the correct partition, so make sure which one that is.

---

