---
title: "Dual boot problem :( Please help :("
date: 2008-10-27
forum: New to Ubuntu
---

### Post by maxpayne34 on 2008-10-27
Hey guys I'm under lot of stress and unable to use my computer..

I had windows XP and Kubuntu installed in my pc as a dual boot. installed kubuntu on different partition of the same HDD. I was able to use them without any problems for many months. few days ago when i switched on my pc i noticed it was laggy and took few mins to boot. the boot screen was really slow and this happened..

> verifying DMIpool data................
GRUB Loading stage1.5

GRUB Loading, Please wait...

it takes about 10 mins to go to the OS selection menu (i never got this grub loading thing before.. i did but it was so quick that time)

> Ubuntu 8.04.1, kernal 2.6.24-19-generic
ubuntu 8.04.1, kernal 2.6.24-19-generic(recovery mode)
Ubuntu 8.04.1, memtest86+
other operating systems
Mircosoft Windows XP Professional

now when i select Ubuntu it takes another few mins and loads without any problem.. sometimes it doesnt load initialy and gives me error18

when i select windows xp it says

> Error13: Invalid or unsupported executable format

Press any key to continue..

This means im pretty much screwed as i cant access windows :(

Also sometimes while booting it gives ERROR18 as well.. 


I'm confused and dont know what to do. i dont even have a bootable disk !

Please help me :|

Update : I have located the menu.lst

here is it

> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=284446b6-d7ca-4e7e-95f1-b53221c091c4 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=284446b6-d7ca-4e7e-95f1-b53221c091c4 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by damien22 on 2008-10-27
well for starters use a livecd to boot your machine... and for second please tell what is error 18...and what task did you perform the last time your pc worked!?

---

### Post by maxpayne34 on 2008-10-27
> **damien22 said:**
> well for starters use a livecd to boot your machine... and for second please tell what is error 18...and what task did you perform the last time your pc worked!?

Thanks for your quick reply 

I can use kubuntu.. but not windows..

Sometimes when i boot it goes like this

verifying DMIpool data................
GRUB Loading stage1.5

GRUB Loading, Please wait... 
Error18

Most of the time i can boot and get into kubuntu but not windows.. Im getting that error13 when i select XP

I was using it without any problems but that day i left the pc as it is and went somewhere. came back and it was on a powersaving mode.. the monitor usualy goes to standby.. i moved the mouse and nothing.. i rebooted and its laggy ever since and cant access windows :(

---

### Post by ajgreeny on 2008-10-27
> it takes about 10 mins to go to the OS selection menu (i never got this grub loading thing before.. i did but it was so quick that time)
Do you mean you didn't get the grub menu when you booted or simply that it did not take ten minutes previously?  There is normally a screen message about starting grub and loading grub 1.5, or at least there always has been on my machines.  I assume you mean that the timeout for the menu used to be very short, maybe one or two seconds, as I set my computer.

Have you made any recent updates to the system, either software or hardware?  I note you are still using kernel 2.6.24-**19**, not the newer **21** kernel which has caused a few problems for some users, so I wonder if you are updating everything very quickly.  his could be an advantage in your situation as there may be no potential updating difficulties of the kernel type I note above to worry about, but it seems strange that something has started to cause the problem suddenly if nothing has happened to the OS or hardware.

---

### Post by maxpayne34 on 2008-10-27
> **ajgreeny said:**
> Do you mean you didn't get the grub menu when you booted or simply that it did not take ten minutes previously?  There is normally a screen message about starting grub and loading grub 1.5, or at least there always has been on my machines.  I assume you mean that the timeout for the menu used to be very short, maybe one or two seconds, as I set my computer.

Have you made any recent updates to the system, either software or hardware?  I note you are still using kernel 2.6.24-**19**, not the newer **21** kernel which has caused a few problems for some users, so I wonder if you are updating everything very quickly.  his could be an advantage in your situation as there may be no potential updating difficulties of the kernel type I note above to worry about, but it seems strange that something has started to cause the problem suddenly if nothing has happened to the OS or hardware.

sorry that i didnt made it clear properly.. yeah it never took me that long before.. as far as i remember i havent really updated my software/hardware recently.. maybe a couple of softwares in windows and everything worked perfectly.. 

This is very frustrating that i have all my university files under windows and worried that i will never be able to get them back.. im desperate :(

I dont need the kubuntu anymore after this.. is there any way i can get rid of it and get my windows back ?:confused:

Thanks

---

### Post by Sef on 2008-10-27
This is grub error 18:

>  Selected cylinder exceeds maximum supported by BIOSThis error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).       

---

### Post by bumanie on 2008-10-27
You should [read this]("http://users.bigpond.net.au/hermanzone/p15.htm"). About two thirds down the page is a section on grub errors. Downloading super grub disk may also be help.

---

### Post by maxpayne34 on 2008-10-27
> **Sef said:**
> This is grub error 18:

Yeah I read that before. they say i need to do some changes in the BIOS. but there are no clear solutions..

I can boot Kubuntu.. works fine.. I noticed that i dont get error18 now at all.. it takes time to load the os selection menu..

Anyone know how i can get my windows xp back ?

I will lose everything if i do a fresh install :(

Any way to get rid of kubuntu and get my xp back ?

---

### Post by AnxietyDrive on 2008-10-27
I am only a super noob at this and im sure ill be corrected if im wrong but, as far as I know you can mount your windows partition / files system from ubuntu, then copy all your uni files into a safe ubuntu or burn them to disc. At least that way your stress level will be under control and you will live longer:lolflag:
Then you can worry about the techie issues of the dual-boot
AnxietyDrive
salute

---

### Post by ajgreeny on 2008-10-27
If you really want to get rid of (k)ubuntu you can simply delete the partition on which kubuntu is installed, after restoring the windows MBR with your windows install CD.  If you have a Restore CD instead of a windows install CD, you will need to search on google for a MBR restore utility which you can download freely.  After that you can format the kubuntu space back to ntfs for windows use.

---

### Post by inkrypted on 2008-10-27
If you have a Windows install CD put it in the drive and reboot then choose the repair option once it has booted to the cd once in the recovery console type fixmbr then press enter then type fixboot type y press enter then type exit you should now get into Windows upon reboot use you Kubuntu CD to reinstall GRUB and you will be back in business.

---

### Post by maxpayne34 on 2008-10-27
> **ajgreeny said:**
> If you really want to get rid of (k)ubuntu you can simply delete the partition on which kubuntu is installed, after restoring the windows MBR with your windows install CD.  If you have a Restore CD instead of a windows install CD, you will need to search on google for a MBR restore utility which you can download freely.  After that you can format the kubuntu space back to ntfs for windows use.

I would love to do that.. does that means i can get back my windows ? (not a new installation) 

Thanks mates.. Im a total newbie and having problems :(

---

### Post by inkrypted on 2008-10-27
That is excatly what it means. No problem

---

### Post by caljohnsmith on 2008-10-27
The kind of erratic behavior you are describing with slow loading and inconsistent Grub errors would suggest that you probably have a hardware problem at this point. How old is your computer, and especially how old is the HDD? First, I would do as AnxietyDrive suggested earlier, namely mount your Windows partition and immediately copy over all your important files to some other drive. Next I would suggest running some diagnostics tests on the HDD, and also do a RAM test by booting the "memtest86" option in the Grub menu if you have it. If you don't have a diagnostics CD that came with your HDD, you can download the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") and use that instead. Also, if you can check the cable connections to your HDD, I would do that too. Let us know how it goes. :)

---

### Post by maxpayne34 on 2008-10-27
> **inkrypted said:**
> That is excatly what it means. No problem

I found my windows XP Boot CD.. set the CD-ROM as the boot device and booted from CD..

It displayed "Inspecting System Hardware/Software devices" and in few seconds it went off and I see a blank Screen only now :(

Should i let it be like that for sometime and see if i can get to the repair screen ? 

**caljohnsmith**:- My computer is more or less 7 months old and its pretty new.. Athlon 64 X2 2109 MHz..

I did installed a Graphic card & a wireless network card few months back.. no problems with it..

regarding copying files.. I'm going to attempt it..but i dont have any space at all on other drives..lol.. i will use my friends external HDD

I'm doing the memtest as we speak and will post the results..

I will look into the cables ASAP !

Btw You guys rock ! Thanks.. sorry to behave like an headless chicken as I'm worried about getting back my files..

---

### Post by random turnip on 2008-10-27
That GRUB message is usual, this happens every time i have loaded my PC since i installed Ubuntu, GRUB is simply the program that is used to select the OS when loading.

---

### Post by tarps87 on 2008-10-27
> **random turnip said:**
> That GRUB message is usual, this happens every time i have loaded my PC since i installed Ubuntu, GRUB is simply the program that is used to select the OS when loading.

The error: ERROR18 is not usual.
I would suggest backing up you data and then doing as caljohnsmith said. I have had similar issues when by hard drive cable broke, replacing it fixed the problem.

The method inkrypted suggested should get you windows back, you will need to reformat the Ubuntu partition latter but I'd suggest making a copy of your uni work before trying to repartition and format

---

### Post by maxpayne34 on 2008-10-27
Guys...

I'm totally lost :(

I don't know how to get the windows partition :(

I tried to repair the windows with the XP CD but nothing happens after the ""Inspecting System Hardware/Software devices"

I downloaded Ultimate BootCD and there are so much diag tools i dont know which 1 to use :confused:

I'm in the point of breaking down to tears :(

---

### Post by caljohnsmith on 2008-10-27
OK, how about booting up your Live CD, open a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
And then do:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Post the output of the above commands and we can work from there. :)

---

### Post by maxpayne34 on 2008-10-27
> **caljohnsmith said:**
> OK, how about booting up your Live CD, open a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
And then do:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Post the output of the above commands and we can work from there. :)

First command I got this

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb77220ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   c  W95 FAT32 (LBA)
/dev/sda2        40965750   312576704   135805477+   f  W95 Ext'd (LBA)
/dev/sda5        40965813   122881184    40957686    7  HPFS/NTFS
/dev/sda6       122881248   123073964       96358+  83  Linux
/dev/sda7       123074028   126977759     1951866   82  Linux swap / Solaris
/dev/sda8       126977823   136745279     4883728+  83  Linux
/dev/sda9       136745343   312576704    87915681    b  W95 FAT32

Second command

> max@(none):~$ sudo mount /dev/sdal /mnt ls -l /mnt
sudo: unable to resolve host (none)
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
max@(none):~$

Thanks mate :(

---

### Post by caljohnsmith on 2008-10-27
Try doing that from your Live CD, as it looks like you have problems with sudo right now in your Kubuntu install. Also, be sure to enter the commands separately, pressing enter after copy/pasting each one. So try the "mount" and "ls" commands again (separately) from the Live CD and post the results.

---

### Post by maxpayne34 on 2008-10-27
> **caljohnsmith said:**
> Try doing that from your Live CD, as it looks like you have problems with sudo right now in your Kubuntu install. Also, be sure to enter the commands separately, pressing enter after copy/pasting each one. So try the "mount" and "ls" commands again (separately) from the Live CD and post the results.

I booted on liveCD the first command is working and returning the same results..

The second set of commands are not working

When i enter this

```
sudo mount /dev/sda1 /mnt
```

I get 

```
Mount: you must specify the filesystem type
```

When i use 

```
ls -l /mnt
```

I get

```
Total 0
```

Thats it :|

---

### Post by reg4c on 2008-10-27
Try

```

ls -l /media

```
since that is probably the place that you mount the drive to.

Also, the easiest way to do this would be

```

sudo mount -a

```

This mounts all the drives in your fstab file. 

Cheers

---

### Post by maxpayne34 on 2008-10-27
> **reg4c said:**
> Try

```

ls -l /media

```
since that is probably the place that you mount the drive to.

Also, the easiest way to do this would be

```

sudo mount -a

```

This mounts all the drives in your fstab file. 

Cheers

None of them works.. ls -l /media returns total 0 and sudo mount -a doesnt do anything at all

---

### Post by reg4c on 2008-10-27
> **maxpayne34 said:**
> None of them works.. ls -l /media returns total 0 and sudo mount -a doesnt do anything at all

```
sudo mount -a
```

would not produce any visible output in the terminal but would mount the drives.

Can you post the output of 
```
cat /etc/fstab
```

Cheers

---

### Post by maxpayne34 on 2008-10-27
```
cat /etc/fstab
```

I get this

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
```

---

### Post by caljohnsmith on 2008-10-27
Try instead:
```
sudo mount -t vfat /dev/sda1 /mnt -o force
```
If that doesn't give an error, then:
```
ls -l /mnt
```

---

### Post by maxpayne34 on 2008-10-27
> **caljohnsmith said:**
> Try instead:
```
sudo mount -t vfat /dev/sda1 /mnt -o force
```
If that doesn't give an error, then:
```
ls -l /mnt
```

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg | tail or so
```

---

### Post by caljohnsmith on 2008-10-27
Do you remember if sda1 was ever NTFS file system instead of FAT32? After you do that mount command and it gives an error, do:
```
dmesg | tail
```
and post that.

---

### Post by maxpayne34 on 2008-10-27
> **caljohnsmith said:**
> Do you remember if sda1 was ever NTFS file system instead of FAT32? After you do that mount command and it gives an error, do:
```
dmesg | tail
```
and post that.

I think its NTFS ! Not sure though..sorry

Because im booting from liveCD i cant access the internet.. im posting this from my laptop

Anyways this is what im getting something like this >>

[ 127.351206] Bluetooth: LCAP ver 2.9
.... so on 

its quite a lot of type :(

---

### Post by reg4c on 2008-10-27
Perhaps you could try:

```
sudo mkdir /media/winXP
sudo mount -t ntfs-3g /dev/sda1 /media/winXP -o force
```

Cheers

---

### Post by reg4c on 2008-10-27
PFFFT, DOUBLE POST.
Not intentional.

---

### Post by maxpayne34 on 2008-10-27
> **reg4c said:**
> Perhaps you could try:

```
sudo mkdir /media/winXP
sudo mount -t ntfs-3g /dev/sda1 /media/winXP -o force
```

Cheers

First command didnt return anything..so i guess it worked

Second command returned

```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid Argument
The device '/dev/sda1' doesnt have valid NTFS.
maybe you selected the wrong device?Or the whole disk instead of a partition (e.g /dev/hda, not /dev/hda1) ? or the other way around?
```

---

### Post by caljohnsmith on 2008-10-27
I'm not sure what to say, because not being able to mount sda1 (your Windows partition) reinforces the idea that you have a hardware problem at this point. If you have another drive that you can save your files to, I would recommend using something like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover your files from your HDD. You can run it from the "[SystemRescueCD]("http://www.sysresccd.org/")", which you can download. I would highly recommend not trying to boot into Ubuntu on your HDD at this point, because depending on your hardware problem, it could make things worse. Let us know how it goes.

---

### Post by maxpayne34 on 2008-10-27
> **caljohnsmith said:**
> I'm not sure what to say, because not being able to mount sda1 (your Windows partition) reinforces the idea that you have a hardware problem at this point. If you have another drive that you can save your files to, I would recommend using something like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover your files from your HDD. You can run it from the "[SystemRescueCD]("http://www.sysresccd.org/")", which you can download. I would highly recommend not trying to boot into Ubuntu on your HDD at this point, because depending on your hardware problem, it could make things worse. Let us know how it goes.

Thanks a lot for all ur help/time mate.. appreciate it a lot..

I want to call this off.. because you guys have no idea how much stress im under at the moment.. i feel like throwing away this stupid pc and buy a new one :)

---

### Post by reg4c on 2008-10-27
> **maxpayne34 said:**
> Thanks a lot for all ur help/time mate.. appreciate it a lot..

I want to call this off.. because you guys have no idea how much stress im under at the moment.. i feel like throwing away this stupid pc and buy a new one :)

No need for stress, just relax
If you keep thinking about the problem and not the solution you wont be able to do anything.

I wanted to tell you to try sda0, sda2 and other numbers before giving up.

Now, I am really interested in this....:popcorn:

---

### Post by Keen101 on 2008-10-27
I have the feeling that your hard drive is going bad.

Here is what i would recommend for a hard drive that is ok:

Use the Gparted Live-CD if you want to remove Kubuntu. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

After that if you want to try and attempt to restore the windows MBR (Windows bootloader) since GRUB is no longer needed, then use the **SUPER GRUB DISK**. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by inkrypted on 2008-10-27
I have the feeling after reading all the post that it is a hardware problem better remove the drive and put it in a USB enclosure and then transfer those files you want to save to you notebook.

---

### Post by tarps87 on 2008-10-28
Before you give up try

```

sudo mkdir /media/winXP
sudo mount -t ntfs /dev/sda5 /media/winXP -o force

```
(I believe a standard XP install should use the NTFS format)
and
```

sudo mkdir /media/winXP2
sudo mount -t vfat /dev/sda1 /media/winXP2 -o force

```
(This is the same as suggested before but with a folder inside the media one so I might work)
If either of these work the drives will be mounted in /media/winXP or /media/winXP2

---

### Post by maxpayne34 on 2008-10-28
```
sudo mkdir /media/winXP
sudo mount -t ntfs /dev/sda5 /media/winXP -o force
```

I get the outout of
```

Did not find any restart pages in $LogFile and it was not empty.
Warning Forced mount, reset $LogFile.
```

```

sudo mkdir /media/winXP2
sudo mount -t vfat /dev/sda1 /media/winXP2 -o force
```

I get the output 

```
mount point /media/winXP2 does not exist
```

:(

---

### Post by maxpayne34 on 2008-10-28
> **inkrypted said:**
> I have the feeling after reading all the post that it is a hardware problem better remove the drive and put it in a USB enclosure and then transfer those files you want to save to you notebook.

I think ur rite..

Here is an update..

I got Gparted LiveCD.. booted and deleted the 3 Drives held kubuntu.. after deleting them and partioned them together and made a new drive (for windows use)

Booted again and now I got

Grub Loading...
Error 17

I inserted Windows XP bootable.. booted off windows. this time i got the install menu. but i was hoping to repair the C partition that held XP. but when i tried to install it said the partition is either damaged/full .. it never detected a previously installed XP :(

So i think i have to remove the hard drive and take a backup from somewhere Which i hardly doubt cause i think all the data is gone :(

Anything else i can do guys ? guess this is the end :( Thanks everyone :(

---

