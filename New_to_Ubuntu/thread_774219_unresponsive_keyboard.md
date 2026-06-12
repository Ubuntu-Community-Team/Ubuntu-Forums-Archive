---
title: "unresponsive keyboard"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by eryngium on 2008-04-29
I upgraded directly to hardy from a clean install of gutsy. On rebooting the keyboard is dead. Have checked the settings under System> Preferences> Keyboard and tried different keyboards to no avail.

currently using a gutsy liveCD which seems fine

Any suggestions?

Ken

---

### Post by spiderbatdad on 2008-04-29
have you tried running ```
sudo dpkg-reconfigure xserver-xorg
```on your Hardy installation?

---

### Post by eryngium on 2008-04-29
nice idea, but I have no means of typing anything after hardy boots up :confused:

---

### Post by spiderbatdad on 2008-04-29
lol...at being slow, I am very quick.
I wonder if you could mount your file system from the live cd and run the command...after the file system is mounted: ```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda? /mnt/root
```of course you need to know the partition number to put in sda...like sda5 in my case.

But another possibility might be to simply try some boot parameters from the Grub menu by pressing 'e' then moving to the kernel line, and pressing 'e' again...then editing the end of the kernel line to remove --quiet splash and replace with pci=routeirq...enter...'b' to boot.

I'm trying to write a how-to on this: [http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/)
if you care to read it.

---

