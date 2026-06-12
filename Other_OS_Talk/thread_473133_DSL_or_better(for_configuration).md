---
title: "DSL or better(for configuration)"
date: 2007-06-13
forum: Other OS Talk
---

### Post by dracule on 2007-06-13
I have been searching and searching for a way to configure dsl (keep programs i download, save my config etc) but i cant seem to find any. every thing that i have looked at says to save it to your hdd, well the comp i am using doesnt have a hdd. so if anyone can tell me how to accomplish this. the only storage medium i have is a usb flash drive. thank you.

---

### Post by johnny4north on 2007-06-13
> i have chosen puppy linux 2.15 ce final. why, well because of the ease of install, on the usb stick and saving data on the usb, cd-r or harddrive. it took 5min to install and set-up networkcard. 40 seconds to boot. i tested seamonkey(ok) and watched a dvd. the dvd keep blinking. i wasted 3hr trying to correct. installed mplayer and firefox. installed 3DCC utilitty and other pet packages. then finally the nividia drivers w/ the 3DCC. the kittens and i watched best "the two towers". very clear and smooth. i will save about 10-20 watts per hour(est.) somemore tweaking and customizing, then remaster a custom live-cd. done. good call bodhi.zazen thank you all.
links - [http://www.puppylinux.org/user/downloads.php](http://www.puppylinux.org/user/downloads.php)
           [http://rhinoweb.us/](http://rhinoweb.us/)
it took 5min to install to usb and 1/2 hour to install packages.:) note- very solid os.  i tryed very hard to crash it, and it already suvived two power outages.  still running well.

---

### Post by Shazaam on 2007-06-13
wiki...
[http://www.damnsmalllinux.org/wiki/index.php/Persistence](http://www.damnsmalllinux.org/wiki/index.php/Persistence)

---

### Post by dracule on 2007-06-13
> **Shazaam said:**
> wiki...
[http://www.damnsmalllinux.org/wiki/index.php/Persistence](http://www.damnsmalllinux.org/wiki/index.php/Persistence)

i saw that... and it explains how to do it on a different media...i need to do it on the same stick.

---

### Post by dracule on 2007-06-13
> **johnny4north said:**
> links - [http://www.puppylinux.org/user/downloads.php](http://www.puppylinux.org/user/downloads.php)
           [http://rhinoweb.us/](http://rhinoweb.us/)
it took 5min to install to usb and 1/2 hour to install packages.:) note- very solid os.  i tryed very hard to crash it, and it already suvived two power outages.  still running well.

i looked around and found nothing on how to do it on a usb, the link you gave me was for a cd.

---

### Post by johnny4north on 2007-06-13
> i have chosen puppy linux 2.15 ce final. why, well because of the ease of install, on the usb stick and saving data on the usb, cd-r or harddrive. it took 5min to install and set-up networkcard. 40 seconds to boot.
after you boot the livecd. look for the "puppy univisal installer" start it and follow directions(install to usb, and i chose to have linux puppy use the whole usb stick).   oh, you may have to mount the usb stick w/ Drives>Media utility tool, before you start the install.  click drives, then usb flash mem(mount).  note-your usb stick should be allready formated out of box(fat 16). correct me if wrong.. you may want to set-up yours to use half the usb stick.  you may resize it later. installer here - menu>  settup>puppy univisal installer.  goodluck.:)

---

### Post by dracule on 2007-06-13
> **johnny4north said:**
> after you boot the livecd. look for the "puppy univisal installer" start it and follow directions(install to usb, and i chose to have linux puppy use the whole usb stick).   oh, you may have to mount the usb stick w/ Drives>Media utility tool, before you start the install.  click drives, then usb flash mem(mount).  note-your usb stick should be allready formated out of box(fat 16). correct me if wrong.. you may want to set-up yours to use half the usb stick.  you may resize it later. installer here - menu>  settup>puppy univisal installer.  goodluck.:)

did what you said, but my condition makes me have to use wakepup. the installer only lets me select ext2 (maybe ext3) and vfat but when i use teh wakepup floppy it says that it has to be in DOS fat16 or fat32 for it to find it. should i partition the flash drive so it is like 200 for pup, 800 for files (since in the installation it says something about you having to make some partion if you choose vfat...

hopefully all this formattin wont fry my stick.

---

### Post by johnny4north on 2007-06-13
i used the live cd to install to usb stick(fat 16) with no formating. are you using you using floppy or live-cd?  formating usb should be ok.  i would give the usb sticks mem time to cool down(1 min.) before install.

---

### Post by dracule on 2007-06-13
> **johnny4north said:**
> i used the live cd to install to usb stick(no formating) with no formating. are you using you using floppy or live-cd?  formating usb should be ok.  i would give the usb sticks mem time to cool down(1 min.) before install.
here is what i did:
put the live cd in my comp (this isnt the one im usin the usb on)
mount my usb drive
install it (i guess i choose the wrong option last time)
once it is done i went to create wakepup floppy disk since my comp's bios does not support usb
now when i load it up, it finds teh stick, but it gets stuck at loading kernel modules

---

### Post by johnny4north on 2007-06-13
here is a link w/ possible solution - [http://www.murga-linux.com/puppy/viewtopic.php?search_id=1974128657&t=7979](http://www.murga-linux.com/puppy/viewtopic.php?search_id=1974128657&t=7979)  does the usb stick boot on the other pc?
> Notes
-----
- wakepup2 can only find Puppy2 files on DOS (FAT16 or FAT32) formatted partitions.

- wakepup2 does not seem to work with some USB flash drives. Check Puppy Linux Wiki for tips on working USB flash drives.

- If wakepup2 cannot find your USB flash device, it may help to re-format it (FAT16).

---

### Post by johnny4north on 2007-06-13
i believe that you need to format the whole usb stick to fat 16. note below - Notes
> -----
- wakepup2 can only find Puppy2 files on DOS (FAT16 or FAT32) formatted partitions.

- wakepup2 does not seem to work with some USB flash drives. Check Puppy Linux Wiki for tips on working USB flash drives.

- If wakepup2 cannot find your USB flash device, it may help to re-format it (FAT16). i believe soon you will have linux puppy running :).

---

### Post by johnny4north on 2007-06-13
> How to make a wakepup2 floppy disk
----------------------------------
With a formatted 1.44MB diskette in the floppy drive, do one of the following:

1) In DOS/Windows, unzip WKPUP202.ZIP in a temp dir and execute MAKEDISK.BAT

2) In Linux, copy WKPUP202.ZIP to a temp dir and execute:
# unzip WKPUP202.ZIP
# dd if=WKPUP202.IMG of=/dev/fd0 bs=1440k

Using wakepup2
--------------
I have provided the marker files IDEHD, USBHD and USBFLASH for convenience on the wakepup2 floppy. Just copy the one you need to the drive you want to boot from containing the Puppy2 files INITRD.GZ, PUP_xxx.SFS and VMLINUZ. The CD-ROM doesn't need a marker file.

Examples of booting Puppy2 with wakepup2:

- Boot from a built-in hard disk: copy the IDEHD marker file to the drive containing the Puppy2 files, then boot using wakepup2.

- Boot from a USB hard disk: copy the USBHD file to the drive containing the Puppy2 files, then boot using wakepup2.

- Boot from a USB flash pen: copy the USBFLASH file to the drive containing the Puppy2 files, then boot using wakepup2.

- Boot from a built-in IDE or external USB CD-ROM: no marker file is needed - wakepup2 should find the Puppy2 files anyway.

wakepup2 will pause after the USB driver has scanned for USB devices. If it detects one, it will print a short id string. If not, it will print "Target USB device not found".

Notes
-----
- wakepup2 can only find Puppy2 files on DOS (FAT16 or FAT32) formatted partitions.

- wakepup2 does not seem to work with some USB flash drives. Check Puppy Linux Wiki for tips on working USB flash drives.

- If wakepup2 cannot find your USB flash device, it may help to re-format it (FAT16).
this solution is from this site - [http://www.murga-linux.com/puppy/viewtopic.php?search_id=1974128657&t=7979](http://www.murga-linux.com/puppy/viewtopic.php?search_id=1974128657&t=7979)

---

### Post by dracule on 2007-06-13
> **johnny4north said:**
> i believe that you need to format the whole usb stick to fat16 which should work. note below - Notes
 i believe soon you will have linux puppy running :).
it is in fat32, and it now loads the kernel off the usb (light flashes, floppy is silent), but when it loads the kernel modules, the activity light on the usb stops. i think i may be missing a file or something on my usb drive here is what i have:
```
initrd.gz
pup_215.sfs
syslinux.cfg
USBFLASH
vmlinuz (no extention, i thought it was .gz)
zdrv_215.sfs
```

I really appreciate you help

---

### Post by johnny4north on 2007-06-13
the fat 32 seems to be alright. which wakepup 1 or 2 ?

---

### Post by johnny4north on 2007-06-14
Make bootable usb drive with puppy on it from in Windows (with/without CD/DVD drive)
1.format your stick using the Fat16 or Fat32 file system. To do this you can Download and install the HP USB tool.  By running HPUSBFW.EXE with admin rights you can format the usb drive [http://h18023.www1.hp.com/support/files/server/us/download/26504.html](http://h18023.www1.hp.com/support/files/server/us/download/26504.html)
If you can read files on your usb drive you probably won't need to do this.
2.Download the Puppy Linux ISO.
3.Open the ISO using a program that can read iso images such as Izarc or winrar.
Extract the files from the ISO (or CD) to a folder on your harddrive, then to the root of your USB stick.
(There will be a single 'boot.images' directory amoung the other files.)
4.Rename isolinux.cfg to syslinux.cfg (not case sensitive)
5.open syslinux.cfg and
change &#8220;PMEDIA=idecd
timeout 50
&#8220; to &#8220;PMEDIA=usbflash&#8221;
6.Download syslinux-3.36.zip and unzip the files to a directory named syslinux on your computer.
[http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.36.zip](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.36.zip)
7.Go to the win32 directory of the syslinux folder that was created (\syslinux\win32)
8.Type syslinux.exe F: (replace F with your USB drive letter) to make the drive bootable.
9.Reboot your PC, go into your system BIOS and set your boot order to boot from a selectable USB device. (example USB_ZIP or use USB_HDD)
10.Save your BIOS settings. On the next reboot, you should have a successful launch of Puppy Linux from your USB memory stick.
i found this at [http://murga-linux.com/puppy/search.php](http://murga-linux.com/puppy/search.php) i re-did my usb stick and had similar difficulty's (2 days) i found this [http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html](http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html) formated and deleted files off usb. used the livecd to install to usb.  on exiting puppy i did not save, after the reboot, i then saved the pup file(it will then ask you how much of the usb to use for pupfile{all}).  you are done, ten minutes...yeeees :)  i m hopeful you GED. :)

---

