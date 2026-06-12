---
title: "Bootup failure"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by user9 on 2011-10-10
Helo everyone, I please you to help.
 Some time ago I tried format my usb flash using dd command.  Unfortunately I was wrong with one letter while I was naming erased  device and I tried to erase data from my harddisk. Although I switch off  everything, I couldn't boot for second time and I couldn't se linux  partition. Partition was fortunatelly recovered by test disk and I have  installed GRUB2 after some argue with my computer, I gave connected  right partition to grub (checked) and after that I choose kernel and  initrd.img System had start sucessfully (in text mode) until it failed  with error:

Switching to colour frame buffer device 160x50 ALERT! Dropping to shel!

That dropped me to shell, where are some floders from partition missing  and some other are new (partition is right, it is checked). After  switching to TTY7 I see folowing info:

Give up waiting for root device common problems:
     - Boot args (cat /proc/cmd line)
     - Check rootdelay=(did system wait long enough)
     - Check root=(did system wait for right device?)
- missing modules (cat /proc/modules ls /dev)

Where is mess? How to run GNOME?

PS: I've made some coppies of files according errors written above and I put it into the root directory.
      Where are they now? In the root directory absolutely don't...

---

### Post by Rubi1200 on 2011-10-11
Hi and welcome to the forums :-)

Please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by user9 on 2011-10-11
.

---

### Post by user9 on 2011-10-11
Thanks for answer.

I am sending you the file that you talked. The partition used for repair should be /dev/sda6...

---

### Post by user9 on 2011-10-11
I have just checked, that directory /dev is missing, but unfortunatelly I can't copy it from another device (su or sudo tried, not active system disk tried). Know someone how to do that?

---

### Post by LinuxFan999 on 2011-10-11
Use a live CD to back up your data to external storage, then reinstall Ubuntu.

---

### Post by user9 on 2011-10-11
Trouble is, that I have data stored in encrypted home directory from default, so I cannot simply backup them, because I don't know where they are in the fact stored and how I can open them... If you know, how to restore data from encrypted home directory, please write, I am working on it for several days.

---

