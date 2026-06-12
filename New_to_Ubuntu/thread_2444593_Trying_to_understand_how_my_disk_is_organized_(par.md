---
title: "Trying to understand how my disk is organized (partitions)"
date: 2020-06-01
forum: New to Ubuntu
---

### Post by valdemarv on 2020-06-01
Hello, I'm new to Ubuntu user, so apologies if I'm asking too simple things. 

I recently installed Ubuntu on an old Dell laptop over Win7, choosing during installation that only Ubuntu should be on the computer (Win erased). I have one 256 GB SSD hard drive, no other disks (at least that's what I believe). 

When I explore the disk with Disks, I can see an "image" of the disk under heading "Volumes". On the left side of that image, it says "File system - Partition 1 - 537 MB FAT". On its right side there is longer bar with two parts. The two parts are jointly equally high as is the leftmost part (Partition 1). The upper part reads "Extended partition - Partition 2 - 256 GB", and the lower "Filesystem - Partition 5 - 256 GB Ext4".
The partition type of these 3 entities are (in the same order): WP95 FAT 32 (Bootable) / Extended / Linux.

Could somebody help me understand the following:

1) Are there really 3 partitions on my single hard drive?
2) If so, is it normal for an Ubuntu system to have these 3 partitions, or are these some remnants of my previous setup (Win 7)?
3) Why are partitions 2 and 5 displayed on top of each other, and why is their total size (sum of the two) actually twice the size of my hard drive?
4) Why on earth are the partitions numbered like that: 1, 2, 5? (Where are 3 and 4?)
5) Can any of the above mean that there is still something from Dell or Win 7 lurking on the disk? I wouldn't want that.

---

### Post by GhX6GZMB on 2020-06-01
Open a Terminal (Ctrl+Alt+T) and type:

sudo lsblk
sudo blkid

and let let us know the results.

---

### Post by CatKiller on 2020-06-01
> **valdemarv said:**
> 3) Why are partitions 2 and 5 displayed on top of each other, and why is their total size (sum of the two) actually twice the size of my hard drive?
4) Why on earth are the partitions numbered like that: 1, 2, 5? (Where are 3 and 4?)

[https://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition](https://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition)

One is inside the other.

You can only have 4 partitions with MBR partitions. If you make one of those (2, in this case) an Extended Partition you can put several logical partitions (just the one - number 5 - in this case) inside it.

---

### Post by valdemarv on 2020-06-01
Hello @ml9104, here are the responses. I wasn't sure if some of the ids are meant to be kept confidential, so replaced them with SOMECODE.

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT

 loop0    7:0    0  93,9M  1 loop /snap/core/9066
 loop1    7:1    0 240,8M  1 loop /snap/gnome-3-34-1804/24
 loop2    7:2    0   9,1M  1 loop /snap/canonical-livepatch/95
 loop3    7:3    0  62,1M  1 loop /snap/gtk-common-themes/1506
 loop4    7:4    0    55M  1 loop /snap/core18/1705
 loop5    7:5    0  27,1M  1 loop /snap/snapd/7264
 loop6    7:6    0  49,8M  1 loop /snap/snap-store/433
 loop7    7:7    0    55M  1 loop /snap/core18/1754
 loop8    7:8    0  49,8M  1 loop /snap/snap-store/454
 loop9    7:9    0 255,6M  1 loop /snap/gnome-3-34-1804/33
 sda      8:0    0 238,5G  0 disk  
 &#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
 &#9500;&#9472;sda2   8:2    0     1K  0 part  
 &#9492;&#9472;sda5   8:5    0   238G  0 part /
```
 
 
```
 /dev/sda5: UUID="SOMECODE" TYPE="ext4" PARTUUID="SOMECODE"
 /dev/loop0: TYPE="squashfs"
 /dev/loop1: TYPE="squashfs"
 /dev/loop2: TYPE="squashfs"
 /dev/loop3: TYPE="squashfs"
 /dev/loop4: TYPE="squashfs"
 /dev/loop5: TYPE="squashfs"
 /dev/loop6: TYPE="squashfs"
 /dev/loop7: TYPE="squashfs"
 /dev/sda1: UUID="SOMECODE" TYPE="vfat" PARTUUID="SOMECODE"
 /dev/loop8: TYPE="squashfs"
 /dev/loop9: TYPE="squashfs"
```

---

### Post by valdemarv on 2020-06-01
@CatKiller, so the partition 5 is inside 2? Is the numbering because 3 and 4 are reserved for the potential third and fourth primary partitions or is there some other reason for it? I'm curious to know because I've seen some discussion where people are wondering about their Dell partitions and it seems to be that Dell has included some service or recovery partitions in their systems. Hence I was wondering why the numbers are like this after a "clean Ubuntu" install (i.e. Win was not supposed to be kept alongside Ubuntu).

---

### Post by valdemarv on 2020-06-01
And allow please one more question: which of these is the actual boot partition for Ubuntu, nr 1?

---

### Post by GhX6GZMB on 2020-06-01
First, don't worry about posting the UUIDs. They are internal to your machine and useless for anyone else.

Second, your installation was unsuccessful. You have remnants of old stuff, and the partitioning is no good.

You need to do a new install and _format_ and partition your HDD correctly. For a 100% Ubuntu install, the file system should be ext4.

How you want to partition your HDD is up to you, a single partition is also fine. I attach an example from my own laptop:

```

macro@macro-pc:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  

macro@macro-pc:~$ blkid
/dev/sda1: UUID="269ffc34-0c2a-4ef4-b794-85019d562e0d" TYPE="ext4" PARTUUID="7e408a68-01"
/dev/sda2: UUID="aac2fbd9-4194-436b-b8ae-65262e102311" TYPE="ext4" PARTUUID="7e408a68-02"
/dev/sda3: UUID="22928e29-fe9a-45ee-b043-666fd6520d7c" TYPE="swap" PARTUUID="7e408a68-03"
macro@macro-pc:~$ 


```

---

### Post by yancek on 2020-06-01
Question 1: Yes
Question 2: (first part of the question)No but it is an option. (2nd part of the question)It could be.  Not enough information to tell
Question 3: Explained in post above,  partition 2 is a Primary partition used as an Extended partition and can not contain data.  You can as pointed out above, create logical partitions within the Extended partition which can contain data.  The first logical partition is always partition 5. You can create any number of logical partitions, depends mostly on the size of your drive. 
Question 4:  Answered above.
Question 5:  Yes it can but I don't see how it could be a problem unless you need that 500MB for data.  It might be that partition one was used with windows for an EFI install which can be determined by mounting sda1 and taking a look at it to see what it contains.

---

### Post by TheFu on 2020-06-01
This command makes more useful output:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

After the install, you can create an alias so less typing is needed.

```
sudo fdisk -l 
```
is the other command to see disk layouts.

All the "loop" stuff is useless for almost every command. All it does is take away from what you or we really care to see.

i cannot say that the install didn't work.  
[LIST]
[*]/boot/efi has to be FAT32. That is for EFi support and part of the standard. 500MB is a reasonable size for that.  
[*]/ as ext4 is 100% fine too.  I’d want it to be 25GB and use the rest of the storage for other locations, but using all the disk this way is what the default installer does.
[/LIST]

Here's my 20.04 Mate desktop layout:
```
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     12G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home

```
i use a virtual machine and only gave it 30GB total storage.
Here's another view:
```
$ df -Th
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   12G   11G  427M  97% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.2G  5.0G  56% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```
i deleted the loop stuff.

---

### Post by valdemarv on 2020-06-02
Thanks a lot for all your comments! I believe I understand a bit more now. But @ml9104's comment about an unsuccessful installation got me a bit more confused and worried. 
This was indeed the default Ubuntu 20.04 LTS installation. I just allowed Win to be removed during the installation. I enclose below the response to the lsblk command, suggested by @TheFu and the further information by Disks.  

```
lsblk -e 7 -o name,size,type,fstype,mountpoint

NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda    238,5G disk        
&#9500;&#9472;sda1   512M part vfat   /boot/efi
&#9500;&#9472;sda2     1K part        
&#9492;&#9472;sda5   238G part ext4   /

DISKS:

Partition 1
Size        537 MB (0.2% full)
Device        /dev/sda1
Partition type    W95 FAT32 (Bootable)
Contents    FAT (32-bit version) - Mounted at /boot/efi
  
Partition 2
Size        256 GB
Device        /dev/sda2
Partition type    Extended
Contents    Extended partition

Partition 5
Size        256 GB (5.6% full)
Device        /dev/sda5
Partition type    Linux
Contents    Ext4 (version 1.0) - Mounted at Filesystem Root


```If I understand correctly from the above, partition 1 is indeed an EFI system partition, partition 2 doesn't really contain anything. Instead, it is the basis for Partition  5, which in turn is the location of Linux/Ubuntu and all my data. If that is correct, allow me to place the following new questions:

1. Is the EFI partition something that has been there since the computer was made, or did Ubuntu install somehow make it? 
2. If it is an older entity (as I presume), does it usually still contain something from the previous windows installation? I mean if I would decide e.g. to go back installing windows on this laptop, could there be some mixup between the previous and new windows installations, especially their licenses and settings?
3. Is the EFI partition still used for something or is it competely irrelevant now? I don't mind the "lost" 500 MB, but just would like to understand the "insides" of the computer better.
4. Based on your somewhat conflicting comments earlier: are there problems ahead if I keep the system and data on the same logical partition (5)?

---

### Post by TheFu on 2020-06-02
1. Could be either. Can't tell.
2. Nothing to worry about. You can remove the Windows files which should be in their own directory, unless your BIOS is broken and requires a stub in the Windows EFI dir that points to the Ubuntu EFI dir.
3. It is used for booting on systems that use UEFI booting.  UEFI is recommended by the Linux Foundation for a more secure workstation, along with some other settings like secure boot and whole disk encryption.  If you use any encryption, be 100% certain you have excellent backups for the data you cannot lose.
4. It is the default setup.  "problems" depends on whether you want to avoid issues BEFORE they can happen or not. Opinions about what is a "problem" is highly subjective.  When it comes time to move to a new release, having the OS and /home on different storage partitions can greatly reduce risk.  If you do backups in an organized way, sometimes that happens on a partition level. If there's one partition, you could be forced to backup the entire partition, rather than just 25G for the OS and "data" for everything else.  Is that a "problem"?  Only you can say?  

If you won't be on Ubuntu in 2 yrs, then do you want the headache of screwing around with storage today? Probably not worth it.  OTOH, making changes to storage BEFORE it has much data on it is much easier.

My "ideal" storage layout:
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

There are some issues with my layout now that snap packages restrict which storage can be accessed by which programs. I keep the OS, HOME, media and stuff that never gets backed up on different storage.  The way I backup the OS is a little different than what I do with HOME, which is different than video, auto, and photo images.  Media doesn't change, so it is more about access, archival, and having 2-3 copies of those files.  HOME gets daily, automatic, versioned backups.  Same for the OS, but at OS upgrade time, the OS gets touched, not the HOME.

All of this is addressed by having a storage plan BEFORE it is needed. Central to that storage plan is a backup and restore plan that is known to work.

Everyone has different experiences.  I've lost 80% of my data before. Don't want to ever be in that situation again.

I don't use or trust the gnome-disks program.

---

### Post by CatKiller on 2020-06-02
> **valdemarv said:**
> Is the EFI partition something that has been there since the computer was made, or did Ubuntu install somehow make it?

It's the [EFI System Partition](https://en.wikipedia.org/wiki/EFI_system_partition). If you're installing Ubuntu in UEFI mode and there isn't one there, the installer will create one.

UEFI replaces the (extremely) old BIOS. BIOS could only use MBR partitions, and the (tiny) bootloader lived in the Master Boot Record and chainloaded the rest of the boot process from there. And had the 4-partition limit. UEFI comes with a new partitioning scheme - GPT - that doesn't have the 4-partition limit. A completely fresh UEFI installation wouldn't need to put the partition within an extended partition. You can have as many independent bootloaders as you want with UEFI, and they all co-exist happily within the ESP.

What I suspect has happened is that your Windows 7 installation was done in UEFI mode, and so had the EFI partition, but you booted and installed Ubuntu in BIOS mode so it put the bootloader in the MBR and created MBR-style partitions but *didn't* nuke the EFI partition in case you needed it.

Ideally you'd have your Ubuntu install in UEFI mode, using GPT partitions, with your bootloader in the ESP. Your slightly messy setup seems to be working, so you don't *need* to change it, but it's something to pay attention to if you reinstall. There are advantages to UEFI over BIOS regardless of the partitioning scheme / bootloader situation, so you might consider doing a reinstall anyway to take advantage of them before you create too much of customisation in your existing install that you'd need to redo.

---

### Post by valdemarv on 2020-06-02
Thanks again TheFu and CatKiller! 

I tried to see what is actually happening during the startup and entered computer settings. It's a long time since I've done something like this, and I'm not familiar with UEFI, so I don't really know what I see after pressing F2 during boot (BIOS or UEFI?). It shows my laptop model on the top and there is a tree (with "Settings" on the highest level of the tree). 

Anyway, under Boot Sequence I can see the disk types and their boot order (HDD, USB, etc.), and also something named Boot List Option, together with a radio button with two options: Legacy and UEFI. Legacy is selected. There is also a button called "View" (grayed out). I changed it for a while to UEFI to see what happens (the button becomes visible and so do two other options, "Add boot option" and "Delete boot option"), but changed it back to Legacy before rebooting. Now it got interesting... this time the computer said that no bootable disk was found, and gave the options e.g. to press F2 again. I did so, entered setttings again, and now the boot sequence had been set to UEFI. I changed it back to Legacy, applied and reboot again, and the computer started ok.

So does this sound like something that confirms CatKiller's suspicion, i.e. that Win was installed using UEFI mode and now I installed Ubuntu in BIOS mode? It is a somewhat old computer, so I don't know if and why someone has changed the modes inbetween.

_**I still haven't understood from what partition is the system booting up now, partition 1 or 5?**_ Is the partition 1 really not in use right now? And how can I remove the windows files that TheFu is referring to ("in their own directory")? Do you mean that I can somehow access the contents of the ESP?
  
I think I want to try to make this system better for future use, so how should I proceed? Should I somehow format/reorganize the disk using this current installation of Ubuntu, or just reinstall Ubuntu and during reinstall do something about it (I remember that there was an option to define partitions or sth)? I presume after that the computer won't start as everything is erased. Should I then leave or erase the Partition 1 too? Or what would be the good way to go? I believe I'd like to install Ubuntu in UEFI mode, using GPT partitions, with the bootloader in the ESP, as CatKiller suggested. And I'd like to get rid of any traces of the earlier Windows.

Btw, If I'd reformat the whole hard drive, erasing all partitions, including the ESP, must I then say goodbye to UEFI in general, or can it be somehow reinstalled afterwards? Lots of questions again. Thanks in advance if someone is kind enough to shed some light...

---

### Post by CatKiller on 2020-06-02
> **valdemarv said:**
> (BIOS or UEFI?) 

All machines from about the last 15 years are UEFI. UEFI can pretend to be BIOS with the option called Legacy, or Compatibility Support Module, which you've already found. 

> I still haven't understood from what partition is the system booting up now, partition 1 or 5? 

Probably neither, strictly. The MBR isn't part of any partition, and your bootloader is probably there. If that's the case, then it's probably chainloading the next stage from your partition 5 and the ESP is vestigial. I don't know for sure, though. 

> Do you mean that I can somehow access the contents of the ESP? 

It's mounted at /boot/efi. By default non-root users can't read from there, but root can. You can also read it from the live installer. 

> I believe I'd like to install Ubuntu in UEFI mode, using GPT partitions, with the bootloader in the ESP, as CatKiller suggested.

If you've got it set to UEFI rather than Legacy then you should get two entries when you choose to boot from your thumb drive: one UEFI and one not. If you boot the UEFI one Ubuntu will install in UEFI mode, otherwise it will install in BIOS mode. 

A useful indicator is that the text-mode part of the installer has a black background in UEFI mode and purple in BIOS mode. 

> Btw, If I'd reformat the whole hard drive, erasing all partitions, including the ESP, must I then say goodbye to UEFI in general, or can it be somehow reinstalled afterwards? 
UEFI is something that your motherboard supports rather than anything else. If you install Ubuntu in UEFI mode it will create an ESP for you (if there isn't one already) and put its bootloader in there.

---

### Post by TheFu on 2020-06-02
CatKIller Is correct.  I'm wrong.  If the system Is usIng bIos to boot, then the EFI area Isn't beIng used.   Sorry, my 'I' key Is broken.

Better would be to use UEFI.  The easy answer Is to do a fresh Install when the BIOS Is In UEFI mode.  Let the Installer wipe everything.  If you want to be fancy, you can "do something else" In the disk setup part.  I usually just ensure the /boot Is at least 700MB to hold a few more bloated kernels and let everything else be default using LVM.  With LVM, experienced people can fix the sizes later without too much fuss.

---

### Post by valdemarv on 2020-06-02
OK, thanks again. Very interesting, I'm learning quite a lot of new stuff. Still, if I may, a couple of clarifications...

> **CatKiller said:**
> 
It's mounted at /boot/efi. By default non-root users can't read from there, but root can. You can also read it from the live installer.
I'm logged in using and Administrator account and tried to open the directory in Files, but it doesn't allow me to open it. I dont' have the "permissions necessary to view the contents of efi". I found some advise ([https://askubuntu.com/questions/650291/how-to-edit-boot-efi](https://askubuntu.com/questions/650291/how-to-edit-boot-efi)) and tried to use "sudo gnome-system-monitor" and opened the File systems. There I was able to double click the directory open. This time I got no error messages, but the folder was reported to be empty. It seems to be that there is nothing in the ESP, provided that this method of checking is reliable. Is it? It indicated though that 4.1 kb were "used". I wonder if that is just something that the ESP needs for itself to function or whether the system monitor just didn't show me everything.  

> **CatKiller said:**
> UEFI is something that your motherboard supports rather than anything else. If you install Ubuntu in UEFI mode it will create an ESP for you (if there isn't one already) and put its bootloader in there.
OK, so by deleting the ESP partition, I cannot delete anything that Dell has provided and is possibly important for the hardware etc. to function? Is all the data in the UEFI screens (I mean those screens I get after pressing F2 at booting) stored somewhere else?

---

### Post by valdemarv on 2020-06-02
> **TheFu said:**
> The easy answer Is to do a fresh Install when the BIOS Is In UEFI mode.  Let the Installer wipe everything. 
If I just set the computer to UEFI mode and do a fresh install, will the Ubuntu default install "wipe everything" (including the current ESP), or do I need to select during the installation the "custom path" for defining partitions etc.?

---

### Post by GhX6GZMB on 2020-06-02
> **valdemarv said:**
> If I just set the computer to UEFI mode and do a fresh install, will the Ubuntu default install "wipe everything" (including the current ESP), or do I need to select during the installation the "custom path" for defining partitions etc.?

Booting from the install media will bring up a "live desktop", from where you'll start the installation.

Yes, you'll be asked about language, keyboard etc.
Then it goes on to the disk(s)

You can define partitioning, mount points, and importantly: should each partition be formatted? YES! (tick box)

Put some brain into exactly this stage of installing and plan your storage architecture beforehand. It's really tedious to change it afterwards.
For a simple laptop, I'd say: just one partition /

And always choose ext4 as file system.

But really: just try it out! What do you have to lose? Your base system works, and if you hate the installation, just do it again!

---

### Post by CatKiller on 2020-06-02
> **valdemarv said:**
> I'm logged in using and Administrator account and tried to open the directory in Files, but it doesn't allow me to open it.

You can use ```
sudo -i
``` to open a shell as root. Then, in my system as an example:

```
cd /boot/efi/EFI/
ls
[COLOR=#0000ff]BOOT  ubuntu[/COLOR]

ls BOOT/
[COLOR=#00ff00]BOOTX64.EFI  fbx64.efi[/COLOR]

ls ubuntu/
[COLOR=#00ff00]BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi[/COLOR]

exit
```

> OK, so by deleting the ESP partition, I cannot delete anything that Dell has provided and is possibly important for the hardware etc. to function? Is all the data in the UEFI screens (I mean those screens I get after pressing F2 at booting) stored somewhere else?

That's all stored in a chip on your motherboard.

---

### Post by valdemarv on 2020-12-28
Hello huge thanks one more time for all the help I got from here. I reinstalled Ubuntu, but due to difficulties getting the computer even to start when I switched UEFI on in bios, I reinstalled Ubuntu in legacy mode. It's been working fine.

And now, against the great principle "If it's n8t broken, don't fix it", I decided to give UEFI one more try. I got the "brilliant" thought to wipe the hard disk before trying another install. There was one about 537 MB primary partition and linux was on the extended partition that takes the remaining space of the hard drive.  

So, I formatted the primary partition (W95 FAT32) and created there a new partition, this time as EXT4. And it is now of course empty. I was not able to format the extended partition probably because linux is running on it.

So now when I change the bios to UEFI, I get and empty boot list and the computer cannot find a bootable drive. When I reset the bios to defaults it starts in legacy mode, but when I go back to legacy and put usb to the first place in boot order, I get the message "Invalid partition table ". I can bypass that with esc, and then Ubuntu starts ok, but it takes quite a long time for it to start (there's just the logo spinning for a while first).

Any idea why the partition table is broken?

---

### Post by CelticWarrior on 2020-12-28
If you want to do it properly then boot a live session, open Gparted and select the drive. Then in Device menu > new partition table, select "GPT" (this will delete everything).

Then change the settings to UEFI only to assure you're booting in UEFI mode and use the option to use all disk.

---

### Post by valdemarv on 2020-12-28
> **CelticWarrior said:**
> If you want to do it properly then boot a live session, open Gparted and select the drive. Then in Device menu > new partition table, select "GPT" (this will delete everything).
Then change the settings to UEFI only to assure you're booting in UEFI mode and use the option to use all disk.

Sounds good, but the problem is that I cannot boot to a live session. When trying to do that, I only get the message "Invalid partition table" when trying to boot from a USB stick. The same happens if I change the boot device order in bios or if I press F12 during boot to have access to the one-time boot menu where I can select boot from usb device. Then when that message appears, I can only press esc (or perhaps some other key too) and the installed Ubuntu boots ok, although much more slowly than it used to be when I still had not wiped the primary partition.

In the meantime I also downloaded the most recent bios from the manufacturer and managed to do a Bios flash update, so the bios is definitely the most recent version now.

I tried to boot both from a Ubuntu install disk and from a Win 10 install disk, with the same result, Invalid partition table. I wonder if I can fix the partition table somehow from within the installed Ubuntu that seems to work completely fine? I have no idea about how to do it though... And I would even be happy to just get back the mbr / legacy bios if easier to do.

---

### Post by CelticWarrior on 2020-12-28
> [COLOR=#000000]When trying to do that, I only get the message "Invalid partition table" when trying to boot from a USB stick.[/COLOR]
If it says the USB drive has an "invalid partition table" then it's probably right. Re-do the USB installer. If doing it from Windows with Rufus make sure UEFI/GPT options are selected before "burning" the ISO. Or use Balena Etcher which makes a perfect copy (boots in UEFI or BIOS mode). Or use any similar tool in Ubuntu, including the default Startup Disk Creator.

---

### Post by valdemarv on 2020-12-28
> **CelticWarrior said:**
> If it says the USB drive has an "invalid partition table" then it's probably right. Re-do the USB installer. If doing it from Windows with Rufus make sure UEFI/GPT options are selected before "burning" the ISO. Or use Balena Etcher which makes a perfect copy (boots in UEFI or BIOS mode). Or use any similar tool in Ubuntu, including the default Startup Disk Creator.

The same happens with both the Ubuntu and Win10 install disks so I don't believe both are faulty, especially since I used the Ubuntu disk to install the currently functioning version. 

I tried now to format the 537 MB primary partition (that used to be EFI partition) back to FAT32 from ext4, and suddenly the Ubuntu install disk agreed to boot (but not the Win 10 disk). So I'm now running a live Ubuntu session and opened Gparted as adviced above. But I'm not sure what to change now to GPT. One of the partitions or the whole disk? And how can I be sure that the whole disk is selected?

---

### Post by CelticWarrior on 2020-12-28
If the disk is shown then it is selected (in Gparted). And obviously the selection part is applicable only in systems with more then one internal drive; with a single drive it should appear by default. But, in either case, you may use the dropdown menu to confirm. When booting from external media it should show that media in the dropdown menu and you should easily spot which are which just by the respective sizes.

Again, changing it to GPT **will delete everything**. Do NOT proceed if you need to backup personal files!

Now, if you already have backups and can afford it nuking from orbit, then proceed as explained before: With the internal drive where you want to install the OS shown in Gparted go to its DEVICE menu, then "NEW PARTITION TABLE" and when asked select "GPT". It's as simple as that. This will create a new GPT partitioning table for that drive which is highly recommended for any modern installation in UEFI. Ubuntu is flexible enough to allow UEFI mode installations in MBR ("msdos") partitioned drives, you very own current situation, but it shouldn't.

GPT solves all the issues with primary/extended partitions that are so confusing to you. With GPT all partitions are primary.

---

### Post by valdemarv on 2020-12-28
Ok, tried this and now got it to work and Ubuntu install disk boots, thank you!

---

### Post by valdemarv on 2020-12-28
Just out of interest in case I decide to install Win10 later... I noticed that while the system now recognised Ubuntu install disk, it does not recognize Win 10 install disk. I wonder why? I've set boot to UEFI in bios.

Do I need to create a separate EFI partition? I've now only the disk as one chunk with no formatting or partitions.

---

### Post by CelticWarrior on 2020-12-28
No, you don't need and shouldn't create a different ESP (EFI System Partition). And the installer booting or not is unrelated to the drive's partitioning type, the problem is likely with the installer itself. I suggest redoing it - very easy if you have a Windows computer and a somehow "advanced" process if doing it from Ubuntu but possible - and then, as then do the same you did to boot the Ubuntu one which was likely using the one-time boot menu or changing the boot order in the firmware (UEFI) settings.

Now that you have GPT you can have a proper dual-boot with both OSes installed, as they should be, in UEFI mode. Something not possible before because Windows isn't flexible as Ubuntu (a good thing in this case) so it only installs in UEFI mode in GPT drives and in Legacy/CSM/"BIOS" mode in MBR (what you had before).
And this is another advantage of UEFI/GPT for multi-booting: You can install Windows after Ubuntu without needing to reinstall Grub. Unlike before with BIOS/MBR, bootloaders now co-exist in the ESP. Of course, Windows change the OS boot order to itself - convenient because its installation requires several reboots - but then it's as easy as opening UEFI settings > Boot and change where it says "Windows bootloader manager" back to "Ubuntu". Then boot Ubuntu - at this point Windows will not show up in the Grub menu - and run 'sudo update-grub'. Also make sure to disable Fast Startup in Windows ASAP and before booting Ubuntu and updating Grub. That should be all.

---

### Post by valdemarv on 2020-12-28
Yes, I did some research too and am thinking that the problem is that my install usb disk is formatted to exFAT which as far as I understand is not supported as a UEFI boot device. Will now try if NTFS would work and if not, will try Rufus as it should probably work somehow making a Mx of NTFS and FAT32.

Thanks for all the tips about double-booting too! Very useful!

---

### Post by CelticWarrior on 2020-12-28
Yes, you're right about exFAT not being supported. FAT32 or NTFS are (for Windows installation media).
And if you're going to use Windows to make the Windows installation media then using Rufus is nonsense! All you have to do is download the most up-to-date Windows ISO and that same page (in Windows only) will let you use the Media Creation Tool automatically. All you have to do is having the target USB flash drive inserted at the time. Unlike third-party tools this is fail-proof.

---

