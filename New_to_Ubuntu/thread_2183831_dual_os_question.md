---
title: "dual os question"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by stockpimp on 2013-10-26
I have recently built a new desktop and installed a 1TB HD which I have installed Ubuntu on and partitioned with some space left for a windows install.  are there any good how-to's out there for a configuration such as this?  I found one but it was a "install windows first" senario.  Thank-you.

---

### Post by oldfred on 2013-10-26
Is system UEFI or BIOS?
Did you install Ubuntu in UEFI or BIOS mode.
You need to install Windows in the same boot mode, but with UEFI Windows needs several partitions on gpt partitioned drives and specific order on drives.

---

### Post by stockpimp on 2013-10-26
I just "installed".... not sure which mode but if i had to guess I would would say BIOS.  I downloaded the os burnt to disc booted new cpu entered asus management center (BIOS I'm guessing) changed the boot order to dvd drive and ran the insatll from that drive.  Obviously I have since changed the boot order to the hard drive but you get the idea.  During the install i set up 3 partions i believe (as recomended by Ubuntu as set up proceeded).  One of which is a blank partion which i want to install windows in.

---

### Post by oldfred on 2013-10-26
Post this from terminal:

       sudo parted /dev/sda unit s print

If BIOS and MBR, then Windows requires a NTFS formatted primary partition (sda1 thru sda4) with the boot flag. Some have had issues if primary partition is after the extended partition.

Windows will install its boot loader so be prepared to reinstall grub2's boot loader with Live flash drive or DVD.

Some have had issues with Windows corrupting partition table. 
You can back up partition table, but if you make any changes then backup will not work to restore a missing partition.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by stockpimp on 2013-10-26
not sure what this tells you?


Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End          Size        File system     Name  Flags
 2      2048s       71679s       69632s      fat32                 boot
 3      71680s      169983s      98304s      linux-swap(v1)
 1      976963584s  1953523711s  976560128s  ext4

---

### Post by oldfred on 2013-10-26
Because it is gpt and you have a FAT32 partition with boot flag, you are booting with UEFI.
You have to install Windows in UEFI mode as it only boots from gpt partitioned drives with UEFI.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

You will have to use flash drive and depending on version may have to modify it to work with UEFI. How you boot install media from UEFI menu is how it installs. I do not know any details on Installing Windows in UEFI mode.


 Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

      
 [http://www.eightforums.com/](http://www.eightforums.com/)
Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

