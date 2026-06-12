---
title: "Partition Advice - 1 TB Seagate External HD"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by gatoruss on 2013-03-18
I tried Ubuntu a few years back on an old desk top, could never get
wifi to work, and gave up. Ready to give linux another try.

I have a Dell XPS laptop - it is a i7 dual core 64 bit, with 8 GB RAM
and a 750 GB internal HD (with about 400 GB free space), and currently
runs W7.

I have tried 12.10 as a full install on a 16 GB USB flash drive and
via Virtual Machine, and didn't care for the performance. I do not
want to dual boot.  So, I thought I would install on a 1 TB Seagate
External USB (3.0) HD (on which nothing is installed) that I picked up on sale at Costco.

It seems like 1 TB is a bunch of space and I am seeking advice on how to
best partition the drive. Given the size of the external HD, I think
that I should allocate some space for shared data, root, swap and home
- with the largest allocation to the shared space (that way it can be accessed by linux and W7). Does that sound
right?  Does the following allocation seem wise:

• Shared Space (/windows) -> 900 GB
• root (/) -> 25-30GB
• swap -> 16 GB
• home (/home) -> 50 GB

Also, what file systems should I use?

Thanks!

---

### Post by oldfred on 2013-03-18
My standard recommendation is not far from what you want. Would you ever want another 25GB to just test other installs or version. When I got my new 650GB drive 3 years ago I created pretty large for me 100GB NTFS data partition, same size ext4 data partition and 25 GB for Ubuntu's / (root) and left the rest unallocated as I was not sure what I wanted. I now have too many 25GB partitions with old, obsolete, testing and duplicate installs to experiment with something. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Unless you are hibernating you do not need the huge swap. If you have 8GB of RAM you will never use swap.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I now use gpt for all new drives and allocate space for efi & bios-grub. Efi is for future as my system is BIOS, but it becomes difficult to add an efi partition at start of drive once it has lots of data.
       GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by patrickcage on 2013-03-18
Personally I only use 2GB of Swap to allow hibernating.

---

### Post by gatoruss on 2013-03-18
I have been reading thru the links regarding how windows boots - UEFI/gpt or BIOS/MBR?  My system is a Dell XPS L502X.  When it powers up, and I enter Set Up ("hit F1"), the heading on the "bios" screen reads "Phoenix SecureCore Tiano Setup."  A google search of "Phoenix SecureCore Tiano Setup" suggests it is UEFI.  But I cannot seem to figure out if it is booting in UEFI mode or legacy mode?  Some the message board posts I have come across suggest that it is not configurable?  Where to I go from here as far as GPT and MBR is concerned?

Thanks.

---

### Post by gatoruss on 2013-03-19
It seems that the BIOS in the Dell L502x is UEFI, but is not configurable:

[LIST]
[*][http://en.community.dell.com/support-forums/laptop/f/3518/p/19473013/20215088.aspx]("http://en.community.dell.com/support-forums/laptop/f/3518/p/19473013/20215088.aspx")

[*][http://en.community.dell.com/support-forums/software-os/f/4677/t/19473166.aspx](http://en.community.dell.com/support-forums/software-os/f/4677/t/19473166.aspx)
[/LIST]

I assume that this means that my version of W7 is "UEFI in legacy mode" and, therefore, that I have the option of booting from the external drive if that drive is GPT and has a  BIOS-Boot partition?

That being the case and given oldfred's comments with respect to allocation if the external HD is GPT, does the following seem logical:

[LIST]
[*]250 MB -> EFI (for future use) -- FAT32 : Not sure where to locate this?
[*]1 MB ->  BIOS-Boot partition - I assume that my system is UEFI in legacy mode, and that my W7 can boot off a GPT external drive.  However, I am not sure where to locate this - the disk guide that oldfred links in post #2 states that "...[i]t must be located at the start of a GPT disk."  But guide also says that the EFI boot partition referenced above (for future use) should be at the beginning and, in threads concerning setting up a flash USB with a full install, I have read that the shared partition (referenced below) needs to be at the beginning of the drive? 
[*]700 GB -> /media/mysharedstuff (for shared data) -- NTSF
[*]50 GB -> / (root) -- ext4
[*]50 GB -> /home (/home) -- ext4
[*]16 GB -> swap
[*]balance of the disk unallocated (for future experiments test of other distros or upgrades)
[*]
[/LIST]

Thanks in advance for assistance.

---

### Post by oldfred on 2013-03-19
The efi partition should be first or at least near start of drive. The bios_grub can be anywhere  on drive, but I usually make it second. UEFI specification says the efi partition should be first, but Windows suggests its repair partition be first and efi second. Some vendors even add another. I have seen one user with efi fairly far into a drive, but wonder if UEFI spec want it first as its driver cannot read beyond some point on drive. 

The advice on NTFS first may be for USB flash drives as older Windows only reads the first partition of flash drives. I do not think (but not 100% sure) that it is the same for hard drives.

If you have both efi & bios_grub only one will be actually used and it will depend on how you boot. 

Your UEFI/BIOS may not be upgradeable to secure boot (a good thing) but it probably is UEFI with BIOS CSM mode. 
        UEFI Compatibility Support Module (CSM)

There are only several UEFI/BIOS vendors and tianocore is an open source one. I think it is supported by Intel.
But each vendor customizes for its hardware. 
[https://gitorious.org/tianocore_uefi_duet_builds](https://gitorious.org/tianocore_uefi_duet_builds)

---

### Post by gatoruss on 2013-03-19
Thanks, Fred.

I apologize for being obtuse, but I am out of my depth here and I want to make sure that I understand this correctly...thanks for your patience.

[LIST]
[*]Since my Bios appears to be UEFI with BIOS CMS mode, that means my W7 should be able to boot in GPT and that I will boot off of the bios_grub partition, correct?

[*]And the bios_grub partition is the same as the BIOS-Boot partition, correct?

[*]The guide that you linked - [https://help.ubuntu.com/community/DiskSpace]("https://help.ubuntu.com/community/DiskSpace") - indicates that the EFI partition should be approx 250 MB and mounted at /boot/efi, but that there is no need to create it as the installer will do.  So, when I am setting up my partitions prior to installation, The first partition I create is a 250 MB FAT32 partition with no mount point?  Since my w7 is in CMS mode, this partition will not be used at this point, correct?

[*]For the bios_grub partition, the second partition I create is a 1MB partition (after the EFI partition) that has no mount point or file system.  This is where my current comfiguration will boot.

[*]Then the NTFS shared partition with "/windows/sharedstuff" as the mount point.

[*]Then root (/) and home (/home) as ext4

[*]And finally swap.

[*]That will leave me approx 100GB of unallocated space.
[/LIST]

Do I have this correct?

Thanks again!

---

### Post by oldfred on 2013-03-19
Windows will not boot from an external drive, so that does not matter.

Windows does not see Linux partitions but newer versions of Windows (not XP) will read NTFS partitions in a gpt partitioned drive.

I would not change your Windows on your internal drive. And if dual booting you should install Ubuntu in the same mode. UEFI writes system data for Windows or Ubuntu to use differently than does BIOS, so you have to totally hard reboot, change UEFI from UEFI to BIOS or vice-versa and reboot to change if both are not in same mode.

I do not know what a BIOS-boot partition is. With partition tools you can set the bios_grub flag on a 1MB unformatted partition.
Some systems have BIOS that will not boot past a certain point or servers often use a /boot partition for grub and the kernels.  Most desktop installs do not need the /boot.

System still boots from /boot folder. But grub needs ton put its embedded core.img somewhere.
 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "bios_grub partition" to hold core.img. The bios_grub Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

---

### Post by gatoruss on 2013-03-19
> **oldfred said:**
> I do not know what a BIOS-boot partition is.

"BIOS-boot partition" is the terminology used in the linked guide ([https://help.ubuntu.com/community/DiskSpace]("https://help.ubuntu.com/community/DiskSpace")):

[INDENT]> If you want to install Ubuntu on a GPT disk (you can check it via the 'sudo parted -l' command), you will need either an EFI partition (if your BIOS is setup in EFI mode) or a BIOS-Boot partition (if your BIOS is setup in Legacy mode).[/INDENT]

I think I understand better... I think :-)  Since I have my w7 on the internal hard drive, it never boots off of the external drive. *But since my bios is UEFI in CMS mode, if I want to have GBT partitions on the external drive, the external drive needs to have *a boot_grub partition so that linux can boot off the external drive. *The EFI partition on the external drive is just in case I some day change my w7 install or bios setting where UEFI is enabled -in that case, to boot Linux on the external drive, grub will use the EFI boot partition. *Am I understanding that better?

> **oldfred said:**
> System still boots from /boot folder. But grub needs ton put its embedded core.img somewhere.
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "bios_grub partition" to hold core.img. The bios_grub Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

I am curious, can I/should I add a /boot partition, and if I do will I still need a " bios_grub partition"?

Thanks for your patience!

---

### Post by oldfred on 2013-03-19
Yes, the efi partition is just to allocate space now, in case later you convert. It is not really large and would make it easier in the future as then it would be hard to add an efi partition at or near beginning of drive.

Bios_grub partition is unformatted space just for grub2's core.img. It is totally separate from a /boot partition which has to be formatted with Linux format usually ext2 as ext4's journal does not add much for a small 250 to 400MB /boot partition.

 Some BIOS have issues with booting beyond 100GB on a drive. It was an issue years ago (IDE 137GB issue), grub did have a bug on / (root) partitions over 500GB which supposedly was fixed. But we see some systems where the boot still does not work. It seems to only be a few and may be just BIOS settings, but we have never seen a solution other than a small / or separate /boot fully inside the first 100GB. If you have the issue, it will be right away, but check before copying lots of data into NTFS partition. NTFS partitions can be a bit more difficult to move.

---

### Post by gatoruss on 2013-03-19
Thank you.  I appreciate your time.  I hope to do the install tonight.

BTW, I have been playing around some with an install of 12.10 on a 16 GB USB flash drive.  The performance isn't as bad I initially thought - this morning was able to install the Citrix Receiver on the flash drive and log into my work network.  That could be handy if i am away from home (travelling) and don't have my laptop.   Anyhow, I am hoping that the external USB hard drive will be an improvement as far as speed and performance...I am excited to find out.  Do you know offhand if 12.10 is compatable with USB 3.0?

---

### Post by oldfred on 2013-03-19
I have 12.04 full install in 8GB on my 16GB flash drive with another 8GB for data. While not speedy it is functional. Did you make the changes like an SSD to reduce writes as that slows down everything. With a fair amount of RAM once an app has loaded it is just as fast as a hard drive as Linux is good about cacheing everything into RAM.

There used to be some issues with USB3, but I think that was the BIOS not anything else. I just bought a 32GB USB3 flash, but only have USB2 ports and want to see if I can tell any difference. Supposedly the flash drive itself is better.

---

### Post by gatoruss on 2013-03-20
> **oldfred said:**
> Did you make the ***_changes like an SSD_*** to reduce writes as that slows down everything.

Can you elaborate?  I do not follow what you are suggesting.

---

### Post by oldfred on 2013-03-20
Flash drives do not support trim, but all the other settings are similar. I believe I did these on both my flash & SSD.

 With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

I have seen some newer info on scheduler but did not save that info. But the default one is really for rotating hard drives. I did not use swap on flash drive as I have 4GB of RAM and never see swap used the way I normally work. With flash drive I do not try to load lots of programs at once, just in case.

---

