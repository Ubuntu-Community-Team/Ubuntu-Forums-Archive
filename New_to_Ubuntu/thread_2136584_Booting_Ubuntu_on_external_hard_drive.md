---
title: "Booting Ubuntu on external hard drive?"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by AutumnFox on 2013-04-18
Hey guys!
Wasn't sure which category this problem might fit best, so I settled on posting it here. I was wondering if it were possible for me to boot up the Ubuntu OS from my now external hard drive?

You see, a few weeks ago my laptop decided to no longer work. (It turns on, but doesn't seem to actually do anything.) And because we couldn't figure out the problem, we decided to take out my hard drive, and make it external temporarily. Initially, there wasn't any pressing need for me to attempt to access it until now.
Thing is though, I've never had to do this sort of thing before. And therefore have virtually no idea what I'm doing.

If it's at all relevant, the computer that I currently borrow uses Windows 8. And my hard drive has two partitions on it. Ubuntu 12.04, and Windows 7.

I would love to get back to using Ubuntu again, so help would be very much appreciated! ^^

---

### Post by duanedesign on 2013-04-18
HI,
Is the hard drive now hooked upp usb? Or is still hooked up as normal just sitting outside the case?
Is their more then one HD hooked up right now, working or not?
Thanks Duane

---

### Post by MoebusNet on 2013-04-18
> I was wondering if it were possible for me to boot up the Ubuntu OS from my now external hard drive?

IMPORTANT: Back up your data before doing anything else. You don't want to lose your data or your friend's data.

Try going into your BIOS and set it to boot from USB before HDD. That way when it finds the bootable OS's on the USB HDD it will boot from there before it gets to the internal HDD. Of course, if your borrowed computer uses UEFI for boot and you old computer didn't, that will be another kettle of fish:

[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode)

If your borrowed computer uses UEFI, it looks as though you need the 64-bit version of Ubuntu if you have been using the 32-bit version. Be careful! Try not to make changes on the borrowed computer's HDD if you can.

---

### Post by AutumnFox on 2013-04-18
@duanedesign
It is hooked up as USB now. The only other hard drive besides it would be the internal hard drive.

@MoebusNet

That is simple to do for the internal drive and my Windows 7 partition. But the computer cannot detect my Ubuntu partition. Is there a way for me to back up the data somehow despite that?
The day before, we even made a bootable USB flash drive, to see if I could even get to my files. I could see the folders, but opening them only had it tell me I didn't have permission, so no files showed.

Heh. That is indeed a different kettle of fish, as both of my partitions are 32-bit. And looking into the BIOS of this computer has mentioned UEFI. (It is 64-bit.)
I'm trying to make sure that I don't mess with the borrowed computer too much. As they wouldn't like it one bit if I messed it up.

Aside from that, I was curious to see what might happen if I tried to boot it up on a 32-bit Vista computer instead.
Which trying to boot it up from there didn't seem to work. (Which I had a feeling that might happen.);

error: unknown filesystem
grub rescue >


So, I won't mess with it any further, until I can get my Ubuntu files backed up.

---

### Post by MoebusNet on 2013-04-19
Possibly this will help:

[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

[https://help.ubuntu.com/community/Installation/FromImgFile](https://help.ubuntu.com/community/Installation/FromImgFile)

To avoid messing up your borrowed notebook's hard drive, you can boot from a Ubuntu Live-USB or Live-DVD and then access your files on the external HDD. The data files themselves don't care if you are running a 32-bit or 64-bit OS.

QUESTION: Have you tried booting your old notebook from Live-USB or Live-CD/DVD to make sure it is truly dead (hardware) and not just a messed-up OS? I'd try to diagnose the old one when you get the time.
 If it is dead, you need to be shopping for your own notebook if you can't get your old one going again. That way you minimize the chances of borking your borrowed notebook.

---

### Post by MoebusNet on 2013-04-19
The other way to go about this is from the Window 8 end, but that has drawbacks:

[http://ubuntuforums.org/showthread.php?t=2080028](http://ubuntuforums.org/showthread.php?t=2080028)

oldfred mentions that Win8 does not support ownership or permissions for Linux filesystems.

But if you just want to view the files without making changes, maybe:

[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

Just be aware that writing to your Ubuntu ext3 or ext4 filesystem from Windows can cause corruption and/or loss of data, because of Windows' lack of support.

---

### Post by oldfred on 2013-04-19
To repair Windows you need a Windows repairCD with the same 32bit or 64 bit version.

You should be able to repair Ubuntu with a liveDVD or Flash drive, but again best to be same version. Newer may work depending on repairs or you have to chroot into your install and repair it internally. 

As posted above backup is the most important first task.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by AutumnFox on 2013-04-19
@MoebusNet

Right, I do have a Live-USB. Which I mentioned I had already used to see if I could get to the files on my Ubuntu partition.
The first time I used the Live-USB, it did mount the Ubuntu partition, but I lacked permission to actually see/do anything beyond the folders that I kept on the Desktop.

I assume that was probably my best opportunity to get those files backed up, had I figured out how to obtain permission. Since for some odd reason, when using the Live-USB now, it looks like it's not even mounting my Ubuntu partition. Just the Windows partition like usual. So I don't know what that's all about, or what I should do...

Any idea if something can be done now so I can backup my Ubuntu files? ^^;

> [COLOR=#000000]QUESTION: Have you tried booting your old notebook from Live-USB or Live-CD/DVD to make sure it is truly dead (hardware) and not just a messed-up OS? I'd try to diagnose the old one when you get the time.[/COLOR]
[COLOR=#000000]If it is dead, you need to be shopping for your own notebook if you can't get your old one going again. That way you minimize the chances of borking your borrowed notebook.
[/COLOR]
I actually never thought to try that. So I did, but the attempt seemed futile. As not even the Live-USB worked. (Which is a shame...)
Eventually, I do intend to get myself a new computer. But that won't happen for a while, unfortunately.


@oldfred

I'll have to find out if we even have a repair CD for Windows. Even though my Windows partition isn't exactly a huge priority at the moment for me.

As I've mentioned, I have a Live-USB. But now I can't seem to get to my Ubuntu partition like I could the first time. =/

I also got the Boot Info report, so here are the results;
[http://paste.ubuntu.com/5722274/](http://paste.ubuntu.com/5722274/)

---

### Post by oldfred on 2013-04-19
It shows it could not mount sdc5, your Linux partition.

Often abnormal shutdown can cause corruption. And a fsck can fix it.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdc5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc5
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdc5

---

### Post by AutumnFox on 2013-04-19
Oh. That would explain a lot, I guess. Haha...
Anyways. The first e2fsck command didn't seem to work for my Ubuntu partition. So I tried the second one.
After waiting, this was what it told me.

*** journal has been re-created - filesystem is now ext3 again ***

/dev/sdc5: ***** FILE SYSTEM WAS MODIFIED *****

  690396 inodes used (9.54%)
    1636 non-contiguous files (0.2%)
     614 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 617179/299/1
13882941 blocks used (47.99%)
       0 bad blocks
       0 large files

  505937 regular files
   94620 directories
      55 character device files
      24 block device files
       0 fifos
4294966993 links
   89755 symbolic links (72833 fast symbolic links)
       3 sockets
--------
  689786 files

---

### Post by MoebusNet on 2013-04-20
@AutumnFox - first, let me say that oldfred is the expert, not me. You should give priority to his advice; I'm just trying to be of some limited assistance. second, I don't think you mentioned which Ubuntu you tried to Live-boot your old notebook with. Is it the same version you had on the old notebook, or are you trying a newer version? The reason I bring this up is that the newer versions of Ubuntu have changed their support for hardware, which could prevent you from booting the newer version on older hardware. Your best bet would try to Live-boot your old notebook with the same version of Ubuntu you originally had on your HDD before you give up on the old notebook entirely. Cheaper than another notebook to try anyway! :)

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by oldfred on 2013-04-20
Was filesystem format ext3, if so it looks like it did make some repairs. Can you now mount it and see files inside the ext3 partition?

---

### Post by AutumnFox on 2013-04-20
@MoebusNet
Alrighty, but I do appreciate the help. ^^
And that is true, it would be cheaper. I would love it if I could use my own laptop again too. The iso I chose for the Live-USB was 12.04, the only slight difference is that it's 64-bit. Should that necessarily make a difference?

I don't want to give up on it just yet, especially if there is still the chance that I can get it working again. But not really knowing what the problem is exactly does make it difficult.


@oldfred
It wasn't mounting automatically. So I tried to mount it through the terminal. (Which I created a directory for it, but don't really know if the name in particular was important.)

ubuntu@ubuntu:/media$ sudo mount -t ext3 /dev/sdc5 /media/Linux
mount: wrong fs type, bad option, bad superblock on /dev/sdc5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by oldfred on 2013-04-20
From liveCD is it still sdc5, with my system sometimes drives get moved around depending on how I boot.

That type of error is often trying to read NTFS with ext3 or vice-versa or corruption that the e2fsck should have fixed, or partition is not now sdc5? Or was it ext4 and should not be ext3?

---

### Post by MoebusNet on 2013-04-20
> **AutumnFox said:**
> @MoebusNet
The iso I chose for the Live-USB was 12.04, the only slight difference is that it's 64-bit. Should that necessarily make a difference?

This is just my opinion, but it seems like that since you had Ubuntu 12.04 32-bit running on your old computer before, your best chance for getting your old notebook to boot would be with the same version: Ubuntu 12.04 32-bit. Most newer computers with newer CPU's can run 64-bit OS's but some, like my 2002 Pentium-M notebook, can only run 32-bit OS's (mine originally came with WinXP 32-bit). Your borrowed notebook is new enough that it needs the 64-bit version as previously mentioned.

---

### Post by AutumnFox on 2013-04-21
@oldfred

I'm actually not using a LiveCD. I guess... I was supposed to, and not the USB? (Tried to use one when I burned the iso onto a disc, but it wouldn't boot.)
Don't know if it was supposed to be ext4 or ext3. Sorry.
From the Live-USB, I'm pretty sure that it is sdc5. Based on what fdisk -l says. (Which I had checked to be sure.)

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3d867707

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8126 MB, 8126464000 bytes
33 heads, 32 sectors/track, 15030 cylinders, total 15872000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e38bb7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15871999     7931968    c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015d46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848   256972799   128382976    7  HPFS/NTFS/exFAT
/dev/sdc3       256974846   488396799   115710977    5  Extended
/dev/sdc5       256974848   488396799   115710976   83  Linux


@MoebusNet
Ah, okay. Well, I'll definitely have to give it another try then!
Let's hope that it will work, when I do try again. =)

---

### Post by oldfred on 2013-04-21
It seems you are still on the Windows 8 UEFI system?

UEFI complicates everything and is not really compatible with MBR(msdos) systems. A UEFI system will only boot with a 64 bit system with secure boot off usually. You can convert a UEFI system to BIOS but that is not what you want. 
You do have to be careful to change UEFI to secure boot off, fast boot off in Windows/UEFI and boot a live installer in BIOS mode and then be careful not to modify anything else in the UEFI sda drive. Then undo those settings when done or Windows 8 may not work.
Would be a lot easier if drive was in a BIOS based system.

---

### Post by AutumnFox on 2013-04-21
Yeah, still am. Though at this point, it's quite tempting to switch over to another computer that doesn't have UEFI. And hopefully make things much more simpler.
Goodness, that stuff sounds a little complicated... And almost not worth risking this laptop.

My other options, are a slightly older Windows Vista 32-bit laptop. And a desktop that also has Windows 7, but is 64-bit.

I'm actually wondering now if it would be a good idea to swap out the hard drive in the Vista laptop and replacing it with mine temporarily.

---

### Post by MoebusNet on 2013-04-21
I think your simplest option to recover the files on your external HDD would be to boot the Windows Vista laptop (because it boots via BIOS not UEFI) with Ubuntu 12.04 and connect the external HDD to recover the data files. Once the data files are recovered, all else is at your leisure.

---

### Post by AutumnFox on 2013-04-23
It does sound like the much simpler option, so I'll be going with using the Vista laptop for my hard drive instead of Windows 8 for the time being. Though I still need to know what I should do now about getting my Ubuntu partition mounted.

---

### Post by MoebusNet on 2013-04-24
I haven't had to do this (fortunately) but I think this will do the trick:

How to recover Ubuntu files on hard drive from Live CD
[http://ubuntuforums.org/showthread.php?t=1767278](http://ubuntuforums.org/showthread.php?t=1767278)

EDIT: I just tried this on my notebook booting from Ubuntu 12.04.2 Live-CD. I was able to see the files on my HDD from the file manager on the Live-CD, and right-clicking on them offered me the option to copy but not delete the files in my /home directory. Using 'gksu nautilus' in Terminal allowed all options in the right-click menu. Thought you'd like to know.

---

