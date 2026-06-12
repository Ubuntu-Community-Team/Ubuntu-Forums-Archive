---
title: "hard driver not shown"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by krobi123 on 2013-03-16
I have kubuntu installed and it uses all my diskspace ( hard 500gb). I want to remove ubuntu and install windows, I boot windows and it doesn t recognise any of my hard driver... can i do something from bios or? ... i`m confused, hard to explain. newbie

---

### Post by kuifje09 on 2013-03-16
Well, I think you are not familiar with these matters, it not easy to explain. But Windows does not recon you harddiesk because its formatted as ext2/ext3.
The easiest way to solve, just get the GNU Parted and try to format your drive to   fat16 fat 32 or NTFS.  Everything on the drive will be LOST then.
But I understand that is your goal ?

[http://www.gnu.org/software/parted/](http://www.gnu.org/software/parted/)

Maby, even only placing a new partion tabel will be enough.

---

### Post by krobi123 on 2013-03-16
yes, but i have only one partition and on that is installed my kubuntu... can t i format my hard driver in bios?

---

### Post by Bashing-om on 2013-03-16
krobi123; Hi !

Bios (Basic Inout Output System) has nothing to do with partitioning. In order to partition the hard disk, a partitioning utility must be employed.
If you are going to install Windows as the only operating system on that hard disk, then the windows installer can take care of the partitioning as a matter of course.
The same applies if only ubuntu is to be installed. The ubuntu installer can take care of the partitioning.

If you want to dual boot Windows with say ubuntu, the situation gets a bit more complex.

edit: The reason Windows does not see the Kubuntu partitions is that Windows ( NTFS filesystem) does not read ubuntu's ext4 filesystem. Whereas ubuntu is able to read window's NTFS filesystem.

[INDENT=2]how can we help



[/INDENT]

---

### Post by kuifje09 on 2013-03-16
When you boot the live CD or the CD in recue mode then you could wipe the disk, but I think it is easier to do with GParted.
Just download , burn to ( rewritable for if you don't like it  ) cd, and boot that cd ( its a bootable image. )
Its (GUI)menudriven , I think you must be able to fix the disk, its not that hard.

b.t.w. Why did you not like ubuntu ?

---

### Post by krobi123 on 2013-03-16
ok i managed to change to ntfs but i still can`t install windows, i see the c disk but i can t select as "the driver to be installed".. if i don t boot this appears "error: unknown filesystem. grub rescue>" ....



[COLOR=#000000]Why did you not like ubuntu ? 
I`ll still use a version of linux [now i had kubuntu][/COLOR]

---

### Post by kuifje09 on 2013-03-16
I see, the master boot record  is in the way also. Ugly windows.
If you cannot fix it with GParted, then you realy need to do it with some old bootflop with the dos-tools ( win 98 ?? )
Or boot from the ubuntu cd to rescue mode and install a new MBR.

When in running in ubuntu, ther must be a file, /usr/lib/syslinux/mbr.bin  , which represents a MBR.

just do :   dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda   .

That should get you a new MBR.

---

### Post by krobi123 on 2013-03-16
i have to install in ubuntu [COLOR=#000000]a new MBR. for windows? :|

i`ll try xp 7 and 8 to see if i get the same error[/COLOR]

---

### Post by kuifje09 on 2013-03-17
No , sorry , thats not what I meant to say, but to get a MBR which windows can handle, you need some software doing it for you.
Could be even an old boot flop win-98 with some extra tools ( fdisk \mbr ) , but if you have no other way, then use ubuntu in life-booted way to put a new MBR on the disk.

I'v found on another forum what said this may help to ( however, I am not so shure about ):  

dd if=/dev/zero of=/dev/sda bs=446 count=1

But also need to boot ( not install ) the ubuntu cd, as life cd.

---

### Post by Mark Phelps on 2013-03-17
Whether or bot GRUB is in the MBR of the hard drive only matters if you're booting from the hard drive -- which you should NOT do if you want to install Windows.  That error message you're seeing indicates that you're still booting from the hard drive, not from a CD or DVD.

First thing you need to do is go into the BIOS and ensure that you're booting from the CD/DVD drive.  Don't know which key to press on your PC, as they're all different, but generally, pressing the Del key or the F1 key gets you into the BIOS settings.

Second, you don't want any partitions on the drive if you're going to install Windows -- the installer will create the partition for you and format it in the process.  IF you can't get the drive empty using GParted, then, using another Windows PC, download and burn a CD of the Minitool Partition Wizard Boot CD -- and use that to remove the partitions from the drive.

After that, you should be able to boot from a Windows disk and do the installation.  Personally, I would recommend Win7, if you have that option.

---

### Post by kuifje09 on 2013-03-17
I think from what I read, kobri does install from the cd, else he could not install linux either.
And when trying to install windows it complains it cannot find a useable disk.
Why create another bootable tool if you have a ubuntu life-bootable disk. However the mbr-rebuild possibillity sounds very good.

When doing a little search, even on this forum, a lot of people having problems with the MBR.

But please correct me if I.m wrong.

---

### Post by kuifje09 on 2013-03-17
I just have read the gparted docs, and it says it is able to recover  MSDOS-MBR as here is just needed.
 [http://gparted.org/h2-fix-msdos-pt.php](http://gparted.org/h2-fix-msdos-pt.php)  or I am mislead.

I must admit, it is not very handy...

---

