---
title: "ubuntu force me to install only on the usb stick which have only 8.1 gb"
date: 2018-06-08
forum: New to Ubuntu
---

### Post by benist on 2018-06-08
Hello

I'm using win 10 and I want to install ubuntu in addition.
The problem is that after I make the USB boot device and start the installation, I have no option to choose on whice drive i want to install the OS.

Im getting the "you need at least 8.6 gb to install ubuntu this computer has only 8.1 gb" message.

I'm using dell xps 13 - just in case its important....

I used rufus to make the boot usb device.

thanks for you help
Ben

---

### Post by yancek on 2018-06-08
Before you start the install, I would strongly recommend you read the Ubuntu documentation on dual booting with windows 10 at the link below.

ttps://help.ubuntu.com/community/UEFI

Are you using the manual installation method, referred to as Something Else in Ubuntu?  You should.  Did you shrink your windows partition to create free/unallocated space on the drive?  You should use windows Disk Management to do this. You will need to create partitions and format with Linux filesystems to use for Ubuntu.   Make sure you turn off fastboot and anything related to hibernation which are on by default in windows 10.  When you are booted into the Ubuntu install media, open a terminal and run the following command and post the output here.

```
sudo parted -l
```

---

### Post by leunam12 on 2018-06-08
Disable hibernation on Windows and retry

[https://www.cnet.com/how-to/how-to-enable-or-disable-hibernate-in-windows-10/](https://www.cnet.com/how-to/how-to-enable-or-disable-hibernate-in-windows-10/)

---

### Post by benist on 2018-06-08
I run the code line in the ubuntu that loaded from the usb (without installation)

ubuntu@ubuntu:~$ sudo parted -l
Model: General USB Flash Disk (scsi)
Disk /dev/sda: 8053MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  8053MB  8052MB  fat32        Microsoft Basic Data  msftdata



although it cant be seen i have a 12 gb unalocated free space.
i turn of the hibernation
and disable the fast boot

anything else?

---

### Post by oldfred on 2018-06-08
Did you disable Windows hibernation?

Dell also need update to UEFI from Dell.
And if SSD, you need to update firmware for NVMe drive.

Dell also has drives set for RAID. And unless truly running RAID, you need to change to AHCI. But install AHCI driver into Windows first, so it still boots.
       Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe 
    
       XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
RAID to AHCI
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on/963100#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on/963100#963100)

---

