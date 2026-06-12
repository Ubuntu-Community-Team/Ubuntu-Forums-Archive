---
title: "New to Ubuntu, can't boot from Windows partition"
date: 2015-07-18
forum: New to Ubuntu
---

### Post by jackbrandt11 on 2015-07-18
Yesterday, I created a 25 gb partition on the hard drive I'm using (1000 gb) via the already installed Windows 7. I then downloaded the Ubuntu 14.04 ISO, and put it onto a flash drive with the help of a program suggested by the Ubuntu site (I don't remember what I used...I can't access it anymore). I then booted from the flash drive, and installed Ubuntu onto the 25 gb partition on the hard drive (i had to format it to ext4 or something of the sort). The rest of the partitions, including Windows, remain untouched. I now cannot access the Windows boot mode or whatever it is called (boot loader?), and this is a major issue for me. I've been searching around for the past 2 hours trying to find the same problem, and I can't find anything that works.

---

### Post by toxx on 2015-07-18
Are you reaching the grub screen? If so, login to ubuntu, run update-grub, reboot and see if windows is available in the boot list.

---

### Post by Mark Phelps on 2015-07-19
The command to run, in a terminal is > sudo update-grub

The "sudo" is needed because you have to run it as superuser in order to update the boot components.

---

