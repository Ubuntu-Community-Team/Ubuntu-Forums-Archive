---
title: "Unable to mount external hd"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by gzav on 2008-11-28
Hi all,

very new to linux, i'm currently using it on a usb key to get the hang of it before installing it for ever. Up to now it's been great, but i've got a kinda serious problem.

I have an external hd that i use to store all my documents which i'm working on. When i first used xubuntu, i had no problem accessing this hd and all my docs when i plugged it in the USB drive. But for some reason, when i try later, i get an error message stating that my hd can't be mounted and i can't access it.

The error message is this:

"Unable to mount the volume 'Lacie USB'

details:
mount: according to mtab, /dev/sdc1 is already mounted on /media/Lacie USB"

The weird thing is, i had that same problem a few days ago, but when i restarted windows, and accessed my hd there without a problem, then came back to xubuntu, i didn't get the error message again. Well, until now that is...

I have no idea what is wrong, so if anyone could shed some light on this and help me out, i'd be very very much obliged!

Thanks!

---

### Post by Michael.Godawski on 2008-11-28
Make sure you have safely removed the external drive in Windows. Do so and try again to plug it in while being on Linux.

Please also post the output of these terminal commands:

```
sudo fdisk -l
cat /etc/fstab
ls -la /media

```

---

### Post by gzav on 2008-11-28
Went back to Windows, unplugged it cleanly and plugged it back in linux, same problem

here's the result from the commands:

**ubuntu@ubuntu:~$ sudo fdisk -l**
$
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c150c14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        5045    37447515    c  W95 FAT32 (LBA)
/dev/sda3            5046        9729    37624230    f  W95 Ext'd (LBA)
/dev/sda5            5046        9729    37624198+   b  W95 FAT32

Disk /dev/sdb: 4109 MB, 4109592064 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003b7c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         500     4013242    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(498, 254, 63) logical=(499, 160, 32)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc796501a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS

[B]
ubuntu@ubuntu:~$ cat /etc/fstab[/B]
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


**ubuntu@ubuntu:~$ ls -la /media**
total 8
drwxr-xr-x  2 root root 4096 2008-11-28 09:49 .
drwxr-xr-x 33 root root 4096 2008-11-28 10:47 ..
-rw-r--r--  1 root root    0 2008-11-28 10:48 .hal-mtab
-rw-------  1 root root    0 2008-11-28 09:49 .hal-mtab-lock

---

### Post by taseedorf on 2008-11-28
well, did you try looking in /media/Lacie Usb to see if it is mounted in there?

or try this in a command line
sudo umount /dev/sdc1

than try this

sudo mkdir /media/externalUSB
sudo mount /dev/sdc1 /media/externalUSB

see if that works.

is Xubuntu saving the configuration information to the USB key you have it on? Sometimes, for whatever reason, there is an option than gets set so it does not save (it wont if you have a live disk)....... you can try editing your /etc/fstab file
with
sudo gedit /etc/fstab

than adding a line (after creating the folder in /media called externalUSB

/dev/sdc1 /media/externalUSB ntfs3g defaults 0 0

---

### Post by gzav on 2008-11-28
Thanks for the help, it worked, i can now access my hd!

But as to the 2nd part, i tried you sudo gedit command, but the terminal tells me that the command is not found...?

---

### Post by Dedoimedo on 2008-11-28
Hi,

You're running Xubuntu. gedit is the text editor for Gnome (Ubuntu). So you need a different text editor. I don't remember what the default on Xubuntu is.

You can always use the dirty terminal text editor like vi, but it's not easy for new users.

Dedoimedo

---

