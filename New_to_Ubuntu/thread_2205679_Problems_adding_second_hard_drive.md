---
title: "Problems adding second hard drive"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by david_brown on 2014-02-15
Just trying to configure a simple home server with my old PC. I have the server up and running and accessible via putty. I also have webmin running.

The way I have the PC set up is a 20Gb drive dedicated to Ubuntu and I have a 260Gb and a 2Tb drive that were originaly NTFS when it was windows 7. I then had a play with FreeNAS and am now trying to use Ubuntu. I'd like to format and repartition the two drives for storage. I know I have to format them as FAT32 as I intend them to have windows saving files on them.

Following this tutorial [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) I've tried GParted and am getting myself in knots. I've installed Xming and allow X11 to run and the error I get is:-



root@ubuntu:/home/david# gksudo gparted
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attempted
(gksudo:8619): Gtk-WARNING **: cannot open display: localhost:10.0

I'd like to set the disks up graphically if possible, as following the command line setup procedure is confusing to say the lest - especially as one of the drives is a large one.

Grateful for any help!

---

### Post by steeldriver on 2014-02-15
For your "cannot open display" error, it sounds like you didn't check the PuTTY box for X forwarding (under Connection --> SSH --> X11)

---

### Post by david_brown on 2014-02-15
Hi and thanks for the reply. The box is ticked and I still have the same error

---

### Post by steeldriver on 2014-02-15
OK sorry - I don't use xming much (either stick to pure command line SSH via PuTTY or use a full VNC session)

What X server is running on the other end? You call the box a "server" but did you actually install the server edition (no GUI) or the regular desktop Ubuntu? or is it running something like tightvncserver?

If you have a working SSH connection via PuTTY and then it may be easier to use non-graphical tools (i.e. parted instead of gparted)

---

### Post by david_brown on 2014-02-15
The version installed on the server is [COLOR=#393939][FONT=arial]Ubuntu Linux 12.04.4 and it is headless. I access it via putty on my PC. SHH and PuTTY are working fine. I'm happy to try command line if there is a decent tutorial to follow! [/FONT][/COLOR]

---

### Post by oldfred on 2014-02-15
You do not want FAT32. It has no journal and cannot save files over 4GB.

NTFS is a choice, but if a server using Samba to communicate with Windows it does not matter what format you use and Linux formats may be better.

---

### Post by JnPson on 2014-02-17
This thread is marked as [SOLVED]. It would be nice to know how you solved this. Please include your solution. Thanks.

---

