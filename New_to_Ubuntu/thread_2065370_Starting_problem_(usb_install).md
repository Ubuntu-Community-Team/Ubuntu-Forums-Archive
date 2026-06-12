---
title: "Starting problem (usb install)"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by roster on 2012-10-01
I just installed Ubuntu from a USB and erased all de Hard disk, i cant run de OS with out de USB, i use dell inspiron1464.
PS the monitor is broken so i use an LG monitor in sustitution it works well

---

### Post by AndyOpie150 on 2012-10-01
Are you using a standard .iso or a live .iso (It looks as if you have the live .iso).
What utility did you use to format, and configure the USB drive, and install Ubuntu onto the USB drive?

---

### Post by Bashing-om on 2012-10-01
roster; Hi ! Welcome to the forum.

Seems to me that grub (grand unified bootloader) has been installed on your usb device.

To boot ubuntu on your hard drive alone, grub must be installed onto the hard drive.
Not knowing your configuration, I can not advise further at this time.

This link will be point you in the right direction:
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

The emphasis is using a cd, but the information will still apply to usb ..additional links for further info is also in this link.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by roster on 2012-10-01
I used "Pen drive linux usb installer"

---

### Post by Bashing-om on 2012-10-01
The situation remains the same, to get grub installed onto your booting hard drive.
Grub can be installed from either the live environment or from the installed system.
Follow the documentation or refer to the additional links to do so. 

In the event you still have difficulties, we will tell you the terminal commands to give the required info to have you install grub properly.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by westie457 on 2012-10-01
Using a Live Desktop (Try Mode) and a working internet connection go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and use option 2.

If this does not work post the link to the bootinfo so we can have a better look at what has gone wrong.

---

