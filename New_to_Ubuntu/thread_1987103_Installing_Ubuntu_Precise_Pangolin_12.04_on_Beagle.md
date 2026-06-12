---
title: "Installing Ubuntu Precise Pangolin 12.04 on BeagleBoard xM . Cannot Boot"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by ElEsGato on 2012-05-25
I am trying to install Precise Pangolin 12.04 on my Beagleboard XM.

I've downloaded from here: [https://wiki.ubuntu.com/ARM/OMAP](https://wiki.ubuntu.com/ARM/OMAP)

and used instructions here: 

[https://wiki.ubuntu.com/ARM/OmapDesktopInstall](https://wiki.ubuntu.com/ARM/OmapDesktopInstall)  

[I][B]Download the image and extract it with the system archive utility, you should get a .img file if the disk is mounted disk1.. disk2.. not - disk0, unmount it with the following code.

sudo diskutil unmountDisk disk1
Then use the following code to write the image to disk1 (not - disk1s1..)

sudo dd bs=4m if=ubuntu-12.04-preinstalled-server-armhf+omap4.img of=/dev/disk1
If you get any errors trying to run the following code then try reinserting the SD card and trying again after unmounting the disk, or try formatting it first with DiskUtilities[/B][/I]

I believe I am doing this, but when I pull the SD card from my macbook and put into the Beagleboard, nothing happens.  The instructions say that I should just insert the card and it should boot.  

When I run a DiskUtil List on my command console on my macbook, I see that it lists: /dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *15.9 GB    disk1
   1:             Windows_FAT_32                         75.5 MB    disk1s1
   2:                      Linux                         2.0 GB     disk1s2


Is it a problem that the Linux is on disk1s2 instead of disk1? 

Thank you for the help!

---

### Post by samitharansara on 2012-08-15
Bump..

---

