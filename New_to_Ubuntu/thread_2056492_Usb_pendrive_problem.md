---
title: "Usb pendrive problem"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by Donjet on 2012-09-11
Hello 
Im new in ubuntu the reason why i choose to install ubuntu was cause my usb have viruses and the antiviruses in xp couldnt fix my problem . In ubuntu my usb plug out automatically when i try to format the same does when i try to scan it. I delete manually the files in usb when i plug out the usb and insert it the files return back. Avast ,clam av and avg start to scan it but after 1 min the usb plug out automatically and the scan fail . I have used gparted but the same happens it unplug himself when gparted try to write it. Im tired 2 week spent only for my usb and cant repair it . Pls help me . Bye and sorry for my english

---

### Post by mlentink on 2012-09-11
Sounds very much like a hardware issue to me. The fact that your USB-drive seems to 'unplug' means the connection is dropped, which leads me to suspect hardware failure. I would restore my backup to a new USB-drive if I were you.

---

### Post by Donjet on 2012-09-12
> **mlentink said:**
> Sounds very much like a hardware issue to me. The fact that your USB-drive seems to 'unplug' means the connection is dropped, which leads me to suspect hardware failure. I would restore my backup to a new USB-drive if I were you.
No I dont think is a hardware failure cause in xp it dont unplug himself but you cant do anything in it it says only write protected . I think the virus have writed the files when they are prepared to delete the virus see that he's gona formated or deleteed and unplug himself :S

---

### Post by mips on 2012-09-12
Do you want to erase/format the pendrive?

If you then make sure the pen drive is plugged in and post the output of the following command here:

```
sudo fdisk -l
```

Which device in the above output is your pendrive, should say something like "Disk /dev/sdX X.XGB, XXXXXXXX bytes"

---

### Post by Donjet on 2012-09-12
> **mips said:**
> Do you want to erase/format the pendrive?

If you then make sure the pen drive is plugged in and post the output of the following command here:

```
sudo fdisk -l
```Which device in the above output is your pendrive, should say something like "Disk /dev/sdX X.XGB, XXXXXXXX bytes"
Here is the output And yes i wanna erase all my data :
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c8182ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4017 MB, 4017749504 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7847167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009cc5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7862910     3931424    b  W95 FAT32


When you dont use the usb it can stay about 3 minutes and unplug himself automatically And if you use it example format or scan it goes out immediately !

---

### Post by mips on 2012-09-12
> **Donjet said:**
> Here is the output And yes i wanna erase all my data :

Disk **/dev/sdb**: **4017 MB**, 4017749504 bytes
<snip>

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7862910     3931424    b  W95 FAT32


When you dont use the usb it can stay about 3 minutes and unplug himself automatically And if you use it example format or scan it goes out immediately !

Ok if your pendrive is 4GB in size then it's /dev/sdb, is that correct?

If it's the correct device then execute this command,

([COLOR="Red"]Warning! make sure you copy and paste this or write it out exactly like that as dd can cause catastrophic data loss if you specify the wrong device[/COLOR])

```
dd if=/dev/zero of=/dev/**sdb** bs=1M
```

The above command essentially overwrites /dev/sdb (your pendrive) with zeros, it will wipe the master boot record, partitions & any data you have on the device.

Try that and see how it goes.

Once it's completed you can open gparted (install it if you dont have it already installed and then you can create a new partition table and format the device. gaprted menu, Device-->Create Partition Table type msdos and then you can format creat a new partition and format it with whatever filesystem type you want, fat, fat32, ntfs, ext3/4 etc.

---

### Post by Donjet on 2012-09-12
> **mips said:**
> Ok if your pendrive is 4GB in size then it's /dev/sdb, is that correct?

If it's the correct device then execute this command,

([COLOR="Red"]Warning! make sure you copy and paste this or write it out exactly like that as dd can cause catastrophic data loss if you specify the wrong device[/COLOR])

```
dd if=/dev/zero of=/dev/**sdb** bs=1M
```

The above command essentially overwrites /dev/sdb (your pendrive) with zeros, it will wipe the master boot record, partitions & any data you have on the device.

Try that and see how it goes.

Once it's completed you can open gparted (install it if you dont have it already installed and then you can create a new partition table and format the device. gaprted menu, Device-->Create Partition Table type msdos and then you can format creat a new partition and format it with whatever filesystem type you want, fat, fat32, ntfs, ext3/4 etc.

Thank you so much for reply but isnt workin it says /dev/sdb permission denied

---

### Post by mips on 2012-09-12
> **Donjet said:**
> Thank you so much for reply but isnt workin it says /dev/sdb permission denied

you have to run it with sudo, sorry.

```
sudo dd if=/dev/zero of=/dev/sdb bs=1M
```

---

### Post by Donjet on 2012-09-12
> **mips said:**
> you have to run it with sudo, sorry.

```
sudo dd if=/dev/zero of=/dev/sdb bs=1M
```

it do nothing it stays sudo dd... Tell me to write pasword i write and it do nothing my usb unplug same and i waited 20 min the terminal only make my pc not responding but thanks from you.

---

### Post by mips on 2012-09-12
> **Donjet said:**
> it do nothing it stays sudo dd... Tell me to write pasword i write and it do nothing my usb unplug same and i waited 20 min the terminal only make my pc not responding but thanks from you.

Then you have a faulty pendrive or usb port issues. Can you try formatting the pendrive on another pc?

If dd can't write to it I doubt anything else will.

---

### Post by gandaran on 2012-09-12
>  In ubuntu my usb plug out automatically when i try to format
sorry but I'm having difficulty trying to understand your problem.
when you try to format you have to unmount the usb drive, you will have to mount the drive again to see files or scan the drive.
also everytime you use the usb drive on an infected Windows PC the virus return to the drive, to avoid reinfecting the drive in Windows all you have to do is disable autorun on the windows machine.

---

### Post by Donjet on 2012-09-12
> **gandaran said:**
> sorry but I'm having difficulty trying to understand your problem.
when you try to format you have to unmount the usb drive, you will have to mount the drive again to see files or scan the drive.
also everytime you use the usb drive on an infected Windows PC the virus return to the drive, to avoid reinfecting the drive in Windows all you have to do is disable autorun on the windows machine.
i unmount it using terminal gksu nautilus and go to disk utility and try to format it says device is busy i try to erase the volume it says device is busy when i try to muont it , it says writing data and after 1 minute came a error that you have pluged out the usb . For format with te terminal it doesnt work it only make my pc not responding and the usb goes out atomatically !

---

### Post by gandaran on 2012-09-12
> **Donjet said:**
> i unmount it using terminal gksu nautilus and go to disk utility and try to format it says device is busy i try to erase the volume it says device is busy when i try to muont it , it says writing data and after 1 minute came a error that you have pluged out the usb . For format with te terminal it doesnt work it only make my pc not responding and the usb goes out atomatically !
you don't need to use the terminal, use gparted to unmount before formatting then to mount again just click the drive in the file browser, this is very simple I think you are doing it the wrong way or using wrong tools (for format only gparted can do it) and if it says device is busy just remove it then plug in the device again.

---

### Post by geronl on 2012-09-12
> **Donjet said:**
> it do nothing it stays sudo dd... Tell me to write pasword i write and it do nothing my usb unplug same and i waited 20 min the terminal only make my pc not responding but thanks from you.

If you poke that thing into an Xbox as if to save a game it would need to reformat it I think.

---

