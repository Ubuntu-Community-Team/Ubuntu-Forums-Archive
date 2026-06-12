---
title: "How to install Unbuntu on a 2nd HD &amp; 1st HD is W98"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Banshee42 on 2008-10-25
How to install Unbuntu on a 2nd HD & 1st HD is W98

I tried to create a UBUNTU USB and the PC didn't boot

What is the easiest way to get it done?

---

### Post by bumanie on 2008-10-25
Follow [this guide]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm"). Although it is for xp/ubuntu, it should work the same for win'98 and ubuntu.

---

### Post by Banshee42 on 2008-10-25
W98 isn't recognizing the 2nd HD and I don't want to keep W98 or the 1st HD.  I also have another PC with XP on it.  BUT My big problem is I can't get UBUNTU installed on the 2nd HD. I am hoping to do this and then just put the 2nd HD in the w98 PC as a replacement HD for the W98 primary HD.

What is the best & easiest way for me to do this?

---

### Post by w4ett on 2008-10-25
If you are confident that you can change hardware components....try this method:

1.  Remove the IDE cable from the original Win98 drive
2.  Place the jumper on the second drive to set as the "Primary" drive
3.  Connect the second drive to the IDE and power connectors.
4.  Boot your computer with the Live CD and install Ubuntu.
5.  When complete, Power down the Computer...Replace the IDE cable on the   Original Win 98 drive.
6.  Set the jumper on the Ubuntu drive to "Slave"

Doing this will keep both OS installations COMPLETELY separate...to choose OS on boot, use the boot toggle options to select the device you want to boot from.  On some older machines this can be an easier method than installing grub on your existing primary HDD.

Good Luck

---

