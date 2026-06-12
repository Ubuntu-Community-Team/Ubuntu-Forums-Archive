---
title: "Updating BIOS allows USB boot?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by FireFreek on 2008-09-18
I've got a Dell Optiplex GX1, with 128MB RAM, and a Pentium III 450 MHz processor. I recently installed Damn Small Linux on it using a burnt CD to see if it would work and to put back some usability into it(It's been in my closet for a while now). Being the gaming/computer geek that I am(more of a console man myself), I wanted to mess around with it, see what it can do. So now I want to install some other distributions, but I don't want to burn that many CDs. So now an idea came in my head and I ask the following question: 

Would updating the BIOS allow me to boot using a USB Flash Drive?

Also, what distributions of Linux would you all recommend?

---

### Post by issih on 2008-09-18
Dunno, some pc's need a bios update some are just too old to have that feature, either way your only hope is to search the dell website for the latest bios for your model and see if the release notes mention usb boot.

Given the age of your machine, I do doubt it I'm afraid..

You could of course use a rewritable cd or a dvd if you are distro hopping at the moment.

Hope that helps

---

### Post by oilchangeguy on 2008-09-18
> **FireFreek said:**
> I've got a Dell Optiplex GX1, with 128MB RAM, and a Pentium III 450 MHz processor. I recently installed Damn Small Linux on it using a burnt CD to see if it would work and to put back some usability into it(It's been in my closet for a while now). Being the gaming/computer geek that I am(more of a console man myself), I wanted to mess around with it, see what it can do. So now I want to install some other distributions, but I don't want to burn that many CDs. So now an idea came in my head and I ask the following question: 

Would updating the BIOS allow me to boot using a USB Flash Drive?

Also, what distributions of Linux would you all recommend?

not sure what you're wanting to do with this computer. it won't be much with damn small linux that's for sure. if it were mine, i'd just do a fresh install of whatever it was born with, if you still have the cd. or upgrade the ram, and at least get it to where it can run xubuntu.

---

### Post by jemate18 on 2008-09-18
> **FireFreek said:**
> I've got a Dell Optiplex GX1, with 128MB RAM, and a Pentium III 450 MHz processor. I recently installed Damn Small Linux on it using a burnt CD to see if it would work and to put back some usability into it(It's been in my closet for a while now). Being the gaming/computer geek that I am(more of a console man myself), I wanted to mess around with it, see what it can do. So now I want to install some other distributions, but I don't want to burn that many CDs. So now an idea came in my head and I ask the following question: 

Would updating the BIOS allow me to boot using a USB Flash Drive?

Also, what distributions of Linux would you all recommend?

it depends upon the BIOS you are updating. You must first check the documentation before doing so, because you might end up screwing things...

---

### Post by FireFreek on 2008-09-18
Updated the BIOS to the latest one. Nothing for USB boot, unfortunately :( . At least it's updated.

---

### Post by gregphil on 2008-09-19
If you already have GRUB install on your boot disk, you can install to a USB drive in anyway.  If your BIOS can't "boot from" the USB disk you can just copy the kernel and initrd images to the bootable disk and then in the GRUB menu.lst file specify the locations of the images and specify the USB disk as the /boot disk.  I have done this successfully.

The BIOS start the bootstrap process, they transfer control the MBR of the first disk (where the first part of the GRUB bootloader code is).  The bootloader in the MBR invokes the BIOS Int13 function to load some more code ( initrd and kernel ) from the disk into ram and then jump into it to execute.  The bootloader configuration file (menu.lst) tells the running kernel in RAM where to find all the rest of the install (say on the USB disk for example).

This works fine and does not require the BIOS to support USB booting.

So for the new distribution installs just do the "live CD" boot and select "install".  Choose the USB disk as the destination.  Just before you click the final "ok to install"  use the "advanced" button (on the lower right) to set the location to install GRUB to.  If you leave the location set to the boot disk, it will over write the MBR and, on the next boot, it won't be able to read the bootup code images from the USB disk (because no BIOS support).  So I simply selected the USB disk as the target for the 2nd GRUB install (even though I won't be booting from it.)  Once the 2nd install is complete, boot into the first install, mount the USB disk and go get a copy of the /media/disk/boot/grub/menu.lst file section that would invoke the 2nd install.  Copy that section into your GRUB menu.lst install on the 1st disk.
Copy the USB disk kernel image and initrd image to the first disks /boot directory.  Finally edit the menu.lst on the fisrt disk to point at the images you just copied over.  Reboot, select the distribution you want, and press enter.

It sounds much more complex then it really is.

---

