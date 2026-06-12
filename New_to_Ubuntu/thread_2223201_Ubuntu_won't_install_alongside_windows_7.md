---
title: "Ubuntu won't install alongside windows 7"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by Blakeo on 2014-05-09
Ubuntu won't give me the option to install alongside a working windows install? 
Can anyone help me and give me some suggestions why it won't work. 
Thank you.

---

### Post by grier-devon on 2014-05-10
Weird, maybe try using gparted and shrink the Windows partition. It should work but if not make room for Ubuntu manually then go through the install.

---

### Post by sammiev on 2014-05-10
How many partitions do you have? Maybe check with Windows or GParted and post the screen shot here.

---

### Post by Blakeo on 2014-05-10
> **sammiev said:**
> How many partitions do you have? Maybe check with Windows or GParted and post the screen shot here.
There are 3 partitions, one system health partition of 100mb, a windows partition which is 458gb and unallocated which is 451gb
> **grier-devon said:**
> Weird, maybe try using gparted and shrink the Windows partition. It should work but if not make room for Ubuntu manually then go through the install.
Thanks for the reply, I have already done this through windows disk management. 

Thanks guys, and other suggestions?

---

### Post by LastDino on 2014-05-10
You need to break that unallocated area into few more partitions by selecting ''something else'' while installing Ubuntu through Gpart which will appear automatically. (Not through Windows partition manager)

Those partitions are
/   = root made up of about 20 GB. This needs to be formatted into ext4.
SWAP = In equal size as your RAM. This will be dealt by gparted automatically as soon as you make it and select SWAP.

That is minimum and you can add few more as you need, like;
/home = anything above 30 GB (Would be good to keep it around 100 GB). This needs to be formatted in ext4 as well.
Format rest into NTFS storage area by making it separate logical partition. I say NTFS because then you can access it from both windows and linux. Windows can't read ext4.

---

### Post by Blakeo on 2014-05-10
> **LastDino said:**
> You need to break that unallocated area into few more partitions by selecting ''something else'' while installing Ubuntu through Gpart which will appear automatically. (Not through Windows partition manager)

Those partitions are
/   = root made up of about 20 GB. This needs to be formatted into ext4.
SWAP = In equal size as your RAM. This will be dealt by gparted automatically as soon as you make it and select SWAP.

That is minimum and you can add few more as you need, like;
/home = anything above 30 GB (Would be good to keep it around 100 GB). This needs to be formatted in ext4 as well.
Format rest into NTFS storage area by making it separate logical partition. I say NTFS because then you can access it from both windows and linux. Windows can't read ext4.

Am I able to change the swap at a later date as I plan to upgrade to 16gb of ram from my current 8gb when it arrives in the post. 
I want to fix the underlying issue when the installer won't detect windows as well though.

---

### Post by veddox on 2014-05-10
Yes, you can change swap any time - see this [tutorial]("https://help.ubuntu.com/community/SwapFaq") for a howto. 

I suspect your installer didn't offer you the option of installing alongside Windows because the rest of your hard drive was unpartitioned space. Try creating an ext4 root partition (along with all the others that LastDino suggested) while running Ubuntu from a live CD. Then try the installer again.

---

### Post by LastDino on 2014-05-10
Looking at your RAM amount, I'm curious. Is your system new? Is it UEFI or Legacy? Please check that before doing anything and which Windows is already installed anyway?

If it is UEFI, you need to do few more things.

Btw, with 16GB RAM, I might forget about making SWAP all together.

---

### Post by Blakeo on 2014-05-10
> **LastDino said:**
> Looking at your RAM amount, I'm curious. Is your system new? Is it UEFI or Legacy? Please check that before doing anything and which Windows is already installed anyway?

If it is UEFI, you need to do few more things.

Btw, with 16GB RAM, I might forget about making SWAP all together.

My computer is 2 months old, pretty much brand new so I'm guessing it's not that legacy one. What do I have to do with the UEFI? I'll do some google searching on this. 
Thanks again.

---

### Post by LastDino on 2014-05-10
> **blake8 said:**
> My computer is 2 months old, pretty much brand new so I'm guessing it's not that legacy one. What do I have to do with the UEFI? I'll do some google searching on this. 
Thanks again.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You can start from reading there, this is just the start though. You can search this forum for similar topic, I'm sure there are dozens of threads addressing the very same thing.

---

### Post by sammiev on 2014-05-10
Two months old is likely UEFI. You want to be-sure before you do anything and have a full backup of your system.

---

### Post by oldfred on 2014-05-10
If new systems with Windows 8 pre-installed it definitely is UEFI. Title says Windows 7?

Then Windows not seen is often Windows fast boot is still on, or you have not rebooted after resize & it needs to run chkdsk.
If an Ultrabook you also have additional issues. See link in my signature.

What model computer? And what video chip/chips?

From live installer terminal post this:

sudo parted -l

---

### Post by Blakeo on 2014-05-11
> **oldfred said:**
> If new systems with Windows 8 pre-installed it definitely is UEFI. Title says Windows 7?

Then Windows not seen is often Windows fast boot is still on, or you have not rebooted after resize & it needs to run chkdsk.
If an Ultrabook you also have additional issues. See link in my signature.

What model computer? And what video chip/chips?

From live installer terminal post this:

sudo parted -l
I will do the sudo parted -l when I'm back at my computer, however my computer has been custom built by myself. 
My video card is a: Asus Radeon R9 280x

---

### Post by LastDino on 2014-05-11
> **blake8 said:**
> I will do the sudo parted -l when I'm back at my computer, however my computer has been custom built by myself. 
My video card is a: Asus Radeon R9 280x

Then it should be mentioned on your Mobo box too. ;)

---

### Post by Blakeo on 2014-05-13
> **LastDino said:**
> Then it should be mentioned on your Mobo box too. ;)
Yeah dam it is UFEI, does anyone know how to disable secure boot on a [COLOR=#4D4D4D][FONT=helvetica]GIGABYTE 3D BIOS?

What I want to do is in the Ubuntu installer to select the option Install alongside Windows 7, but it does not detect any other operating systems and thus does not give me this option.
How do I make ubuntu detect my other operating system?[/FONT][/COLOR]

---

### Post by oldfred on 2014-05-13
Is system hibernated? Or have you resized Windows and not rebooted so it needs chkdsk.
Often better just to have Windows on one drive and Ubuntu on another drive.

       Boot Issues from live Installer not showing partitions
Do you have Windows hibernated?  Or Windows 8 fastboot still on
Does NTFS need chkdsk? Even if it boots ok?
Was drive every part of RAID or RAID set in BIOS? or Intel SRT which uses RAID
SFS, Windows dynamic partitions or LDM on gpt drives
 backup GPT table is not at the end of the disk
Left over gpt data Windows leaves backup gpt data when converting to MBR.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Blakeo on 2014-05-14
> **oldfred said:**
> Is system hibernated? Or have you resized Windows and not rebooted so it needs chkdsk.
Often better just to have Windows on one drive and Ubuntu on another drive.

       Boot Issues from live Installer not showing partitions
Do you have Windows hibernated?  Or Windows 8 fastboot still on
Does NTFS need chkdsk? Even if it boots ok?
Was drive every part of RAID or RAID set in BIOS? or Intel SRT which uses RAID
SFS, Windows dynamic partitions or LDM on gpt drives
 backup GPT table is not at the end of the disk
Left over gpt data Windows leaves backup gpt data when converting to MBR.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

I dont understand what you mean by hibernation. The machine is not in hibernation in windows or Ubuntu, no secure boot is enabled or any of that sort. Ubuntu installer still does not detect windows. I have ran FixParts.

---

### Post by oldfred on 2014-05-14
Then it must be one of the other issues. Post this, but it may not show which problem you have.

sudo parted -l

---

### Post by Blakeo on 2014-05-15
[img]http://i.imgur.com/ZrAYqZF.jpg[/img] 
There's what I can boot up with, if I use UEFI it won't boot. So I use legacy, it boots.

---

### Post by oldfred on 2014-05-15
Please change screen shot to an attachment. You can use advanced editor, and attach with the paperclip icon in the edit panel at the top.

What happened to?
sudo parted -l

---

### Post by Blakeo on 2014-05-18
> **oldfred said:**
> Please change screen shot to an attachment. You can use advanced editor, and attach with the paperclip icon in the edit panel at the top.

What happened to?
sudo parted -l

Sorry about the slow reply, been busy with work.
[HTML]sudo parted -l 
Model: ATA WDC WD10EALX-009 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  106MB  105MB  fat32        EFI system partition          boot
 2      106MB   240MB  134MB               Microsoft reserved partition  msftres
 3      240MB   517GB  517GB  ntfs         Basic data partition          msftdata


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 8024MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      5353kB  8024MB  8018MB  primary  fat32        boot, lba


[/HTML]

Also @Fred, I am running Windows 7.

---

### Post by oldfred on 2014-05-18
That looks like a UEFI install as a BIOS install of Windows has a 100MB boot partition and the main install and both partitions are NTFS. 
Windows only boots from gpt with UEFI.

You should boot Ubuntu from flash drive with UEFI Toshiba entry as the other one would be BIOS boot.
But you say is will not boot? Do you get any error messages.
You can install in BIOS boot mode and use Boot-Repair to convert to UEFI, but better to install directly in UEFI mode. 

Do not know if it applies to your model or not, others have posted these:
 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.


Is Windows hibernated? 
Or does it need chkdsk? Which after any resize it needs. Did you reboot after resize so it can run the chkdsk?

I would suggest using only Something Else, but then you have to choose your partitions. 

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

