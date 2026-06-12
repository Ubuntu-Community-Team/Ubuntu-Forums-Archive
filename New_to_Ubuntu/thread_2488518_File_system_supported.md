---
title: "File system supported"
date: 2023-07-07
forum: New to Ubuntu
---

### Post by mordechay2 on 2023-07-07
Hello.
 I'm an AOSP developer and 
I want to work on Windows, macOS, and Ubuntu. 
Which file system can I use to initialize the hard disk that supports all three operating systems and also supports Android development?
(I assume Android development requires a file system that distinguishes between capital letters)

---

### Post by SeijiSensei on 2023-07-07
Don't know about Macs.

The easiest solution is to use virtual machines. You can run an instance of Windows on top of Linux using [VirtualBox]("https://virtualbox.org/") or Linux's built-in "[kernel virtual machine]("https://www.tecmint.com/install-kvm-on-ubuntu/")" system. I've never tried to install MacOS anywhere, so I don't know if you can just download an ISO image and install it to a virtual machine.

If you want to share files between Windows and Linux, set up a shared device with NTFS.

---

### Post by CharlesA on 2023-07-07
It doesn't look like OSX is a supported build environment for building Android itself.

[https://source.android.com/docs/setup/start/initializing](https://source.android.com/docs/setup/start/initializing)

Android Studio, for building apps, can run on any OS, however.

[https://developer.android.com/studio](https://developer.android.com/studio)

I don't think file system matters. Ubuntu should default to ext4

---

### Post by MAFoElffen on 2023-07-07
I do a bit dev work, as well as supporting a lot of other things... Systems engineering and administration, database development and administration, network administration, enterprise architecture, etc. I have also taught Computer Science. I went back to school to help document some of the things I had past experience on. That was fun. 

When I took classes on Android Applications Development, we used Android Studio. Android Studio will run on just about anything. Filesystems are not a limiting factor, but rather whatever the hosting OS  will support. (discussed later.) The Android Emulator within Android Studio is QEMU based.

I mainly stay on Ubuntu with QEMU/KVM installed as my main daily driver where "I live". My editor choices, git, spinning up KVM guests to test my work (or play), are all very well supported on that platform, no matter what the target platform of my endeavors might be. KVM is very flexible and adaptable. I have quite a personal test-suite setup, where I can clone VM Guest machines very quickly to setup my test cases for different things.

File systems are not a factor in that, ***but***... As an experienced IT Profession for over 35 years now, I do take advantage of advanced File Management Systems to help me... Such as using LVM2 and ZFS snapshots to rollback things to specific points of time... Lets just say that I save checkpoints of time to go back to. Unexpected things came happen when you write code and do testing on things. (LOL)

I also use other various 'things' for source version management and version control.

---

### Post by mordechay2 on 2023-07-18
The most important thing for me is that it supports Windows and Ubuntu (Mac is less important), I didn't mean Android Studio, I'm mean AOSP, I use a virtual machine, but I want access to the drive from both Windows and Linux, the file system should be case sensitive

---

### Post by mordechay2 on 2023-07-18
I build in Linux but I want the drive to work in Windows as well (and preferably also in Mac)

---

### Post by gezzer2 on 2023-07-18
> **mordechay2 said:**
> I build in Linux but I want the drive to work in Windows as well (and preferably also in Mac)

i believe NTFS can be used read/write in all the systems now, but can have issues of corruption, but FAT32 can be used read/write in about every system  without any problems but you will have to watch disk sizes ...

---

### Post by ajgreeny on 2023-07-18
Macintosh systems can only be installed and used on Apple hardware according to Apple terms and conditions, and are not available for install on normal PC hardware or as a VM in any way unless things have changed, which I doubt.

---

### Post by CharlesA on 2023-07-19
> **mordechay2 said:**
> The most important thing for me is that it supports Windows and Ubuntu (Mac is less important), I didn't mean Android Studio, I'm mean AOSP, I use a virtual machine, but I want access to the drive from both Windows and Linux, the file system should be case sensitive

If it's on a virtual machine, just install Samba or NFS and use whatever filesystem you want.

---

### Post by MAFoElffen on 2023-07-19
If a VM... QEMU runs on anything. Like i said, the emulator in Android Studio uses QEMU. That is what makes it multi-platform.

Your other options would be to have your VM in VirtualBox or VMware Player. I stopped using VirtualBox and VMware Workstation about 10 years ago. I still keep up with their support issues, but no longer use them personally.

I use QEMU/KVM. My VM storage pool on my Workstation, just happens to be formatted as NTFS...
```

mafoelffen@opti-ubuntu:~$ lsblk -e7 -o name,label,size,fstype,mountpoint
NAME          LABEL             SIZE FSTYPE      MOUNTPOINT
sda                             3.6T             
&#9500;&#9472;sda1                           16M             
&#9500;&#9472;sda2        Win_G             3.4T ntfs        /home/mafoelffen/WIN_G
&#9492;&#9472;sda3        Home_LTS        295.4G ext4        
sdb                           465.8G             
&#9500;&#9472;sdb1        System Reserved    50M ntfs        
&#9500;&#9472;sdb2                        365.2G ntfs        
&#9500;&#9472;sdb3                          508M ntfs        
&#9500;&#9472;sdb4                            1K             
&#9492;&#9472;sdb5                          100G LVM2_member 
  &#9492;&#9472;vg0-lv--0                   100G ext4        /
sdc                             4.5T             
&#9500;&#9472;sdc1                          128M             
&#9492;&#9472;sdc2        WIN_H             4.5T ntfs        /Media_H
sdd                             3.6T             
&#9500;&#9472;sdd1                          128M             
&#9492;&#9472;sdd2        WIN_F             3.6T ntfs        
sde                             3.6T             
&#9500;&#9472;sde1                           16M             
&#9492;&#9472;sde2        20210604          3.6T ntfs        
sr0                            1024M             
mafoelffen@opti-ubuntu:~$ grep . /etc/mtab | grep -v -e 'nsfs\|squashfs\|tmpfs\|snap\|sys\|run\|proc\|devpts\|mqueue\|hugetlbfs'
/dev/mapper/vg0-lv--0 / ext4 rw,relatime 0 0
/dev/sdc2 /Media_H fuseblk rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0
/dev/sda2 /home/mafoelffen/WIN_G fuseblk rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0

```
My notes on NTFS:
I have used NTFS as a go between filesytem format for, well since OpenSolaris in 2005. With both CIFS and SMB shares, and with native mounted drives, to share information between OS'es. So what... 13 years or so? I have not had any experience with having corrupted files, because of that. What I can say, is that if you have a partition with an NTFS filesystem on it, and you want to resize that partition, use Windows Disk management tools to do that. Linux tools do not recognize the indexes Windows uses in that filesystem. You will end up having to rebuild those indexes if something happens while trying to use Linux Tools to do that.

---

### Post by TheFu on 2023-07-20
There's no native file system that can be read and written to by all 3 OSes.  The closest is NTFS, but it isn't case-sensitive.  NTFS will regain case, when provided, but as every Java programmer who takes their programs from MS-Windows to Unix, you have to be extremely careful about case if you will deploy to any Unix.

Never use FAT32.  Use exFAT instead.

There are questionable 3rd party drivers for EXT3 file systems available on MS-Windows. If you feel lucky, those are options. I've never used any.

I've had issues using CIFS/Samba for software development to remote storage.  CIFS is a "lowest common denominator" solution.  

The best solution is to develop and code on Linux and have porting to other platforms at least 2-3 times each week, not longer.  I was a cross-platform developer for about a decade.  We coded for 12+ platforms, including MS-Windows and MacOS, but the initial coding all happened on UNIX systems, mainly Solaris, but some was done on Digital Unix, Irix and HP-UX because those platforms were what people sat behind. Spreading compilation jobs around to balance the load was common in our environment.  We had more Solaris systems, so compiles and links would use 5 of those systems and run much faster than on a single HP-UX box (of similar capability), but if we had time before the completed build would be used (perhaps it was lunch time), then staying off the Solaris systems was kind to other people.

I would only use NTFS if that file system was going to be physically connected to an MS-Windows computer. Over the network, I'd use any native Linux file system and NFS for most Unix-based systems (including MacOS), but CIFS for MS-Windows clients.  I'd keep the physical storage on Linux.  For primary storage, I don't use USB. USB uses an inferior storage command set to what SAS/SATA/eSATA use and it is obvious.  I only use USB storage for backup purposes.

---

### Post by mIk3_08 on 2023-07-20
> **mordechay2 said:**
> I build in Linux but I want the drive to work in Windows as well (and preferably also in Mac)
I never heard of this. communicating the drive locally from Linux Ubuntu to MS Windows and vice versa? In my case, I use MariaDB to communicate the drive of  MS Windows using my Linux Ubuntu Machine but I don't know how to communicate from MS Windows to my Linux Ubuntu Machine drive. I usually put my Linux files to MS Windows Machine if MS Windows Machine needs it for some reasons. Regards and cheers.

---

### Post by TheFu on 2023-07-20
DBMS isn't a file system.

---

### Post by MAFoElffen on 2023-07-20
+1 with TheFu...

If it is a network share, it doesn't matter what the filesystem is, because it is the file itself that is shared. I believe both our preference for share is NFS. Both Windows and Linux do NFS well. I struggled making CIFS to work consistently. SMB was better. But NFS works for me.

Locally attached, I use NTFS.

Head TheFu's warnings on FAT32... and ExFAT. FAT32has a filesize limit of 4GB and a partition limit of 8TB. Microsoft says that the ExFAT file system works with all versions of Windows, Mac OS X, needs additional software on Linux. But all the other marketing hype... That is a real stretch of the truth in the real world. 

You've seen the threads here on this Forum with users trying to use ExFAT, right? It is read-only with some Mac's and some versions of Linux (needs drivers which are not installed by default). ExFAT has no support for journaling, a feature that allows the file system to keep records of changes made. Because of that omission, Apple recommends that you only use it on media used to transfer files to, not for every day access. ExFAT lacks the consistency checks and advanced features of NTFS. ExFAT, even though being a newer file system than NTFS, it was created to bridge the gap between FAT32 and NTFS. ExFAT's file transfer rate is much slower than NTFS.

And that is the short list.

For Ubuntu 22.04 LTS, if you want to use ExFAT, install package 'exfat-utils'. It is not installed by default.

---

### Post by MAFoElffen on 2023-07-20
Oh Dang... Sorry, I just learned it "is" possible...

I just figured out a way to mount ext4 formatted partitions in Windows WSL2 and be able to access then inside of the Windows file explorer.

From a PowerShell command prompt with administrative privileges 
```

wmic diskdrive list brief
wmic diskdrive get manufacturer, model, partitions
wsl --mount \\.\PHYSICALDRIVE1 --partition 1 -t ext4

```
The disk identifier in line #3 is from whatever the output is in the first 2 lines... With the target partition number.

Then from the address bar in the File explorer
```

\\wsl$\Ubuntu-22.04\mnt\wsl

```
RE: [https://learn.microsoft.com/en-us/windows/wsl/wsl2-mount-disk](https://learn.microsoft.com/en-us/windows/wsl/wsl2-mount-disk)

---

