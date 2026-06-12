---
title: "Cannot see the computer's hard drive through Disk Utility or GParted"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by Aabicus_Finch on 2014-01-21
I have an old tower, a Dell Inspiron with a Vista sticker, that I'm hoping to turn into a backup storage computer, however when I crank it up, it warns me that the hard drive selfchecker has  detected a possible problem with the hard drive. Going forward takes me  to the Dell splash page and the Windows XP (?) splash page before it  tells me Windows didn't shut down properly, would I like to start in safe  mode, safe mode with network, safe mode with command prompt, last known  working settings, or normally? All do the same thing; load for a while  then loop back to the hard drive warning. Doing a Dell self-check with f12  fails because it cant find the partition. There is nothing in the CD  drives.

In an attempt to reach a working desktop, I have booted Ubuntu from a USB stick and it works fine. I followed these steps [http://askubuntu.com/questions/317241/can-i-use-ubuntu-to-diagnose-hard-drive-or-ram-problems-in-windows](http://askubuntu.com/questions/317241/can-i-use-ubuntu-to-diagnose-hard-drive-or-ram-problems-in-windows) but according to disk utility there is nothing under local storage. There are just no options except peripheral devices, i.e. the ones on the thumb drive. I'm not sure what I should do next to determine what's preventing the computer's hard drive from being accessible.

I asked this question on the [Wikipedia Computing Reference Desk ]("http://en.wikipedia.org/wiki/Wikipedia:Reference_desk/Computing#How_to_find_out_if_this_tower_has_an_OS.3F")and was recommended here, if you'd like more information. Thank you for any and all assistance!

---

### Post by Bashing-om on 2014-01-21
Aabicus_Finch; Hi ! Welcome to the forum .

There being XP installed, and a vista sticker on the box, I would think that there are existing problems and at some point someone has "tried" to install the prior version XP.
I see 2 options:
1. Obtain a Window's repair disk and run Windows' file system checks.
2. Forget Windows, and try and overwrite the disk with an install of ubuntu.

If there are problems installing ubuntu onto that hard drive, zero out the hard disk (say with dd or other tools) and try to install ubuntu once more.

From the indication, possible that the initial "superblock" for the file system is corrupt. Thus, in this instance, a valid file system can not be determined or accessed. A disk wipe and a new file system might correct this. Within ubuntu there are means to "spare" off this superblock. I do not know if that is possible in Windows' world.

It may turn out there are defects and/or mechanical defects -> toss the disk ........

[INDENT][INDENT]just my little bit
[INDENT][INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Aabicus_Finch on 2014-01-21
Yeah, all signs are pointing to something being wrong with the hard drive. Regarding Recovery disks, there's nothing important on the hard drive that I care about saving, so a factory restore or something would be acceptable as well. (I thought it was alt-f3 to do those but alt-f3 didn't work.) So far I can't get the computer to accept any commands except f2 and f12 though.

also, if I install Ubuntu onto the computer (so far I've been hitting the 'try' button), will it wipe the faulty XP OS that is currently on there?

---

### Post by sudodus on 2014-01-21
Wiping the first megabyte (overwriting with zeros) is usually enough to make it possible to re-partition and re-format a mass storage device (HDD or pendrive or SSD). If it does not work, there might be physical defects (bad sectors or some bad electric or electronic component).

When Ubuntu is booted from the USB-stick, you can download ***mkusb*** and use it to wipe the first megabyte with the command (in the same directory where you have downloaded the mkusb shell-script file

Make the file executable with

```
chmod ugo+x mkusb
```

and run it with

```
sudo ./mkusb wipe-1
```

See this [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by sudodus on 2014-01-21
> **Aabicus_Finch said:**
> ... also, if I install Ubuntu onto the computer (so far I've been hitting the 'try' button), will it wipe the faulty XP OS that is currently on there?

You can keep or overwrite the current operating system. In this case I suggest that you overwrite it and get a clean Ubuntu system.

But before installation, you can also consider other Ubuntu flavours with lighter desktop environments, that will make the computer more responsive and make it easier to get good playback of video, for example Xubuntu or Lubuntu.

---

### Post by Aabicus_Finch on 2014-01-21
> **sudodus said:**
> Wiping the first megabyte (overwriting with zeros) is usually enough to make it possible to re-partition and re-format a mass storage device (HDD or pendrive or SSD). If it does not work, there might be physical defects (bad sectors or some bad electric or electronic component).

When Ubuntu is booted from the USB-stick, you can download ***mkusb*** and use it to wipe the first megabyte with the command (in the same directory where you have downloaded the mkusb shell-script file

```
sudo ./mkusb wipe-1
```

See this [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

So, before I begin I want to ensure I do everything right:

Step1: Download mkusb from here: [http://phillw.net/isos/one-button-installer/scripts/](http://phillw.net/isos/one-button-installer/scripts/) (is that the shell-script file?) and put it on my computer somewhere.
Step2: use terminal to locate the downloaded mkusb on my USB. I'm not sure how to do that but I can look it up, I remember vaguely working with terminal in my C class from college.
Step3: Type the above quoted code into the terminal
Step4: Sit back and wait as it wipes the first megabyte?

Will that be enough to restart the computer and maybe have it boot up correctly?

---

### Post by sudodus on 2014-01-21
Typically, the downloaded files go to the Downloads directory, but you can select to put it elsewhere, or you can move it after downloading.

Start a terminal window with the hotkey combination ***ctrl + alt + t***

It wipes one megabyte in a second or two, so you won't sit back long ;-)

With the computer booted from the USB pendrive, you will probably *not* need any reboot. After wiping the first megabyte, you can run gparted and start by finding the device (drive), and then select the pull-down menu ***Device*** to create a partition table. After that you can make new partitions (and file systems).

If you have problems, it might help to reboot (into the USB pendrive again).

---

### Post by Aabicus_Finch on 2014-01-21
Sadly I am going to need more exact instructions. So here is the code in terminal i used to reach the mkusb:

ubuntu@ubuntu:~$ cd ~/Downloads
ubuntu@ubuntu:~/Downloads$ ls
mkusb
ubuntu@ubuntu:~/Downloads$ xdg-open mkusb

Upon which it opens in what looks kinda like emacs. But entering your doce line grants the following:

ubuntu@ubuntu:~/Downloads$ sudo ./mkusb wipe-1
sudo: ./mkusb: command not found

What error did I make? And am I supposed to have a second usb for this process, that isnt the one im booting ubuntu from?

Apologies for being slow...I've fixed like two dozen other problems at the office in the past two days so I'm a bit frazzled in general...

---

### Post by sudodus on 2014-01-22
Sorry, you should make the file executable too

```
chmod ugo+x mkusb
```

and it will run with

```
sudo ./mkusb wipe-1
```

or use bash to call it (if you do not want to make it executable)

```
sudo bash mkusb wipe-1
```

---

### Post by Aabicus_Finch on 2014-01-23
It asks if I want to wipe the USB device?

Should I be using a USB device other than the one I'm booting Ubuntu from?

---

### Post by sudodus on 2014-01-24
mkusb is mainly aiming at USB drives, but if you ***toggle USB-only*** with ***u*** (and the Enter key) you will be 'allowed' to aim at internal drives too. This is a security precaution, to help avoid erasing internal drives by mistake.

---

### Post by Aabicus_Finch on 2014-01-24
At what point in the process do I toggle USB_only with u? I keep getting "command not found" when I try to input it into terminal during the process.

---

### Post by sudodus on 2014-01-25
In a terminal window, change directory until you are in the same directory as the shell-script file **mkusb**. Then run this command

```
sudo bash mkusb wipe-1
```

When will it reply [FONT=courier new]command not found[/FONT]? A typical dialogue should look like this (different high-lighting because I don't know how to get inverse video with the Ubuntu Forums editor)

```
sudo bash mkusb wipe-1
[sudo] password for sudodus: 
Wipe the first megabyte (MibiByte) ... :
Do you want to wipe the USB device? (y/n)
y
[COLOR=#ff0000]***  WARNING: the device will be completely overwritten      ***
     Use the info in the xterm window (less /tmp/help-mkusb.txt)
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************[/COLOR]
 
Model: ATA SAMSUNG HD322HJ (scsi)    Disk /dev/sda: 320GB    
Model: ATA OCZ-AGILITY3 (scsi)    Disk /dev/sdb: 60.0GB    
Model: ATA WDC WD10EARS-00Y (scsi)    Disk /dev/sdc: 1000GB    
Model: SanDisk Cruzer Blade (scsi)    Disk /dev/sdd: 4005MB    
Live drive: /dev/sdb
USB drive:  /dev/sdd: 4004 MB, 4004511744 bytes
 
[COLOR=#ff0000]---> 1: wipe device SanDisk Cruzer Blade (scsi) Disk /dev/sdd: 4005MB[/COLOR]
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
u
[COLOR=#ff0000]---> 1: wipe device ATA SAMSUNG HD322HJ (scsi) Disk /dev/sda: 320GB[/COLOR]
#       could not unmount /dev/sdc because file system on device is busy
     2: wipe device SanDisk Cruzer Blade (scsi) Disk /dev/sdd: 4005MB
Select another device with (+/-) or the number of the list item.
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
2
     1: wipe device ATA SAMSUNG HD322HJ (scsi) Disk /dev/sda: 320GB
#       could not unmount /dev/sdc because file system on device is busy
[COLOR=#ff0000]---> 2: wipe device SanDisk Cruzer Blade (scsi) Disk /dev/sdd: 4005MB[/COLOR]
Select another device with (+/-) or the number of the list item.
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
g
2: wipe device SanDisk Cruzer Blade (scsi) Disk /dev/sdd: 4005MB 
Do you really want to wipe and install to this device? (y/n)
y
 
Wiping the first megabyte (MibiByte) of /dev/sdd ... :
< /dev/zero pv  | dd bs=4096 count=256 of=/dev/sdd
1.03MB 0:00:00 [ 263MB/s] [ <=>                                                                         ]
256+0 records in
256+0 records out
1048576 bytes (1.0 MB) copied, 0.272458 s, 3.8 MB/s
Syncing the device ...
sudodus@ssd-grund ~/bin $

```

---

### Post by Aabicus_Finch on 2014-01-25
Here's a transcript of the conversation with terminal. I attempted to otggle USB-only after each command. I suspect I'm using the 'u' command incorrectly.

Also thank you for so much of your time, is there a Reputation button or something of that nature I could reward you by?

```
ubuntu@ubuntu:~$ u
u: command not found
ubuntu@ubuntu:~$ cd ~/Downloads
ubuntu@ubuntu:~/Downloads$ ls
mkusb
ubuntu@ubuntu:~/Downloads$ u
u: command not found
ubuntu@ubuntu:~/Downloads$ xdg-open mkusb
ubuntu@ubuntu:~/Downloads$ u
u: command not found
ubuntu@ubuntu:~/Downloads$ chmod ugo+x mkusb
ubuntu@ubuntu:~/Downloads$ u
u: command not found
ubuntu@ubuntu:~/Downloads$ sudo ./mkusb wipe-1
Wipe the first megabyte (MibiByte) ... :
The program 'pv' can show the progress during the installation.
Do you want to install it? (y/N)n
Do you want to wipe the USB device? (y/n)

```[/QUOTE]

---

### Post by sudodus on 2014-01-25
You need to answer y (yes) to the last question (and later toggle USB-only)

```
Do you want to wipe the USB device? (y/n)
y
```

---

### Post by Aabicus_Finch on 2014-01-25
The reason I'm hesitant to answer 'yes' is because I am running Ubuntu off of a USB, its the reason the computer currently has a working OS. You're sure that answering 'yes' will not wipe the USB currently containing my OS?

---

### Post by sudodus on 2014-01-25
Yes. I made the script. There will be more questions that wants answers before anything will be wiped. See the example in post #13

---

### Post by Aabicus_Finch on 2014-01-25
So when I toggle USB only it stops finding 'target device." Might have something to do with why other basic procedures have been unable to access this computer's hard drive.

```
ubuntu@ubuntu:~/Downloads$ sudo ./mkusb wipe-1
Wipe the first megabyte (MibiByte) ... :
The program 'pv' can show the progress during the installation.
Do you want to install it? (y/N)n
Do you want to wipe the USB device? (y/n)
y
***  WARNING: the device will be completely overwritten      ***
     Use the info in the xterm window (less /tmp/help-mkusb.txt)
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************
 
Model: VBTM Store 'n' Go (scsi)    Disk /dev/sda: 2063MB    
Live drive: /dev
USB drive:  /dev/sda: 2062 MB, 2062548992 bytes
 
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
No USB target device available. Toggle USB-only?
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
u
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
No target device available
ubuntu@ubuntu:~/Downloads$ 
```[/QUOTE]

---

### Post by sudodus on 2014-01-25
I think you have found a bug in mkusb. At least it presents the result in an ugly way.

Is there another device (a HDD) that should be found?

What output do you get from the following two commands?

```
sudo fdisk -lu
```
```
sudo parted -l
```

*Edit*: I have fixed this bug for some new cases, when booted from an Ubuntu install drive, and uploaded ***mkusb*** version 7 to the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by Aabicus_Finch on 2014-01-25
```
ubuntu@ubuntu:~/Downloads$ sudo fdisk -lu

Disk /dev/sda: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x656da90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     4028415     2014192    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~/Downloads$ ^C


```

```
ubuntu@ubuntu:~/Downloads$ sudo parted -l
Model: VBTM Store 'n' Go (scsi)
Disk /dev/sda: 2063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  2063MB  2063MB  primary  fat16        boot, lba


ubuntu@ubuntu:~/Downloads$ ^C
ubuntu@ubuntu:~/Downloads$ 


```

---

### Post by Aabicus_Finch on 2014-01-25
(pasted the wrong codew a second ago, fixed

---

### Post by sudodus on 2014-01-25
No, ***parted*** and ***fdisk*** find only the pendrive, from which you boot the system. Is there a HDD, that is connected in a correct way? (I would guess so)

Even after the kind of wiping I suggest, it should be found as a device (typically **/dev/sda**, while the pendrive would be **/dev/sdb**)

---

### Post by sudodus on 2014-01-25
You need to create a good connection to the internal drive (the HDD), so that it is 'seen' by these programs. Otherwise we cannot do anything with it.

---

### Post by Aabicus_Finch on 2014-01-25
Okay, I'm not sure how I'll do that, but I'll do some research online. I'll revive this thread if I'm ever able to reconnect to the HDD so we can actually see and affect it. (I'd appreciate any advice you may have for doing this, but I understand its a completely deparate problem from the one this topic is dedicated to)

Thank you so much for your help :)

---

### Post by sudodus on 2014-01-25
If we are lucky it is a simple electrical problem. Connect and reconnect the cables to the HDD, maybe connect it to another port if possible.

---

### Post by slooksterpsv on 2014-01-25
A few questions: 
Is the computer running Vista or XP?
Have you setup any sort of RAID environment?
If you can boot into Windows, what did the check disk (scandisk for XP) report?
If you can get into Windows, could you take a screenshot of Disk Management via diskmgmt.msc ?

---

### Post by Aabicus_Finch on 2014-01-25
I reconnected the power cables to the HDD but the problems weren't fixed, the computer still can't boot from it. mkusb gives me the same terminal conversation that terminates at the same time.

Is the computer running Vista or XP? It has a Vista sticker but I get an XP splash screen when (unsuccessfully) trying to start up
Have you setup any sort of RAID environment? Probably not...
If you can boot into Windows, what did the check disk (scandisk for XP) report? I cannot; no partition or boot found (unless I plug in the Ubuntu USB that I'm currently accessing the internet from)
If you can get into Windows, could you take a screenshot of Disk Management via diskmgmt.msc ? The best I could do is a screenshot of the black screen informing me no partition was found. Would that help?

---

### Post by sudodus on 2014-01-25
Can you try to connect the HDD to another computer? (If you can find/borrow one with the same kind of HDDs (IDE-PATA or SATA))

That way we can try to find out if the damage is in the HDD or the computer. An alternative is to connect another HDD to your computer and check if it is recognized.

---

### Post by slooksterpsv on 2014-01-25
Does the BIOS even recognize the HDD if not, may be a bad HDD. It happens, sadly =(

---

### Post by Aabicus_Finch on 2014-02-03
All right, I redownloaded mkusb from the provided url, and got the following. I'll just paste the whole code box from Terminal.

```
ubuntu@ubuntu:~$ cd ~/Downloads
ubuntu@ubuntu:~/Downloads$ ls
mkusb
ubuntu@ubuntu:~/Downloads$ xdg-open mkusb
ubuntu@ubuntu:~/Downloads$ chmod ugo+x mkusb
ubuntu@ubuntu:~/Downloads$ sudo ./mkusb wipe-1
Wipe the first megabyte (MibiByte) ... :
The program 'pv' can show the progress during the installation.
Do you want to install it? (y/N)n
Do you want to wipe a mass storage device (typically USB drive)? (y/n)
y
***  WARNING: the device will be completely overwritten      ***
     Use the info in the xterm window (less /tmp/help-mkusb.txt)
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************
 
Model: VBTM Store 'n' Go (scsi)    Disk /dev/sda: 2063MB    
Live drive: /dev/sda
USB drive:  /dev/sda: 2062 MB, 2062548992 bytes
 
No USB target device available. Toggle USB-only?
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
u
No target device available
ubuntu@ubuntu:~/Downloads$ sudo fdisk -lu

Disk /dev/sda: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x656da90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     4028415     2014192    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~/Downloads$ sudo parted -l
Model: VBTM Store 'n' Go (scsi)
Disk /dev/sda: 2063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  2063MB  2063MB  primary  fat16        boot, lba


ubuntu@ubuntu:~/Downloads$ 
```

---

### Post by sudodus on 2014-02-04
> **Aabicus_Finch said:**
> All right, I redownloaded mkusb from the provided url, and got the following. I'll just paste the whole code box from Terminal.

```
ubuntu@ubuntu:~$ cd ~/Downloads
ubuntu@ubuntu:~/Downloads$ ls
mkusb
ubuntu@ubuntu:~/Downloads$ xdg-open mkusb
ubuntu@ubuntu:~/Downloads$ chmod ugo+x mkusb
ubuntu@ubuntu:~/Downloads$ sudo ./mkusb wipe-1
Wipe the first megabyte (MibiByte) ... :
The program 'pv' can show the progress during the installation.
Do you want to install it? (y/N)n
Do you want to wipe a mass storage device (typically USB drive)? (y/n)
y
***  WARNING: the device will be completely overwritten      ***
     Use the info in the xterm window (less /tmp/help-mkusb.txt)
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************
 
Model: VBTM Store 'n' Go (scsi)    Disk /dev/sda: 2063MB    
Live drive: /dev/sda
USB drive:  /dev/sda: 2062 MB, 2062548992 bytes
 
No USB target device available. Toggle USB-only?
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
u
No target device available
ubuntu@ubuntu:~/Downloads$ sudo fdisk -lu

Disk /dev/sda: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x656da90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     4028415     2014192    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~/Downloads$ sudo parted -l
Model: VBTM Store 'n' Go (scsi)
Disk /dev/sda: 2063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  2063MB  2063MB  primary  fat16        boot, lba


ubuntu@ubuntu:~/Downloads$ 
```

Your computer can only recognize one mass storage device, the USB pendrive. It cannot identify any internal drive, neither via mkusb nor via fdisk and parted.

It is possible to create partitions on a drive with destroyed partition table, but if the drive is not found at all, these tools fail.

Have you checked the cables? Can there be some damage to some electrical or electronic component?

---

### Post by squakie on 2014-02-04
sudous - I don't want to distract from your progress......but.... ;)

Have the OP boot from the pendrive, then run gparted from the terminal in that live session.  It should still see the hard disk if is available under "Gparted" menu item, Devices sub menu.

From my limited experience, if a drive was zeroed, or in a strange state, selecting the deivce by clicking on the above might show a red circle (wiht a white exclamation point in it?) with the drive.  In my experience that means no partition table is foundso you have to use the "Device" main menu entry and select the "Create partition table" submenu item.

Maybe - and I have no idea in this case - it might show there, and if so, give some indication of what is wrong. 

Sorry to distract you.....
Dave ;)

---

### Post by sudodus on 2014-02-04
All ideas are welcome at this point :-)

So, yes, it is worth trying ***gparted*** to identify the device.

Or maybe ***hdparm***. See ```
man hdparm
```

---

### Post by slooksterpsv on 2014-02-04
How is the drive being seen via BIOS is it being seen as AHCI, IDE, or something else?

---

