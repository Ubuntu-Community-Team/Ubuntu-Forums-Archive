---
title: "Portable Linux for external HDD?"
date: 2007-12-11
forum: Other OS Talk
---

### Post by Afkpuz on 2007-12-11
Hi, I was curious if it would be possible to install any distro of linux on an external and move it from computer to computer.  Ideally, I would like to move between two computers with the same external and be able to boot from each with that external.  Is this possible?  How would I go about doing this?  The computers are for public use and it would be amazing if I could plug in my external, boot up linux, then unplug and the computer would be back to normal.  Also, I can't really install anything on the public computers.  It has to be all on the external.  Any ideas?

---

### Post by tgalati4 on 2007-12-11
Simply take a Live CD with you and a 1-2 GB thumb drive.

Boot off of the Live CD and save any important work to your thumb drive.

You can do a similar thing with a USB drive, But you might need to make a USB-boot floppy.  This allows you to boot off the floppy (if allowed, then find the external drive on the USB chain and boot off of that.).

There are lots of options, but a Live CD is more discrete.  Just be sure to pick a theme that looks like Windows so you don't look too subversive.

---

### Post by smartboyathome on 2007-12-11
I have an external hard drive, and while I haven't tried it on any other computers (yet), I have ubuntu working fine off of it.

---

### Post by Afkpuz on 2007-12-12
I'm just concerned about the boot loader.  I've heard of problems arising from the bootloader when ubuntu was installed on an external.  Or is there a dynamic bootloader that can adapt to different partitions on different computers?

---

### Post by pelle.k on 2007-12-13
> **Afkpuz said:**
> I'm just concerned about the boot loader.  I've heard of problems arising from the bootloader when ubuntu was installed on an external.  Or is there a dynamic bootloader that can adapt to different partitions on different computers?

The thing is, with the traditional /dev/sdX (/dev/hdX) nodes, partitions and drives tend to move around quite a bit on different setups, but with persistent drive naming, like the one ubuntu nowadays does with drives in fstab, and to some extent in grub, this is quite easy to do.
A partition can be mounted by device node (/dev/sdX), UUID (/dev/disk/by-uuid/ID) or LABEL (/dev/disk/by-label/LABEL) so that should take care of fstab, and if you check you menu.lst (grub) it looks something like this;
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
#root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=66aab274-bc46-4ca3-92e0-87d250923a94 resume=/dev/sda12 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
Just comment out the root entry like i did, and that will be passed with the kernel entry, but with an UUID.
And, just for the sake of it, i just tried to start gdm without an xorg.conf and that went OK.

Oh, and i also installed ubuntu to my external usb drive, and it works great if you ask me. Just be careful when it wants to install grub, so that it doesn't install it to the internal HD (you want a separate grub on that drive), but to the external one.
The alternate install disk will ask you this before it installs the MBR.
To be on the safe side, just unplug the internal drive while installing to the USB disk.

---

