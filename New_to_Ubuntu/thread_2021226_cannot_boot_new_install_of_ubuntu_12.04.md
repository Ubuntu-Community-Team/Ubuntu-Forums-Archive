---
title: "cannot boot new install of ubuntu 12.04"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by cyphoyd on 2012-07-08
So I've dabbled with some success with Linux over the years but I'm still a newb. I got Ubuntu 12.04 desktop on a boot disktop and installed it in ever configuration I could dream of and can't get it to boot. I've allowed the installer to configure the partitions and hand selected the partitions. I've used the efi partition and installed without it and tried putting the boot loader on sda1 and on a totally sepporate partition(not the efi partition). Nothing works. Grub2 does make any attempt to load. The BIOS recognised the hdd and I can select that hdd to boot off of but it skips over it and continues the boot order until it gets to loading from the network... I've used boot-repair to no avial. Anyone have any ideas for me?

---

### Post by drs305 on 2012-07-08
cyphoyd,

Welcome to the Ubuntu Forums. :-)

Please use the Boot Repair tool to run the info script and post the link. If we can inspect the information we may be able to determine what has gone wrong.

---

### Post by cyphoyd on 2012-07-08
[HTTP://paste.Ubuntu.com/1082172/](HTTP://paste.Ubuntu.com/1082172/)

Keep in mind this is my last ditch effort to trying everything. I'm pretty sure the partitions are excessive and unnecessary but it was worth a try. if you can pick anything out I'd appreciate any feedback.

---

### Post by drs305 on 2012-07-08
Unfortunately I haven't dealt with EFI partitions enough to know what breaks or fixes them. We have some very knowledgeable folks that frequent the forums who do know about these things but they don't appear to be online at the moment.

About all I can do is edit the thread title for you and add "EFI", which might attract those who can help.

---

### Post by cyphoyd on 2012-07-09
An update, looking at the boot-repair info it pulled up, I have no bootloader in the MBR, even after several attempts I can't. Also when I do load grub 2(I have to open it in terminal on the liveCD test load that comes with 12.04) which I'm relatively unfamiliar with, from what I've seen it should automatically locate OS's on the computer. All it does is go to a limited command prompt.

---

### Post by cyphoyd on 2012-07-09
One more update checked the boot order and all in efibootmgr and excluded all options but Ubuntu and cd-rom and it still tried booting off the network meaning my computer is booting and grub is not even being utilized. Plz someone help me lol my head is spinning...

---

### Post by idoitprone on 2012-07-10
[http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)

```
sudo mount /dev/sda2 /mnt #sda2 is my root partition
 sudo mount /dev/sda1 /mnt/boot/efi #sda1 is my efi partition
 for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
 sudo cp /etc/resolv.conf /mnt/etc/ #makes the network available after chrooting
 sudo chroot /mnt apt-get install --reinstall grub-efi
sudo update-grub

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
 sudo umount /mnt/boot/efi #please do this. corrupted efi partitions are not nice
 sudo umount /mnt
sudo reboot
```i never repaired efi before i hope this helps


oh wayyy dose this abomination called uefi...

---

### Post by YannBuntu on 2012-07-10
Hello

> **cyphoyd said:**
> [HTTP://paste.Ubuntu.com/1082172/](HTTP://paste.Ubuntu.com/1082172/)

As we can see here:
```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi
```

, your grub-efi is correctly installed.

And this shows that your BIOS booted on your live-CD in UEFI-mode:

```
=================== dmesg | grep EFI :
[    0.000000] EFI v2.00 by Phoenix Technologies Ltd.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x0000000000054000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000054000-0x0000000000055000) (0MB)
```

Now, all you need is setup your BIOS to boot on the sda1/efi/ubuntu/grubx64.efi file.
Please show pictures of your BIOS if you don't know how to do it.

---

### Post by oldfred on 2012-07-10
+1 on Yann's suggestions.

How did you partition? Did you use Ubuntu installer or gparted?

Gparted automatically starts partitions at 2048 for compatibility with the new 4K drives which your is.
> Sector size (logical/physical): 512 bytes / [COLOR=Red]4096[/COLOR] bytes > 
 Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           [COLOR=Red]   34[/COLOR]       195,346       195,313 EFI System partition
/dev/sda2         195,347    78,320,347    78,125,001 Data partition (Windows/Linux)
/dev/sda3      78,320,348 1,455,273,473 1,376,953,126 Data partition (Windows/Linux)
/dev/sda4   1,455,273,474 1,465,148,474     9,875,001 Swap partition (Linux)


srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by cyphoyd on 2012-07-10
I have built the partitions in both Gparted and ubuntu's installer, however I'll give it another run with everything I've picked up but first one question. My bios doesn't have any way to point to the efi file. It only allows thee selection of boot order and thats it. I'll try to get pictures but I see nothing useful in my bios.

---

### Post by cyphoyd on 2012-07-10
bios snapshots are attached

---

### Post by oldfred on 2012-07-10
I thought the Secure Core Tiano was an efi boot loader, but none of your screens mention UEFI.

Then I thought if you boot with BIOS the USB installer presents you with a BIOS install. Only if you boot with UEFI do you get the choice of BIOS or UEFI type installs.

I would create both a efi partition and a bios_grub partition. 

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

If you may want to install Windows on this drive, you cannot use gpt partitioning unless you can boot in UEFI mode. Windows only works in BIOS mode with MBR partitioned drives. But if only Linux then use gpt.

---

### Post by cyphoyd on 2012-07-10
I'll give that a try and see what I get. The thing that makes this even more confusing is I noticed all my changes done in efibootmgr show but once I reboot and it fails again i bring it up in my liveCD and ots reverted back to the default settings. I also did a bunch of research on the bios, it is SUPPOSED to be a UEFI bios I've seen a lot of mention of issues getting it to work but maybe their wrong... Either way, I've done just about everything at one point or another, maybe the installer/I am assuming its a UEFI bios when it really isn't... I stopped working with linux os's years ago but it was easier back then, kinda strange... guess thats what happens in the constantly evolving world of computing. I'll let you know how it goes....

---

### Post by cyphoyd on 2012-07-10
Here's a question on this partition thing. I've seeing the best way to set it up is to have a boot partition, a root partition, a home partition and a swap partition. I also read that the boot partition is sepporate from the efi partition. does this mean that to boot with the uefi bios I'd do efi,root,home,swap or efi,boot,root,home,swap? Do I need the boot partition if it IS an UEFI bios? If not, would I use the boot partition to see if I can boot with or without efi? does that even make sense....

---

### Post by YannBuntu on 2012-07-12
Hello
On [this screen]("http://ubuntuforums.org/attachment.php?attachmentid=221016&d=1341942988") we see:
```
SATA controller working mode: AHCI
```

Please tell us which other modes are proposed.

---

### Post by cyphoyd on 2012-07-12
Iae is the other option

---

### Post by oldfred on 2012-07-12
Most desktops do not need a separate /boot whether BIOS or UEFI.

 Servers with RAID or LVM may and some older BIOS only boot from the first 137GB of a drive and need either a separate /boot or / (root) fully inside the first 137GB. 
We are also finding some systems (I still think it is a BIOS setting, perhaps emulating old setting for compatibility) that will not boot from either very large / partitions or beyond some point. I normally suggest a 25GB (or smaller if drive is limited) and that will work without the separate /boot.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

IF in BIOS mode you install the grub2 boot loader to the MBR or sda, If in UEFI mode the grub2 (efi) boot loader goes into the efi partition.

---

### Post by YannBuntu on 2012-07-12
> **cyphoyd said:**
> Iae is the other option

This may be a way to disable EFI-boot.

Let's check it:
1) Setup this BIOS option to "Iae"
2) Reboot your PC, try to boot on a Ubuntu live-CD or live-USB. 
   - If you can't, reboot and revert the BIOS options to AHCI.
   - If you can boot, choose "Try Ubuntu", open a terminal "Ctrl+Alt+C", and indicate the output of the following command:
```
dmesg | grep -i efi
```

---

