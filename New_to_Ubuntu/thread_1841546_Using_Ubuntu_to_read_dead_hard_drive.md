---
title: "Using Ubuntu to read dead hard drive"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by sbr2011 on 2011-09-09
I've never used Ubuntu and my Dell PC with Vista crashed and would not boot, so I made an Ubuntu CD, v11.04. Now I would like to recover my data.

But I do not see my hard drive on the Disk Utility, under Storage Devices.

I chose the option to "try Ubuntu without making changes to my PC" and I am able to boot and navigate around Ubuntu, so my hard drive clearly isn't dead, but I can't directly access it. (I'm typing this from another PC.)

My problem seems similar to the rather old thread linked below. I sort of understand what needs to be done, but typing in commands and the actual steps to take are beyond my comprehension... Uh. NTFS partitions, what?

[http://ubuntuforums.org/showthread.php?t=540582](http://ubuntuforums.org/showthread.php?t=540582)

---

### Post by sbr2011 on 2011-09-09
sudo fdisk -l

is that a number one or the letter L ?? I really don't know what I am doing. I typed in the #1.



ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
fdisk [options] <disk>    change partition table
fdisk [options] -l <disk> list partition table(s)
fdisk -s <partition>      give partition size(s) in blocks

Options:
-b <size>                 sector size (512, 1024, 2048 or 4096)
-c                        switch off DOS-compatible mode
-h                        print help
-u <size>                 give sizes in sectors instead of cylinders
-v                        print version
-C <number>               specify the number of cylinders
-H <number>               specify the number of heads
-S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$[]("http://ubuntuforums.org/showthread.php?t=540582")

---

### Post by Enigmapond on 2011-09-09
The fact that you can navigate on Ubuntu has nothing to do with the HDD. With a live CD, it doesn't use the HDD...you are navigating the LiveCD. If, when you boot up the CD and go to Places, you don't see your NTFS,(that's just the file system for Windows) then follow the steps given below...from that thread:

Boot up the Ubuntu live cd and once you're at the desktop, open a Terminal.

Type:
```
 sudo fdisk -l 
```

You'll get a list of partitions on the pc You'll likely have an  NTFS partion that is called /dev/hda1 or /dev/sda1 . Just match the name  to your list.

We need to make a folder to mount the data in so let's create one

 ```
 sudo mkdir /data
```

Then lets mount the Windows partion into it so you can copy off  the data (match the /dev/ name to what you found in the list above

 ```
 sudo mount /dev/hda1 /data 
```

If that completed without errors you can open a file browser and  go to the /data folder and see the files. Email or copy them off as you  wish.

---

### Post by josh6190 on 2011-09-09
Im not a super genius, but i have had this problem before.. when you cant access the drive in disk utility (or gparted) then it is possible it is dead beyond recovering data. That was my experience anyways.

---

### Post by peter d on 2011-09-09
When you boot from a live Cd it does not use your hard drive at all. The fact that Ubuntu is running does not indicate any life in your hard disk.

NTFS is the file system that Windows uses. Ubuntu 11.04 should have no difficulty reading it. If it can read your disk it should show up in Nautilus as something like 250GB File system. If it's there click on it to try to open it. If so you should be able to save the access the files and work on saving what you want.

---

### Post by sbr2011 on 2011-09-09
How can your pc boot if the hard drive is toast??? Is there a way to make my hard drive bootable again? I do not have a windows vista recovery CD, that's why I'm trying ubntu. I wanted to try and save the files before doing a clean install of windows.

When I plug in my external hard drive it shows up on the disk utility as 80 GB FILE SYSTEM or whatever and works fine. I was hoping the internal hard drive would be on the disk utility so I could transfer files but it isn't.

---

### Post by cstambaugh on 2011-09-09
I dont know if this helps, but if you want to recover your data you can try this, remove your hard drive and install it into another computer, a desktop, or computer that can take a second hard drive, or you can purchase an USB to hard drive cable for about 30 bucks on ebay and plug your hard drive into it and it will boot just as a external drive. You can access your files that way to transfer them to another form of media. This is assuming you do not have a windows vista disc and cannot repair startup using the disc, or boot up in safe mode. Dunno if it helps but figured id try.

---

### Post by Bucky Ball on 2011-09-09
It boots from the CD, not the hard drive, as stated. Have you checked the cable to the internal hard drive? I'd say if it is all plugged fine the drive may have had it. When you are at the Ubuntu desktop  could you open System>Administration>Gparted (with the external drive unplugged so you only have the internal HD plugged in). Anything?

---

### Post by racie on 2011-09-09
> **sbr2011 said:**
> How can your pc boot if the hard drive is toast??? Is there a way to make my hard drive bootable again? I do not have a windows vista recovery CD, that's why I'm trying ubntu. I wanted to try and save the files before doing a clean install of windows.

When I plug in my external hard drive it shows up on the disk utility as 80 GB FILE SYSTEM or whatever and works fine. I was hoping the internal hard drive would be on the disk utility so I could transfer files but it isn't.
As the above user stated, you do not need a hard disk to boot anything from a CD.  In fact, I have no hard drive in my laptop... my OS is installed to a small USB drive.

If your internal hard disk does not show up in Ubuntu, then it probably is done for.  However, you could try creating a boot CD/USB of [GParted](http://gparted.sourceforge.net/).  I find that having a boot device of GParted works better than installing GParted to your OS.  If it doesn't show up in a live CD/USB of GParted, then I'd say that it's broken and suggest getting a new internal HDD.  However, if you need to, you can install an OS to your external HDD.

There are some programs that attempt to try and recover data from broken devices, but I don't know much of them or if it would help in this case.

---

### Post by ajgreeny on 2011-09-09
From the live CD use **system->administration->terminal** and run the command ```
sudo fdisk -l
``` What is the output from this, please?

---

### Post by blueridgedog on 2011-09-09
Verify the power cable and the data cable are plugged in and alternatively try a different power cable then boot on the LiveCD and post the result of the command that ajgreeny listed.  If your drive is there and registering, it will show.

If it fails to show, you can try a different data (I assume SATA) port on the motherboard.

---

### Post by CharlesA on 2011-09-09
Another thing to check would be to see if the drive is seen in the BIOS.

---

### Post by sbr2011 on 2011-09-09
System>Administration>Gparted
system->administration->terminal

I do not understand or see how or where to run the things above. On the left I see a "Launcher" bar, and across the top on the left there's File, Edit, View, Places, Help, and on the right it has the clock and options like Shut down and System Settings.

---

### Post by ajgreeny on 2011-09-09
OK, so click on the ubuntu icon top left and then type in the box "terminal" and later "gparted".  The launchers for those two applications should appears and allow you to start them.  Then follow the instructions above, in previous posts.

---

### Post by sbr2011 on 2011-09-09
I'm new to Ubuntu, how do you open a Terminal? I don't see any option to do that.

---

### Post by sbr2011 on 2011-09-09
I got something like this when I opened the terminal and typed in gparted



to run a command as administrator (user "root"), use "sudo <commando>".
see "man sudo_root" for details.

ubuntu@ubuntu:~$ gparted
Inhibit all polling failed: only uid 0 is authorized to inhibit the daemon
ubuntu@ubuntu:~$

---

### Post by sbr2011 on 2011-09-09
To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.

ubuntu@ubuntu:~$ gparted
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
fdisk [options] <disk>    change partition table
fdisk [options] -l <disk> list partition table(s)
fdisk -s <partition>      give partition size(s) in blocks

Options:
-b <size>                 sector size (512, 1024, 2048 or 4096)
-c                        switch off DOS-compatible mode
-h                        print help
-u <size>                 give sizes in sectors instead of cylinders
-v                        print version
-C <number>               specify the number of cylinders
-H <number>               specify the number of heads
-S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$

---

### Post by sbr2011 on 2011-09-09
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
fdisk [options] <disk>    change partition table
fdisk [options] -l <disk> list partition table(s)
fdisk -s <partition>      give partition size(s) in blocks

Options:
-b <size>                 sector size (512, 1024, 2048 or 4096)
-c                        switch off DOS-compatible mode
-h                        print help
-u <size>                 give sizes in sectors instead of cylinders
-v                        print version
-C <number>               specify the number of cylinders
-H <number>               specify the number of heads
-S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$



Here's what I got from sudo fdisk -1

---

### Post by josh6190 on 2011-09-09
> **sbr2011 said:**
> I'm new to Ubuntu, how do you open a Terminal? I don't see any option to do that.


Go to Applications>Accesories>Terminal

---

### Post by overdrank on 2011-09-09
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by sbr2011 on 2011-09-09
sudo fdisk -l

is that a number one or the letter L ?? I really don't know what I am doing. I typed in the #1.

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
fdisk [options] <disk>    change partition table
fdisk [options] -l <disk> list partition table(s)
fdisk -s <partition>      give partition size(s) in blocks

Options:
-b <size>                 sector size (512, 1024, 2048 or 4096)
-c                        switch off DOS-compatible mode
-h                        print help
-u <size>                 give sizes in sectors instead of cylinders
-v                        print version
-C <number>               specify the number of cylinders
-H <number>               specify the number of heads
-S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$

---

### Post by Zephilinox on 2011-09-09
Obviously if ```
sudo fdisk -1
``` doesn't work, then try the other options which are i or L (hint: it's L, lowercase, and don't forget the sudo)

---

### Post by sbr2011 on 2011-09-09
What am I trying to get it to do exactly? I really know nothing about commands. Everyone has abandoned this thread!

---

### Post by CharlesA on 2011-09-09
You are just trying to list which disks are in your computer.

the -l is a lower case L

The output should look something like this:

```
charles@Lucid:~$ sudo fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014f09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2497    20051968   83  Linux
/dev/sda2            2497        2611      916481    5  Extended
/dev/sda5            2497        2611      916480   82  Linux swap / Solaris

```

---

### Post by racie on 2011-09-09
> **sbr2011 said:**
> What am I trying to get it to do exactly? I really know nothing about commands. Everyone has abandoned this thread!

The command fdisk -l (yes, that is a lower case L, not a one... I see that no one has told you that.  :P) shows all of the partitions of all devices connected to your PC.

*edit* Oops, the above poster beat me to it.

---

### Post by sbr2011 on 2011-09-09
when I type in sudo fdisk -l it does almost nothing, like this. 

```
ubuntu@ubuntu:~$ sudo fdisk -l
 ubuntu@ubuntu:~$

```

When I type in something "invalid" I get this.

```
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
fdisk [options] <disk>    change partition table
fdisk [options] -l <disk> list partition table(s)
fdisk -s <partition>      give partition size(s) in blocks

Options:
-b <size>                 sector size (512, 1024, 2048 or 4096)
-c                        switch off DOS-compatible mode
-h                        print help
-u <size>                 give sizes in sectors instead of cylinders
-v                        print version
-C <number>               specify the number of cylinders
-H <number>               specify the number of heads
-S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$

```

Sigh. This is not looking good. I've tried l,i,j, & k. 

I don't think that my drive is unplugged because I haven't messed with it, but I will check.

---

### Post by bigpayne69 on 2011-09-09
Alright look, I know you are new to Ubuntu, but to you know how to use your computer's BIOS?

---

### Post by bigpayne69 on 2011-09-09
since you are having problems seeing you hard drive, first go into your BIOS, drive menu. verify whether or not your BIOS even sees the drive. If it displays the drive info, your problem is software. If it says unknown, then you have a hardware problem.

---

### Post by CharlesA on 2011-09-09
I have a feeling the drive ate it, if it's not a laptop, you can try putting it in another machine and seeing if it is seen.

---

### Post by sbr2011 on 2011-09-09
I don't know if I can put my HD in this PC I'm typing on now because it's older, it might be IDE. It also might be some kind of battery issue. I don't think I can post an outside link but I was reading a thread where a guy was going around and around with the same PC I have (Dell Inspiron) that could boot from a CD but was not reading SATA hard disks that he knew worked b/c they worked in other machines. 

I am not all that familiar with BIOS settings, or what to set them to. How do I know if the BIOS is reading the drive?
Does it mean my HD is installed/recognized in BIOS if I get the error message

No boot device available
SATA 0: installed
SATA 1: installed
SATA 4: none
SATA 5: none

---

### Post by Bucky Ball on 2011-09-10
Looks like you have two hard drives, SATA 0 and 1 plugged in. Don't know if this is any guarantee both are actually working, but they seem to be plugged in.

Now, do what was mentioned before, take it slow: in the Ubuntu desktop type in 'terminal'. The terminal launcher should pop up. Click it to open the terminal. In the terminal paste this:

```
sudo blkid
```That will list all drives and all partitions on them. Copy that output and paste it back here. You should see sda* and sdb* if there are two drives in there (replace the * with a number). If that is the case your in business, if not, hmm.

If the external drive works you could take the internal drive out and put it in the external case and see if you get any life.

---

### Post by sbr2011 on 2011-09-11
There are slots for two hard drives but I definitely only have  one in there, which is SATA. I don't know enough about changing BIOS  settings, or I would stick my hard  drive in another PC but all of the computers in my reach are PATA/IDE,  and my external enclosure is for PATA/IDE also, so I am going to order a  SATA enclosure and wait for it to arrive. 

Thanks for all your help, I don't consider this "solved" yet, depending what happens I may have more ubuntu questions.

---

### Post by Bucky Ball on 2011-09-11
You didn't have your external drive plugged in at the same time?

---

### Post by sbr2011 on 2011-09-14
Right, the internal drive was the only one connected, as I leave the external drive disconnected until I need it for something. My enclosure from new egg should be delivered today! Keeping my fingers crossed.

---

### Post by sbr2011 on 2011-09-15
I put the drive into the external enclosure, it powers up and hums, sounds like it's spinning in there. But I can't view/access/read it from "My Computer" in windows xp. My working external hd shows up as drive J on this pc.

I'm afraid that if the Ubuntu live CD wasn't recognizing it as an interal hd then putting it into an enclosure won't make much difference either, but is there a chance that I could do something using Ubuntu even if Windows doesn't recognize it?

---

### Post by Bucky Ball on 2011-09-15
As for the old internal drive, putting it in an external enclosure that you know to work with another drive will prove everything. If it doesn't work, the drive is dead as the other drive is working perfectly, OR, the *internal* cable being used from motherboard to the hard drive is dodgey OR socket on the mother board is screwed.

;)

---

### Post by mycroft on 2011-09-15
Might I suggest having a look at [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")?

It may look complicated at first, but it's really not that bad. Basically you would be using something called 'ddrescue' to attempt to clone as much data as possible onto a disk image. You would then extract this disk image to a healthy disk and try to restore your data from there. Less intrusive than trying to run file system correcting applications on the damaged disk.

The downside is that it's a somewhat lengthy process - reading the disk, trying each bad sector thrice followed up by as many reverse direction read attempts could easily take weeks. And even then there is no guarantee of how much data, if any, you would be able to eventually restore from the extracted disk image.

On the bright side, 'ddrescue' also incorporates a log, which allows you to interrupt and resume the read operations whenever you want to.

---

### Post by jockyburns on 2011-09-15
A few weeks ago, my HDD stopped working. I was able to download Ubuntu 11.04 to a usb stick on my partners computer and boot mine from that. The HDD doesn't even register at all, so I assume it's either dead or so corrupted as to be beyond any help. I did look on the Seagate website for help, but some of the advice seems so complicated I wouldn't even know where to start. Result? I've bought a new HDD and have now installed Ubuntu 11.04 to that. My original HDD spins up when powered but that's all. Bios doesn't detect it. Perhaps some company out there could possibly recover your data, but at what price??

---

### Post by sbr2011 on 2011-09-15
I see what you're saying Bucky Ball, but I am using two different enclosures for my hard drives since they aren't compatible. The one that works is PATA/IDE and the one I'm having trouble reading is SATA.

---

