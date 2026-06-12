---
title: "Format bootable USB disk"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by krnchwg on 2011-11-18
I created a bootable USB disk to install ubuntu. Is there anyway I can format that usb disk for it to return to regular storage usb? Thanks!

---

### Post by mike555 on 2011-11-18
To format (erase) the usb I would use gparted (making sure you are on the right one) and format it to fat32 .

---

### Post by WasMeHere on 2011-11-18
Welcome to the Ubuntu Forums, krnchwg,

If it is bootable is no problem if you want to use it as a regular drive. Or you can simply remove the files and use it.

But maybe you created some partition(s) that you want to get rid of, or you want to change to another file-system. Then download ***gparted*** and use it to edit partition(s) of your USB disk! It should ***not*** be mounted during the editing. And remember that all data on the disk will be destroyed. So save documents, photos etc before you start with gparted!

```
sudo apt-get install gparted
```

Have fun finding out :-)
Olle

---

### Post by krnchwg on 2011-11-18
There's an issue here: the usb is not detectable.

---

### Post by WasMeHere on 2011-11-18
Try different USB connectors! Try if possible different computers!

What USB disk is it? Size, type etc... Will you see it with the following command?
```
sudo fdisk -lu
``` In that case, post the output of the command in a new reply!

---

### Post by krnchwg on 2011-11-18
it is 4GB PQI Model U339S

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061801

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   300920831   150459392   83  Linux
/dev/sda2       300922878   312580095     5828609    5  Extended
/dev/sda5       300922880   312580095     5828608   82  Linux swap / Solaris

---

### Post by WasMeHere on 2011-11-18
So fdisk does not find your bootable USB disk (it finds only the internal hard drive). Then most linux tools cannot reach it either. 

Can you see it from another computer or USB connector? It is worth trying before deciding that the hardware of the USB disk is damaged.

---

### Post by audiomick on 2011-11-18
Doesn't seem to be there. Try
```
sudo lsusb
```
You will be asked for you password, which you will not see as you are typing it. Type it and hit enter.

This command will list everything that is plugged into a usb port, and all of the empty ports. If the drive is not there, there is something very fundamental wrong with it, I think.

---

### Post by krnchwg on 2011-11-18
It is detectable once i plugged into Windows 7. However, it cant be seen in My Computer.

---

### Post by WasMeHere on 2011-11-18
> **krnchwg said:**
> It is detectable once i plugged into Windows 7. However, it cant be seen in My Computer.

Then there is hope. Try to (re)format it to FAT32 using Windows 7.

---

