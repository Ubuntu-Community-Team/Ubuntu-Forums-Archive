---
title: "Stop the process using?"
date: 2013-10-03
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-10-03
How do I stop these processes?

pi@raspbmc:/dev$ sudo lsof | grep /sda

jbd2/sda2   40            root   cwd       DIR        8,2     4096          2 /
jbd2/sda2   40            root   rtd        DIR        8,2     4096          2 /
jbd2/sda2   40            root   txt   unknown                                /proc/40/exe
jbd2/sda3  330            root  cwd       DIR        8,2     4096          2 /
jbd2/sda3  330            root  rtd        DIR        8,2     4096          2 /
jbd2/sda3  330            root  txt   unknown                                /proc/330/exe

I want to umount the /dev/sda2 and /sda3

This is the terminal output of a RaspBMC which is using both the bootable sd card in a Raspberry PI as well as an external hard drive (via USB). The RaspBMC software is set to write all but the boot time files to the USB drive. I have ssh'd into the PI from an external computer.

---

### Post by ikt on 2013-10-03
I would just install htop, then run it as super user (sudo htop), find the processes, f9 and then sigterm/sigkill away.

What is coming up when you try to umount them? There's the possibility of forcing umount.

There's also the option of sudo reboot and then 'umount /dev/sdaX'

---

### Post by Mark_in_Hollywood on 2013-10-03
Sorry, I should have give more info. Following an out-of-date post 

[How to configure, boot, and upgrade Raspbmc on a USB key/hard-drive]("http://www.intraipsum.se/blog/2012/07/14/raspberry-pi-how-to-configure-boot-and-upgrade-raspbmc-on-a-usb-keyhard-drive/") - I created three partitions on an externally connected USB hard drive. Then I discovered the correct (updated) way to do this: [OS X / Linux installation]("http://www.raspbmc.com/wiki/user/os-x-linux-installation/#comments"). As the Raspberry PI is has no way to shutdown, I was looking for a way to umount active partitions. Because I had already performed the actions on the first post, the updated post would not change what was already there. 

pi@raspbmc:~$ sudo initctl stop xbmc
xbmc stop/waiting

pi@raspbmc:~$ sudo umount /dev/sda*
umount: /dev/sda: not mounted
umount: /dev/sda1: not mounted
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

Because I could not umount active devices, I could not "safely" remove the drive. And as I setup, configured and got the RaspBMC working only yesterday, I didn't want to damage the sd card's structure, if at all possible.

But I have taken enough of others' time with this and if the OS or the USB-drive get corrupted, it's only a matter to re-installing the RaspBMC software. Thank you, Ubuntu Community.

---

### Post by steeldriver on 2013-10-03
fyi those were filesystem journaling processes (jbd = journaling block device)

---

