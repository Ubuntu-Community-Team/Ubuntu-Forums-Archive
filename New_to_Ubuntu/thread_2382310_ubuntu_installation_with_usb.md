---
title: "ubuntu installation with usb"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by raytime on 2018-01-11
I install ubuntu with usb. When I take out the usb, the system is freeze.

I cannot turn off the compuer and open anything. I must plug in the usb in order to tuen on ubuntu.

Why does it happen? I do not want to plug in the usb whenever I use ubuntu?

---

### Post by Autodave on 2018-01-11
Is Ubuntu the only operating system on the computer?

---

### Post by raytime on 2018-01-11
yes. I re-download the ubuntu. when I plug in the usb it goes to black screen asking to try ubuntu or install ubuntu.

I still need to plug in usb whenever I need to turn on ubuntu successfully?

---

### Post by yancek on 2018-01-11
Is your system UEFI or the older MBR?
If you remove the usb, do you change the boot order in the BIOS to boot from the internal hard drive on which you installed Ubuntu?

---

### Post by raytime on 2018-01-11
--deleted--

---

### Post by raytime on 2018-01-11
It is UEFI. After I remove the usb, I just no nothing. The ubuntu get freeze. I want to use ubuntu without using usb every time?

---

### Post by yancek on 2018-01-11
> when I plug in the usb it goes to black screen asking to try ubuntu or install ubuntu.

That means you are still booting the usb you used to install.  You need to change the boot priority in the BIOS to set you hard drive first.  If that doesn't help, you will need to provide more information by booting the Ubuntu usb and going online to the site below and downloading and running boot repair.  Select the 2nd option to use the ppa as explained on the site.  When you do that, make sure you select the option to Create BootInfo Summary and do not try to make any changes but post the link you are given here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

