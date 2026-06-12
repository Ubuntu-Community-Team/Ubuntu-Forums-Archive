---
title: "GNOME rescue&gt;"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by jesuraj2 on 2014-05-31
Hi,

     I'm new for the Ubantu and also for this forum too. 

    I have a HP notebook. I use two OS Win 7 & Debian in that. I   also want to use Ubantu 14.04, so I installed Ubantu in external hard   disk after the installation I removed the external hard disk which I   installed  the Ubantu then I restarted the notebook. It shows "GRUB   rescue> " I cant able to load on  to the Windows. 


   pls help me...   thank you..

---

### Post by Impavidus on 2014-05-31
When you installed Ubuntu on the external disk, the installer installed grub in the internal disk too. This grub points to some data on the external disk, and therefore it doesn't work when the external disk is not attached. The way to solve this is by having Debian in control of grub.

Attach the external disk and boot. A grub menu with Windows, Debian and Ubuntu should appear. Boot Debian and reinstall grub to the internal hard drive.

To make it all clean and tidy, you can arrange that the grub menu from the internal drive doesn't mention Ubuntu (disconnect the external drive before reinstalling grub), so that the Ubuntu option only appears when the the external drive is attached. Ubuntu can remain in control of grub on the external drive, assuming grub has been installed to all drives. Just set boot priority to the external drive, so that you get a menu with Windows, Debian and Ubuntu when the external drive is attached, and one with only Windows and Debian when it's not.

---

