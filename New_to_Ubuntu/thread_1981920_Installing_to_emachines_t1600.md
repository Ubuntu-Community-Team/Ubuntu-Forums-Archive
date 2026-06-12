---
title: "Installing to emachines t1600"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Grant T B on 2012-05-17
I created a bootable USB drive for installing Ubuntu 12.04. One goal I have is to use it to install this OS onto an emachines t1600, about 10 years old. I am aware that it may not meet the minimum requirements, but I don't know its specifications. 

Booting the computer with the USB drive plugged in does not initiate an installation; the USB drive is not recognized. Holding Esc, F2, and F12 has no effect. How can I begin the installation?

---

### Post by Daveth on 2012-05-17
you would need to get into the system BIOS and change the boot order to boot from usb or similar, assuming the BIOS is that sophisticated, which i doubt.
BIOS is typically reached during the start up of the machine where you tap the delete key, then work through the menus with the arrow keys. It will usually show you the options to get into the BIOS at the bottom of the screen.
Not sure the spec will reach the minimum, even if you have done that, unless you have tweaked and re-built it (a vile experience on those machines!).

---

### Post by Grant T B on 2012-05-17
Thanks for the info. I have not altered the hardware. I'll try holding delete to access the BIOS.

---

### Post by Daveth on 2012-05-17
bear in mind there are a number of less demanding linux distros you could run on that machine, both in terms of their install footprint and memory and graphics demands, so if Ubuntu crashes and burns there are still lots of other options out there.

---

### Post by Grant T B on 2012-05-17
Good to know, thanks. I read a little about Xubuntu and it no longer seems much less demanding that Ubuntu. What do you recommend as an OS that is simple to use with less demanding requirements?

---

### Post by Daveth on 2012-05-17
I run peppermint 2 on the 4gb eeepc 701 netbook- the original one that stormed the planet when Asus released it. It uses LXDE as its desktop.
[http://desktoplinuxreviews.com/2011/06/10/peppermint-os-two/](http://desktoplinuxreviews.com/2011/06/10/peppermint-os-two/)

Distros like Puppy are very small and stormingly fast.
Check out
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Grant T B on 2012-05-17
Thanks, I'll look into those. Since you mentioned the eee, let me mention that I am also trying to install 12.04 to an eee 901, as described here:

[http://ubuntuforums.org/showthread.php?t=1970590&page=3](http://ubuntuforums.org/showthread.php?t=1970590&page=3)

Do you think 12.04 is a good solution for the eee 901 (since I've already created the boot disk for 12.04), and if so, do you have any advice on how to overcome the problems I've had with installing it?

---

### Post by black veils on 2012-05-18
> **Grant T B said:**
> What do you recommend as an OS that is simple to use with less demanding requirements?

Lubuntu  **"The objective of the Lubuntu project is to create a variant of [Ubuntu]("http://ubuntu.com") that is lighter, less resource hungry and more energy-efficient by using lightweight applications and [LXDE]("http://lxde.org/"), The Lightweight X11 Desktop Environment, as its default [GUI]("http://en.wikipedia.org/wiki/GUI"). Lubuntu is targeted at 'normal' PC and laptop users running on low-spec hardware"**

official website:
[http://lubuntu.net/](http://lubuntu.net/)

---

