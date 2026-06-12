---
title: "Ubuntu no longer boots after updates"
date: 2020-06-22
forum: New to Ubuntu
---

### Post by ersigh on 2020-06-22
Greetings,

A little background that may or may not be useful (ignore if not useful - I'm wordy):

I have a Dell Latitude Precision running Ubuntu 20.04 LTS. I got this machine beginning of March and it was basically trying to be a brick for that first month because of some random bug. If I reinstalled Ubuntu (any version, the Dell flavored one or others) it would work but then if updated the system it would then stop booting and I could not consistently get to any recovery options, etc. It would hard lock and the fans would spin up. And even on the occasion I could get into recovery mode it did not let me boot Ubuntu. I worked with a tech and he found a bug involving an update with the kernel and intel processors that once a patch was rolled out fixed my issue. My machine has been working fine until last week when I installed some updates and now it won't boot correctly. It's not behaving EXACTLY like the original issue but pretty similar so I am chasing the hope it's just a borked update install and not a hardware issue or another obscure bug.

If I reboot my machine it hangs either at the Dell logo screen or right after. It hard locks and the fans spin up on high. Another reboot and I am given recovery options, etc. I can not boot into the more recent version of the linux kernel (5.4.0-37-generic), even in recovery mode. It just locks. I can boot into the older version (5.4.0-33-generic).

I have tried running repairs/checks. I installed and ran boot-repair ([https://paste.ubuntu.com/p/bBxTGdfzkw/](https://paste.ubuntu.com/p/bBxTGdfzkw/) <-- I don't see anything at that link but it was the one supplied to me after using boot-repair). None of this changed anything. I also tried doing a reinstall but I got an error saying there was no EFI partition even though I can see it in the partition options. My stuff is backed up so I can easily reinstall from scratch but I feel like I'm going to be trapped in a cycle where I have to reinstall my OS every time there is an update if I don't learn how to navigate when this stuff happens and I think I know just enough to get into trouble. I have been googling how to do tasks I think are related (like the boot-repair stuff) but I feel like I'm missing something and would love some guidance/help. I guess I don't feel like I even know the questions I need to be asking. 

I tried to attach a few images of my screen but they don't show up in the management area after uploading them and I didn't see any error message to know if the files were too large or there was some other issue. I put them in a dropbox folder: [https://www.dropbox.com/sh/y8s2k4rjtdchjzp/AADf57bZj-1iMnH0Dc69XDrba?dl=0](https://www.dropbox.com/sh/y8s2k4rjtdchjzp/AADf57bZj-1iMnH0Dc69XDrba?dl=0) - I hope that's ok!

Thanks in advance!

---

### Post by oldfred on 2020-06-22
Pastebin link not working.

Have you updated UEFI from Dell and SSD firmware?

A few users have had corruption on the ESP, FAT32 partition. And in rare cases they had to delete it and recreate it which then requires reinstall of all boot loaders, and removal of old UEFI entries to old ESP.

sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Change above examples (they all are essentially the same) to your correct partition, sda1, sda2, or nvme0n1p2 etc.

---

### Post by hugoparc on 2020-06-23
Excelente tutorial

---

### Post by ersigh on 2020-06-23
> **oldfred said:**
> Pastebin link not working.

I will try again tomorrow and see if maybe I missed something in a tired haze.

> **oldfred said:**
> Have you updated UEFI from Dell and SSD firmware?

BIOS yes - SSD no. I have a Precision 3540. It is not on the list of devices that are compatible with the firmware update. The firmware looks like it's only available to Windows machines currently.

> **oldfred said:**
> A few users have had corruption on the ESP, FAT32 partition. And in rare cases they had to delete it and recreate it which then requires reinstall of all boot loaders, and removal of old UEFI entries to old ESP.

sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Change above examples (they all are essentially the same) to your correct partition, sda1, sda2, or nvme0n1p2 etc.

I took these steps and everything ran fine but it did not change the behavior. It still hangs on boot and I need to select the older kernel to use the system.

---

### Post by oldfred on 2020-06-23
Issues are common by brand and similar models. Bigger difference if AMD or Intel.
With Dell even different series, 3000, 5000, 7000, even 9000 have similar UEFI and issues. Just different features implemented.

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell Precision 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized)

UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/lvfs/devices/com.dell.uefi5a05eb25.firmware](https://fwupd.org/lvfs/devices/com.dell.uefi5a05eb25.firmware)

For my Samsung SSD, I went to Samsung site and they had a bootable ISO just for the latest firmware for my NVMe drive. It looked more like an old DOS screen and just updated firmware, no other options.

---

### Post by ersigh on 2020-06-23
Thanks oldfred.

I read through the links and went from there. Dell has the firmware update for my specific drive ([https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=7ry97](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=7ry97)) but it is for Windows so I looked at Toshiba/KIOXIA. My drive is not listed for the SSD utility tool for either but I tried them just in case since the drive nomenclature varied and why not? Neither can see my drive so I am ASSuming that means the drive is not compatible. The BIOS is set correctly for the utilities (and was updated last week). 

Are there any logs or anything that I could look at/share that might be useful? I really have no idea where to start with that.

I am leaning towards reinstalling the OS and see if updating causes it to break again. I haven't fully "moved" onto this one since having it have issues out of the box made me not trust it so I will just continue not trusting it. *sad face* But it makes doing a fresh install very, very easy.

I am just not sure if  it happens again if I should go back to Dell Support since my machine is under warranty or keep trying to figure it out. I've been using a 2008 Macbook so I was pretty excited to get something new and I accepted that getting a dedicated linux machine would mean having to refresh what I've long since forgotten and learn new stuff but I was not anticipating having a machine that isn't reliable. *whine*

---

### Post by oldfred on 2020-06-24
These are from my notes on Dell's required settings. Then the normal install requirements also apply.

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

