---
title: "desktop background picture doesn't work unless...."
date: 2008-10-23
forum: New to Ubuntu
---

### Post by soona86 on 2008-10-23
i changed my background picture..
and it doesn't work unless i open the drivers in my computer (D) or (E) because the pic is on the drive D

it's like i activate it's memory or something to make it remember that there's a drive that has the pic that i chose on desktop..
i know it realises that i changed the pic..but it can't show it unless i d.click the drive..
i think it's like the (mounting) thing or something..

shortly : my question is

how can i make this work without d.clicking it every time i login!

second, if it's about (mounting) the drivers or something..

what does it mean to (mount) i know i do it when i use daemon tools but that's when i use a removable drive..but my hard drive? to mount it every time?!
and another thing..
when i explore the drives they appear on the desktop..then the next time i login they're not there..

is about this (mounting) thing? and WHAT IS mounting?!

sorry if my english is not so good..

plz answer in simple english...thanks in advance..

p.s. i installed ubuntu from windows..when i turn on my machine it gives two choices etc......i don't know if that effects the mounting thing or not..but i thought i should mention that..

---

### Post by dtsat on 2008-10-23
Simply copy the picture to your "Pictures" folder, under the "Places" menu at the top.

Then, open System -> Preferences -> Appearances, select the "Background" tab, and click the "add" button.

It will automatically open to the "Pictures" folder. From there, it should permanently be there ;-)

---

### Post by Bucky Ball on 2008-10-23
> **soona86 said:**
> 
i think it's like the (mounting) thing or something..

shortly : my question is

how can i make this work without d.clicking it every time i login!

second, if it's about (mounting) the drivers or something..

what does it mean to (mount) i know i do it when i use daemon tools but that's when i use a removable drive..but my hard drive? to mount it every time?!

Simply, you need to mount them at boot. Or automount them at boot.

When you click on a drive/partition in 'Places' it is auto-mounted. If you then right click on the icon on the desktop, you will notice you can then unmount the drive also. What needs to happen is that when you start your machine, there is an instruction in your:

```
/etc/fstab
```Open a terminal and paste in:

```
nano /etc/fstab
```You will see a file that looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=36bd7710-ca84-48c9-9011-e96d336ba192 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=653d41d1-f3d8-4e3c-8fdd-a298084b754c none            swap    sw              0       0
/dev/sdc0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda7
UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/bigboy   ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=4893-E3A6                            /media/fatso    vfat    defaults,umask=0002,gid=46 0 0
```On closer inspection, notice that they are the drives and UUID number of your partitions on your drives with their labels. Please copy and paste the results of:

```
sudo fdisk -l
sudo blkid
```Paste these two commands one at a time into a terminal and copy and paste the information in a post here. We should be able to get you partitions automounting. :)

ps: nothing to do with drivers. You are right kinda, the hard drive/partition needs to be mounted to access the picture for the desktop background.

---

