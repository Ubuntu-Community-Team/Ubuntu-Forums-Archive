---
title: "Problem with usb boot"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by The Toaster on 2013-03-10
Hi,

I decided to install Ubuntu 12.10 onto a 16gb usb drive I had to spare, and to do this I followed the instructions here: [http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive)

All the steps went fine, it all seemed to be working fine, until I tried to boot the usb. I ended up at the grub command line, and so I go ahead and set the root and the kernel, and then boot it. When I do this I receive the following message.


```
 VFS: Cannot open root device "(null)" or unknown block(0,0) error -6
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
pid : 1, comm: swapper/0 Not tainted 3.5.0-17-generic #28-Ubuntu 
```

I have searched extensively and have come to no answer, just stuff about changing the kernel, but I used the same kernel that the liveusb boots from, and that works fine. It seems to be unable to see the partition I just booted from, or the partition with the system files.

Any ideas?

---

### Post by sudodus on 2013-03-10
Welcome to the Ubuntu Forums :-)

First check with md5sum that the iso file was downloaded without errors.

I suggest that you install ***Unetbootin*** and use it to create a USB boot drive. There are versions for linux as well as for Windows.

Erase the files from your USB drive (or reformat it to FAT32).

Then run Unetbootin and follow the instructions in the graphical user interface. It is rather easy to understand.

---

### Post by oldfred on 2013-03-10
With a 16GB flash you can do a full install. My 16GB has 8GB for a full install and 8GB for data. 

With grub on flash drive you do not have to extract kernel to boot. Ubuntu with grub2 will directly mount ISO files. Some ISO files do have to have the kernel extracted as posted.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Newer version of grub have a slightly different mount that includes the user. Older versions were just /media, new is /media/fred (for me).
      
 How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

    
      
 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
      
 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

But my full install is just like any install to another hard drive. You have to use Something Else or manual install to get the option on where the install will install grub2's boot loader and you want it on the flash drive often sdb, but not sda which is used by all the default installs.
      
 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

I used gpt partitioning as I wanted to learn about it. But once created I cannot see any difference.
```
fred@A105-Precise:~$ sudo parted /dev/sdb unit s print
[sudo] password for fred: 
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 31375360s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4         12_04
 3      14749696s  29327359s  14577664s  ext4         KingstonData
 4      29327360s  31373311s  2045952s   ntfs

```

---

