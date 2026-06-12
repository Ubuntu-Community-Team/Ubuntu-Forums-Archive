---
title: "after installing ubuntu how to create separate partition to utilize free space"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by arai on 2011-11-27
after installing ubuntu linux in full hard disk 80gb is it possible to create a separate partition to utilize the free space ?

i got gparted installed.

the new partition would be used for installing winxp (only for offline uses). I would primarily use ubuntu for all online purposes.

please help me. thankx.

---

### Post by Rex Bouwense on 2011-11-27
Yes.  What do you want to do, install another distro?  Just install it side by side and the installer will do everything for you to include partitioning.  Or, if you just want to create another partition for later use, you can do that with GParted.  Resize what is probably sda1(after backing up your data) and then create another partition with what you took away.

---

### Post by arai on 2011-11-27
[[IMG]http://img820.imageshack.us/img820/9162/screenshotat20111128062.th.png[/IMG]](http://imageshack.us/photo/my-images/820/screenshotat20111128062.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

i have attached a screenshot

---

### Post by ddarsow on 2011-11-27
you can make a separate partition with Gparted to install WinXP on, but if you install WinXP after installing Ubuntu it will change the bootloader and you will not be able to boot into Linux.

While this can be fixed, it might be best (if this is a new fresh install) to simply start over. Install WinXP first and then install Linux. You can choose partition sizes during the Linux install. Much easier for those not compfrtable with the terminal and rebuilding GRUB.

---

### Post by arai on 2011-11-27
> **Rex Bouwense said:**
> Yes.  What do you want to do, install another distro?  Just install it side by side and the installer will do everything for you to include partitioning.  Or, if you just want to create another partition for later use, you can do that with GParted.  Resize what is probably sda1(after backing up your data) and then create another partition with what you took away.

i need to install winxp (for offline uses only).

---

### Post by ddarsow on 2011-11-27
how much ram do you have? Why not just use virtualbox for WinXP? even easier yet!

---

### Post by Rex Bouwense on 2011-11-27
Post #4 is probably your best bet, but in case you do not want to do that here are a couple of sites that might help you.

[https://help.ubuntu.com/10.04/switching/C/dualboot.html](https://help.ubuntu.com/10.04/switching/C/dualboot.html)

[http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html](http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html)

---

### Post by arai on 2011-11-27
> **ddarsow said:**
> how much ram do you have? Why not just use virtualbox for WinXP? even easier yet!

2gb ram i got.

Printer Epson Stylus Tx121 i have . it is a printer scanner copier. it is not printing continuously in ubuntu. also i am unable to scan documents using epson tx121 in ubuntu. thats why i thought of using winxp for printing and other offline purposes.

---

### Post by ddarsow on 2011-11-27
> **arai said:**
> 2gb ram i got.

probably not enough, you would be limited to anout 768MB for virtualbox and both OSes would be quite slow when running virtualbox. It would work, but not be very fast.

---

