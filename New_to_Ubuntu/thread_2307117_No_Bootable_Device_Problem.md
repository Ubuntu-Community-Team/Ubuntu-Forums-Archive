---
title: "No Bootable Device Problem"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by job2 on 2015-12-22
I installed Ubuntu 14.04.3 from a USB drive. After rebooting, I get the error: "A bootable device has not been detected"
I tried using the Boot-Repair tool, but it still doesn't work. 
Here's the link to the paste [http://paste.ubuntu.com/14135601/](http://paste.ubuntu.com/14135601/)

---

### Post by Bucky Ball on 2015-12-22
Please tell us what device you are using. You have installed Ubuntu but no boot loader. Looks like you are using something with an eMMC card, not a hard drive.

---

### Post by Bucky Ball on 2015-12-22
Welcome. Please tell us what device you are using. You have installed Ubuntu but no boot loader. Looks like you are using something with an eMMC card, not a hard drive. 

If there is a BIOS, is it set to boot from the correct drive?

---

### Post by job2 on 2015-12-22
I am using and Intel Compute Stick.
The BIOS seems to be set to the correct drive.

---

### Post by sandyd on 2015-12-22
What version of the stick are you using, the Windows model that came with Windows, or the Ubuntu model.

If it's the Windows model, you will have to switch the UEFI settings. See [http://liliputing.com/2015/07/install-ubuntu-14-04-lts-on-the-2gb-intel-compute-stick.html](http://liliputing.com/2015/07/install-ubuntu-14-04-lts-on-the-2gb-intel-compute-stick.html) for full instructions.

---

### Post by job2 on 2015-12-22
The Windows version. 
I've set the bios to Ubuntu though.

---

### Post by Bucky Ball on 2015-12-23
Did you have a good read through the link sandyd provided??? That gives full instructions. :)

---

