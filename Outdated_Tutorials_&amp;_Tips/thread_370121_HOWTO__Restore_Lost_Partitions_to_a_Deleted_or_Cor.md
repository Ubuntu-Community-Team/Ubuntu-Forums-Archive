---
title: "HOWTO:  Restore Lost Partitions to a Deleted or Corrupt Partition Table"
date: 2007-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by JohnPhys on 2007-02-25
This HOWTO will tell you how to recover your lost partitions if the partition data on your hard drive got wiped by some malicious program (windows in my case).  If the new/incorrect partitions have been formatted, then you've probably lost data.  If all that got wiped was the partition table, then this should help you recover all of your data!  I searched in the Tutorials and Tips forum and couldn't find anything quite like this, so I thought I'd write it up.  If someone knows of a better thread, point me to it! :)

I have tested this on a Dapper install using an Edgy LiveCD.  

All that is needed is an Edgy LiveCD, a cd drive you can boot from, and a working internet connection.  A dapper cd would most likely work, but I have not tested it.
WARNING:  This HOWTO is most likely to be used at your own risk, as I'm not sure if I'll be able to test it on future distributions (nor do I feel like destroying my partition info to do so).

1.)  Enable your computer to boot from the cd drive.  You may have to enter your computer's BIOS to do this.

2.)  Boot from the Edgy LiveCD.

3.)  Assuming the LiveCD loaded just fine, enable the universe and multiverse repositories by System -> Administration -> Software Properties and checking the appropriate boxes.

4.)  Open up a terminal (Applications -> Accessories -> Terminal), and type 

```
sudo apt-get install gpart
```

Yes, gpart, not gparted.  gpart is a program that will scan your drive for existing partitions, and output the cylinders that they are on.

5.)  In the terminal, run

```
sudo gpart /dev/hda
``` or substitute whichever drive you are looking at (hdc, sda, etc.) and note the output.  Mine looks like:

```
 sudo gpart /dev/hdc

Begin scan...
Possible partition(Linux ext2), size(149660mb), offset(0mb)
Possible extended partition at offset(149660mb)
   Possible partition(Linux swap), size(2965mb), offset(149660mb)
End scan.

Checking partitions...
Partition(Linux ext2 filesystem): primary
Partition(Linux swap or Solaris/x86): primary
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 149660mb #s(306504072) s(63-306504134)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(19078/254/63)r

Primary partition(2)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 2965mb #s(6072504) s(306504198-312576701)
   chs:  (1023/254/63)-(1023/254/63)d (19079/1/1)-(19456/254/60)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


```

The "size" line is telling you first the number of mb of the partition, then the number of sectors (#s) and then the actual sectors that the partition is on (s).  The last set of numbers (actual sectors the partition is on) is what we want.  Write those down!  With those in hand,

5.a) Now we have to restore the partition table.  We'll use parted.

```
sudo parted /dev/hda
``` 

again substituting the drive you're interested in for hda.

You should be at a prompt that looks like 

```
(parted)
```

5.b)  At that prompt, type 

```
unit s
```

to make sure that parted is using units of sectors.


5.c)  Just in case we want to undo any changes, type "print", and be sure to write down the start and end sectors of all of the partitions on the disk!  NOTE:  The reason you don't want to use this method to get the start/end sectors of the partitions you're trying to restore is that parted just reads the partition table on the disk itself, even if it is incorrect or corrupt.  If parted throws up errors about nonexisting partitions or a corrupt table, then there is no need for this step.

6.)  Now we actually restore the partitions!  Still at the (parted) prompt, type

```
rescue
```, and you will be prompted for the start and end sectors of the partition you want to rescue.  In my example, these numbers would be 63 for the start and 306504134 for the end of the first partition.

7.)  Repeat step 6 for all partitions that need to be recued.

8.)  ```
quit
``` to exit out of parted.

That's it!  You should have access to all of your old partitions, and you can check this by mounting the various partitions in the live cd.

9.)  If you find out you messed with the partition table on the wrong disk, and you followed step 5.c), you can use steps 6-8 to restore the partition table you just wiped, using the numbers you wrote down from the print command in parted rather than the output from gpart.

NOTE:  If your partition table was wiped, it's quite possible (as it was in my case) that your MBR got killed as well, and you'll need to restore grub.  You can try starting here: [How to install Grub from a live Ubuntu CD]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub"), though I'll admit the first method failed for me.  If the admins let this HOWTO through, I'll add on what I did to get GRUB back.

Please post any comments/questions, and let me know if this is helpful!

---

### Post by jan on 2007-03-11
Hi,

nice HOWTO - i just had to use command "rescue" since no "restore" existed. Seemed to work the same way.

However it seems whole my GRUB got wiped so it was good for nothing ;).

---

### Post by JohnPhys on 2007-03-11
Well, at least you have your partitions back now (assuming they were gone before!).  Reinstalling grub shouldn't be *too* much of a hassle.  There's a link at the end of my original post that tells you how to reinstall grub.  If that doesn't work, I can tell you how I managed to do it (probably not the shortest/easiest way, but it worked).

Thanks for catching the rescue/restore bit, I could have sworn I double checked that!  

EDIT:  I've fixed the command now, thanks again!

---

### Post by geoisonfire on 2007-03-27
plz help me!!!!
My  partition table was gone since I mistakenly detected my partition during the re-installation of xp, However, good thing was i stop the next step, (didn't format my hard disk), but now I can't boot to xp anymore and my Partition table is gone. btw, I just detected ubuntu 2 days before that, so I can only access ubuntu using live cd. 

Here's what it looked like after I used sudo gpart /dev/hda  

[COLOR="Red"]ubuntu@ubuntu:~$ sudo gpart /dev/hda

** Error: invalid extended ptbl found at sector(53657100).

Begin scan...
Possible partition(Windows NT/W2K FS), size(18002mb), offset(0mb)
Possible extended partition at offset(18002mb)
   Possible partition(Windows NT/W2K FS), size(8197mb), offset(18002mb)
   Possible partition(Windows NT/W2K FS), size(21799mb), offset(26199mb)
   Possible partition(Windows NT/W2K FS), size(10001mb), offset(47998mb)
   Possible partition(Windows NT/W2K FS), size(18308mb), offset(58000mb)
End scan.

Checking partitions...

* Warning: more than one extended partition: 2.
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
   Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): logical 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): invalid 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): invalid 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 18002mb #s(36869104) s(63-36869166)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(2294/254/55)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 29996mb #s(61432560) s(36869175-98301734)
   chs:  (1023/254/63)-(1023/254/63)d (2295/0/1)-(6118/254/63)r

Primary partition(3)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 18308mb #s(37495640) s(118784673-156280312)
   chs:  (1023/254/63)-(1023/254/63)d (7394/1/1)-(9727/254/56)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r[/COLOR]

My actual partition table using [COLOR="SandyBrown"]fdisk /dev/hda[/COLOR]
[COLOR="Red"]
Device Boot Start End Blocks Id System
/dev/hda1 1 2295 18433024 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2 3341 9728 51311610 f W95 Ext'd (LBA)
/dev/hda3 207176 8283 549881402+ ff BBT
Partition 3 does not end on cylinder boundary.
/dev/hda5 3341 6119 22322286 7 HPFS/NTFS
/dev/hda6 207176 8283 549881402+ ff BBT[/COLOR]

What do i need to do now!!!
I had two primary partitions, I want my first one back ( 18G), the second one(8G) is the one I created in order to install x86 osx , however, my partition was gone even before I get chance to try that.
I have really important files in my logical partitions, What do i need to do now!

I am almost crying now, plz help me to get my partition table back, as well as all my files. thx

---

### Post by JohnPhys on 2007-03-28
Where are you getting the "testdisk" info from?

Also, in linux, run

```

sudo fdisk -l /dev/hda

```

and post the output, please.

---

### Post by geoisonfire on 2007-03-28
"Where are you getting the "testdisk" info from?"
Sorry, I think all i did was just using fdisk /dev/hda
and I get the second result in my post.



I believe [COLOR="Red"]never[/COLOR] I used testdisk, all i used is [COLOR="Red"]gpart[/COLOR] and [COLOR="Red"]fdisk[/COLOR].
(I will correct my original post soon, thx a lot for mention that!)

After I type sudo fdisk -l /dev/hda
I get this 

[COLOR="Red"]Device Boot Start End Blocks Id System
/dev/hda1 1 2295 18433024 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2 3341 9728 51311610 f W95 Ext'd (LBA)
/dev/hda3 207176 8283 549881402+ ff BBT
Partition 3 does not end on cylinder boundary.
/dev/hda5 3341 6119 22322286 7 HPFS/NTFS
/dev/hda6 207176 8283 549881402+ ff BBT[/COLOR]

It seems to be kinda weird although I don't understand it.
Btw, after I type sudo gpart /dev/hda
It give me 

[COLOR="Teal"]Begin scan...
Possible partition(Windows NT/W2K FS), size(18002mb), offset(0mb)
Possible extended partition at offset(18002mb)
Possible partition(Windows NT/W2K FS), size(8197mb), offset(18002mb)
Possible partition(Windows NT/W2K FS), size(21799mb), offset(26199mb)
Possible partition(Windows NT/W2K FS), size(10001mb), offset(47998mb)
Possible partition(Windows NT/W2K FS), size(18308mb), offset(58000mb)
End scan.
[/COLOR]
Then Checking partitions... and other stuff like I post before, all i know is that these 5 possible partitions has the correct size as my partitons in xp and they are listed even in the right order. I hope I can restore these partitions back.
Thx for your help!

---

### Post by geoisonfire on 2007-04-01
Thanks for your help anyway, JohnPhys. I got all my partitions back and lost none of my data. Gpart was not the only tool that I used, but still it did help me a lot!:guitar: :lolflag:

---

### Post by elmo541992 on 2007-08-14
i need help...

i know my mbt and partition table is gone, but im having trouble getting it back.  i do sudo fdisk -l /dev/sdb, and i get this:
```
max@max-desktop:~$ sudo fdisk -l /dev/sdb 

Disk /dev/sdb: 41.1 GB, 41121316864 bytes 
255 heads, 63 sectors/track, 4999 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

Disk /dev/sdb doesn't contain a valid partition table 
```
this info i know is correct.  i also know that the layout of my partitions are something like this:

~38gb ext3
~1.5gb swap

but, when i use gpart, it detects the swap drive, but not the ext3 part.  i can still use this info it spit out at me to assume the sectors of the ext3 part.  so then i continue to parted.   heres what i get:
```
max@max-desktop:~$ sudo parted /dev/sdb

GNU Parted 1.7.1

Using /dev/sdb

Welcome to GNU Parted! Type 'help' to view a list of commands.

(parted) unit s                                                           

(parted) rescue

Error: Unable to open /dev/sdb - unrecognised disk label.                 

(parted)
```
i get the same error when i tell it to print, too.  how can i get around this???  and so you know, im 64-bit, and i used the feisty install on another hard drive.  also, if theres a way to just get files off of it, that would be fine too.

---

### Post by mafiastyle on 2007-11-09
hello!
I have some problems with my partition table. I think it is corrupt. when I check it from windows everything appears to be ok, but when I use gparted it shows i have no partition on my sata drive. when I use gpart it shows me the info I need. Please advise me what to do so I can restore my partitions.
Thanks !

---

### Post by JohnPhys on 2007-11-10
Can you mount any of the partitions on your sata drive in linux?  Please give some more info, including your partition & drive setup.

---

### Post by uzi09 on 2009-01-06
Hi.

Thanks for the much needed how to. One question though that you didn't seem to talk much about. You used a live cd to do all this in it. Is it absolutely necessairy to use a live cd? I can see how for those who don't even have access to the computer will need to do this, however for those that have access to the computer, but the partition table is just messed up, can we do it from the system itself?

I tried it from the system itself and got some results which I thought looked a little funny:
```
Begin scan...
Possible partition(DOS FAT), size(39mb), offset(0mb)
Possible extended partition at offset(39mb)
   Possible partition(Linux ext2), size(14307mb), offset(39mb)
   Possible partition(Linux ext2), size(12527mb), offset(14347mb)
   Possible partition(Linux ext2), size(42915mb), offset(26874mb)
Possible extended partition at offset(69790mb)
   Possible partition(Linux swap), size(2008mb), offset(69790mb)

* Warning: short read near sector(153356301), 64512 bytes instead of 66048. Skipping...
End scan.

Checking partitions...

* Warning: more than one extended partition: 2.
Partition(Primary 'big' DOS (> 32MB)): primary
   Partition(Linux ext2 filesystem): invalid logical
   Partition(Linux ext2 filesystem): logical
   Partition(Linux ext2 filesystem): logical
Partition(Linux swap or Solaris/x86): invalid
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 006(0x06)(Primary 'big' DOS (> 32MB))
   size: 39mb #s(80262) s(63-80324)
   chs:  (0/1/1)-(4/254/63)d (0/1/1)-(4/254/63)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 69750mb #s(142849980) s(80325-142930304)
   chs:  (5/0/1)-(1023/254/63)d (5/0/1)-(8896/254/63)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```


This is what it should look like:
```

Possible partition(DOS FAT), size(39mb), offset(0mb) - [COLOR="Red"]**Dell Restore**[/COLOR]
Possible extended partition at offset(39mb)
   Possible partition(Linux ext2), size(14307mb), offset(39mb) - [COLOR="Red"]**Additional OS (Linux)**[/COLOR]
   Possible partition(Linux ext2), size(12527mb), offset(14347mb) - [COLOR="Red"]**Main OS (Ubuntu)**[/COLOR]
   Possible partition(Linux ext2), size(42915mb), offset(26874mb) - [COLOR="Red"]**Home Partition**[/COLOR]
Possible extended partition at offset(69790mb) - [COLOR="Red"]**I don't know why the heck this is an extended partition. I don't recall putting the swap on a separate extended partition.**[/COLOR]
   Possible partition(Linux swap), size(2008mb), offset(69790mb) - [COLOR="Red"]**Swap**[/COLOR]

```

I tried to add Windows, but didn't have room or something. I tried getting rid of the *additional OS (Linux) *and install Windows over it, but Windows just gave some random error and wouldn't install.

At the moment, gparted and the Windows CD both see the whole HDD as one chunk without any data on there.

Luckly, Grub has been okay and the data all seems to be available on the HDD since I can access my *main OS* and my *home* partitions. I'm not too sure about the *additional OS (Linux)* though.

Any help is much appreciated!

---

### Post by smokey_58au on 2009-01-15
Just want to say a big thank you for this guide JohnPhys.  My son deleted his swap partition (by accident of course) :confused:  and using the Intrepid Live CD and following your guide was able to recover his complete (Intrepid) system.  He needed to do both steps - rescue the partition and restore grub - and it worked exactly as you described.  Well done and thanks.

---

### Post by uzi09 on 2009-01-23
> **uzi09 said:**
> Hi.

Thanks for the much needed how to. One question though that you didn't seem to talk much about. You used a live cd to do all this in it. Is it absolutely necessairy to use a live cd? I can see how for those who don't even have access to the computer will need to do this, however for those that have access to the computer, but the partition table is just messed up, can we do it from the system itself?

I tried it from the system itself and got some results which I thought looked a little funny:
```
Begin scan...
Possible partition(DOS FAT), size(39mb), offset(0mb)
Possible extended partition at offset(39mb)
   Possible partition(Linux ext2), size(14307mb), offset(39mb)
   Possible partition(Linux ext2), size(12527mb), offset(14347mb)
   Possible partition(Linux ext2), size(42915mb), offset(26874mb)
Possible extended partition at offset(69790mb)
   Possible partition(Linux swap), size(2008mb), offset(69790mb)

* Warning: short read near sector(153356301), 64512 bytes instead of 66048. Skipping...
End scan.

Checking partitions...

* Warning: more than one extended partition: 2.
Partition(Primary 'big' DOS (> 32MB)): primary
   Partition(Linux ext2 filesystem): invalid logical
   Partition(Linux ext2 filesystem): logical
   Partition(Linux ext2 filesystem): logical
Partition(Linux swap or Solaris/x86): invalid
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 006(0x06)(Primary 'big' DOS (> 32MB))
   size: 39mb #s(80262) s(63-80324)
   chs:  (0/1/1)-(4/254/63)d (0/1/1)-(4/254/63)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 69750mb #s(142849980) s(80325-142930304)
   chs:  (5/0/1)-(1023/254/63)d (5/0/1)-(8896/254/63)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```


This is what it should look like:
```

Possible partition(DOS FAT), size(39mb), offset(0mb) - [COLOR="Red"]**Dell Restore**[/COLOR]
Possible extended partition at offset(39mb)
   Possible partition(Linux ext2), size(14307mb), offset(39mb) - [COLOR="Red"]**Additional OS (Linux)**[/COLOR]
   Possible partition(Linux ext2), size(12527mb), offset(14347mb) - [COLOR="Red"]**Main OS (Ubuntu)**[/COLOR]
   Possible partition(Linux ext2), size(42915mb), offset(26874mb) - [COLOR="Red"]**Home Partition**[/COLOR]
Possible extended partition at offset(69790mb) - [COLOR="Red"]**I don't know why the heck this is an extended partition. I don't recall putting the swap on a separate extended partition.**[/COLOR]
   Possible partition(Linux swap), size(2008mb), offset(69790mb) - [COLOR="Red"]**Swap**[/COLOR]

```

I tried to add Windows, but didn't have room or something. I tried getting rid of the *additional OS (Linux) *and install Windows over it, but Windows just gave some random error and wouldn't install.

At the moment, gparted and the Windows CD both see the whole HDD as one chunk without any data on there.

Luckly, Grub has been okay and the data all seems to be available on the HDD since I can access my *main OS* and my *home* partitions. I'm not too sure about the *additional OS (Linux)* though.

Any help is much appreciated!


**SOLVED:**

Sorry I didn't post this up earlier.

Searching through the web and various forums I saw someone suggest [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). It was really idiot proof to use, almost like a Windows wizard :)
Fixed things right up.

Hope it helps some of you out.

---

