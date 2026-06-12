---
title: "Questions about dual booting, HDDs, RAID Controllers and WINE..."
date: 2008-09-18
forum: New to Ubuntu
---

### Post by cshard on 2008-09-18
I've been keen to install Ubuntu in order to learn more about Linux in general but it will be some time more before I try to install it. However, before doing so, I have a few questions on prepping my current PC to be both XP and Ubuntu friendly as well as clearing up some of my misconceptions.

I intend to dual boot XP and Ubuntu on a large full tower casing (Coolermaster Cosmos 1000) and I have space for 6 3.5' HDDs by default. This is how I wish to arrange my HDDs:

--------------------------------

Currently existing
- 1 250 GB HDD for XP divided into 2 partitions (one for OS and the other for data/program files)

- 1 500 GB HDD for data formatted as NTFS

- 1 2.5' 160 GB HDD in a hotswap portable drive

Future Planning
- 1 250 GB HDD for Ubuntu

- 1 500 GB HDD (either for extra data storage for Ubuntu or for a future RAID 1 config with the existing 500 GB drive)  

- 2 1 TB or larger HDD in RAID 1 Config for backup storage

--------------------------------

What I am concerned about is about the following:

1. The Ubuntu documentation covers setting up for a dual boot on the same HDD as the Windows partition, but not for separate HDDs. My own experience tells me that the BIOS should auto detect the two OSes and give me the option to boot to either, but as I have never set up a PC to dual boot two radically different OS types on 2 separate HDDs, I do not want to leave this to chance. Has anyone done something similar previously?

2. How does Ubuntu (or any Linux variant) access HDDs that have been formatted by XP or Vista? Can the data stored be accessed through Ubuntu without ill effects, or do I need to format the drives in a certain way beforehand? Will Ubuntu write anything to a XP formatted HDD while accessing it that may affect XP's performance?

3. If I have a pair of HDDs in RAID 1, can both OS environments detect the HDDs and access data from both without problems, or will I need to do anything specific to ensure compatibility in both? In addition, will writing data to such a HDD setup cause problems for existing data such as read/write errors, data corruption, etc?

4. I have a number of applications that I need XP specifically for, especially 3D modelling, graphic software and games and I do not intend to abandon XP just yet.  However, I would like the convenience to access some games and some software while still in Ubuntu, without needing to reboot. Besides WINE and the many variants, what other software can emulate a XP environment? I have heard of a few versions that use files from an actual windows installation - can anyone point me towards the documentation for that?

---

### Post by Sef on 2008-09-18
> 1. The Ubuntu documentation covers setting up for a dual boot on the same HDD as the Windows partition, but not for separate HDDs. My own experience tells me that the BIOS should auto detect the two OSes and give me the option to boot to either, but as I have never set up a PC to dual boot two radically different OS types on 2 separate HDDs, I do not want to leave this to chance. Has anyone done something similar previously?


Read the[ Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") for how to install on two separate hard drives.

> 2. How does Ubuntu (or any Linux variant) access HDDs that have been formatted by XP or Vista? Can the data stored be accessed through Ubuntu without ill effects, or do I need to format the drives in a certain way beforehand? Will Ubuntu write anything to a XP formatted HDD while accessing it that may affect XP's performance?


GNU/Linux can read and write to NTFS files with the ntfs-3g driver which is available in the Ubuntu Universe repository.  Universe = Open Source software not maintained by Canonical.

> 3. If I have a pair of HDDs in RAID 1, can both OS environments detect the HDDs and access data from both without problems, or will I need to do anything specific to ensure compatibility in both? In addition, will writing data to such a HDD setup cause problems for existing data such as read/write errors, data corruption, etc?

There is some software for XP (and Vista, maybe) that makes it (them) read and write to ext2, and ext3 also I believe.  Ext3 is the default file system for Ubuntu.

> 4. I have a number of applications that I need XP specifically for, especially 3D modelling, graphic software and games and I do not intend to abandon XP just yet. However, I would like the convenience to access some games and some software while still in Ubuntu, without needing to reboot. Besides WINE and the many variants, what other software can emulate a XP environment? I have heard of a few versions that use files from an actual windows installation - can anyone point me towards the documentation for that?

There are virtual installs.  I'm not sure what Ubuntu uses, but it is possible to set one up, if you processor is designed for it.

---

### Post by jbrown96 on 2008-09-18
Welcome to Ubuntu.
1) I've never tried this, but Grub does support it. BIOS does not choose OSes or anything like that; it simply initializes hardware and a few other very basic things. The MBR (master boot record) actually starts loading the OS. I'm not sure how well Ubuntu will auto-detect systems on other drives, but you can set it up manually fairly easily. I would install Ubuntu with no other drives connected. Once that's done, you need to connect the other drives. Run ```
sudo fdisk -l
``` to find the drives/partitions. Edit your /boot/grub/menu.lst file. you need to make a backup first with ```
sudo cp /boot/grub/menu.lst /boot/menu.lst.back
``` then edit with ```
sudo gedit /boot/grub/menu.lst
``` There's nice section in the middle > # title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

copy and paste the windows section at the bottom (after ### END DEBIAN AUTOMAGIC KERNELS LIST), remove the "#"s at the beginning of each line, and change the (hd0,0) depending on what fdisk told you. If your windows partition is located at /dev/sda1 then it would be (hd0,0) /dev/sda2 is (hd0,1) /dev/sdb1 is (hd1,0), etc. Save the file and you should be able to choose to boot windows by pressing escape when grub is loading. 

2) Ubuntu can access it all fine. Gnome will even take care of mounting, although you might want to look into editing /etc/fstab to get more consistent mount points.

3) RAID is below the OS layer, and as such, the OS has no idea that RAID is active*. Unless you are running software RAID, and I wouldn't recommend doing that on a dual boot system. RAID 1 does not do any type of data backup* (redundancy). It only does striping, which is not what you want at all. Look at RAID 0 with hardware RAID.

4) Wine and virtualization are the only two options. Winw allows you to run some native .exes. Virtualization runs a complete copy of windows inside Ubuntu, which is great for compatibility, but bad for performance* (with some apps, particularly graphics intensive ones. Since DirectX does not work, you won't be able to play games or do 3d work with virtualization.

---

### Post by mc4100 on 2008-09-18
> **cshard said:**
> 
3. If I have a pair of HDDs in RAID 1, can both OS environments detect the HDDs and access data from both without problems, or will I need to do anything specific to ensure compatibility in both? In addition, will writing data to such a HDD setup cause problems for existing data such as read/write errors, data corruption, etc?

I've no experience with RAID, but reading/writing from/to an NTFS partition from Ubuntu has always been flawless, I've never had any problems with corruption. However, I don't recommend trying the reverse, everytime I've tried to add ext3 support to windows I get Windows explorer crashes, and I stopped using Windows for that reason, in case I damaged the ext3 partition.

---

### Post by cshard on 2008-09-18
@mc4100:

So all current ext3 support for Windows is unstable?

@jbrown96:

1. Thanks for clearing up that misconception about BIOS for me. XD So basically setting up Grub correctly will clear up any issues regarding dual booting?  I suppose that leaving the Ubuntu HDD as Master and the XP HDD as Slave will be ideal in the situation, or is it possible the other way around? 

2 & 3. Noted. Basically no real issue with reading and writing to NTFS in any way. Does Ubuntu write anything to those HDDs while accessing them?

As for RAID 0 vs RAID 1, I'm looking for data redundancy rather than combining drives to increase size, and as far as I remember, RAID 0 is for combining 2 or more HDDs for increased total capacity while RAID 1 is for HDD mirroring. Did I get something wrong?

Not sure if my motherboard supports hardware RAID out of the box and I need to check it first (It's an Asus P5K Pro Workstation motherboard if I'm not wrong) but in the event that I don't have one, what is a recommended hardware RAID controller card for Ubuntu?

4. A few of my games are not 3D based, but still use Direct X to some extent, so I'm not too sure. I don't intend to abandon XP so fast anyway.

@Sef:

1. Thanks. Checked out the thread but it kinda led me back to the Ubuntu forums again. XD

2. Found the driver. Will check it out.

3. Any known problems with the ext2 Installable File System for Windows? And any specific distribution I should look out for?

---

### Post by jbrown96 on 2008-09-20
>  2 & 3. Noted. Basically no real issue with reading and writing to NTFS in any way. Does Ubuntu write anything to those HDDs while accessing them? It won't write anything unless you tell it to. Windows likes to create "thumbs.db" files and maybe some other ones, but Ubuntu won't do anything like that. You could even change the permissions of the folder in which you mount the drive to be read only, which would safeguard you even more, but NTFS support in Ubuntu, from my experience, has been flawless.

From Wikipedia > Raid 0
Striped set without parity/[Non-Redundant Array]. Provides improved performance and additional storage but no fault tolerance. Any disk failure destroys the array, which becomes more likely with more disks in the array. A single disk failure destroys the entire array because when data is written to a RAID 0 drive, the data is broken into fragments. The number of fragments is dictated by the number of disks in the array. The fragments are written to their respective disks simultaneously on the same sector. This allows smaller sections of the entire chunk of data to be read off the drive in parallel, giving this type of arrangement huge bandwidth. RAID 0 does not implement error checking so any error is unrecoverable. More disks in the array means higher bandwidth, but greater risk of data loss. SNIA definition.
> Raid 1
Mirrored set without parity. Provides fault tolerance from disk errors and failure of all but one of the drives. Increased read performance occurs when using a multi-threaded operating system that supports split seeks, very small performance reduction when writing. Array continues to operate so long as at least one drive is functioning. Using RAID 1 with a separate controller for each disk is sometimes called duplexing. SNIA definition.
You want Raid 1 to protect your data. i don't see any reason to use Raid 0, unless it is a Raid 0+1 array but that's different. Raid 0 is doubly dangerous because if either disk fails, all data is lost.

---

