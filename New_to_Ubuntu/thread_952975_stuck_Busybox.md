---
title: "stuck Busybox"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by chrisxhtml on 2008-10-19
Hello, 
   I'm running Hardy 8.04 and my system keeps booting to the initramfs prompt. I've been to many different forums and have found no good answers, but I recently tried replacing the "quiet splash" with "all_generic_ide" as suggested in many other posts. I received this error: 
 
Check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/2A64FA4264FA0FF5 does not exist. Dropping to a shell!

BusyBox v 1.1.3(Debian1:1.1.3-5 ubuntu 12)
Built-in Shell(ash)

(initramfs)

---

### Post by chrisxhtml on 2008-10-19
Hello, 
   I'm running Hardy 8.04 and my system keeps booting to the initramfs prompt. I've been to many different forums and have found no good answers, but I recently tried replacing the "quiet splash" with "all_generic_ide" as suggested in many other posts. I received this error: 
 
Check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/2A64FA4264FA0FF5 does not exist. Dropping to a shell!

BusyBox v 1.1.3(Debian1:1.1.3-5 ubuntu 12)
Built-in Shell(ash)

(initramfs)

---

### Post by bodhi.zazen on 2008-10-19
Threads merged :)

I know it happens, but try not to create duplicate threads ;)

---

### Post by Pro-reason on 2008-10-19
Please post the output of:

```

cat /boot/grub/menu.lst
cat /etc/fstab
sudo blkid -L

```

Use [noparse]```
...
```[/noparse] tags for legibility.

---

### Post by chrisxhtml on 2008-10-19
```

(initramfs) cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such File or Directory

(initramfs) cat /etc/fstab
cat: /etc/fstab: No such File or Directory

(initramfs) sudo blkid -L
/bin/sh: sudo: not found

```

It seems that many terminal type commands do not work at the BusyBox prompt (i.e. sudo)

Using the ls command, I found out that there is no /boot/ directory. Also, there is no fstab in the /bin/ directory.

---

### Post by Pro-reason on 2008-10-19
> **chrisxhtml said:**
> 

It seems that many terminal type commands do not work at the BusyBox prompt (i.e. sudo)

Using the ls command, I found out that there is no /boot/ directory. Also, there is no fstab in the /bin/ directory.

Sorry, I wasn't clear.  I meant to say that you should do those commands if you can somehow get to a proper terminal. 

If the system really doesn't want to let you do that, then the live CD is properly the only option.  Boot into it, and get the information.  You will have to mount your hard drive partition(s) and then look on them.  So, you will be looking in locations such as /media/Ubuntu/etc/fstab.

If you don't understand how to do that, I can try to explain in more detail.

---

### Post by chrisxhtml on 2008-10-19
I'm relatively new to Linux (in case you couldn't tell). I know how to boot with live CD, but not how to mount the partitions. If you could explain how to do this, it would be greatly appreciated.

---

### Post by Pro-reason on 2008-10-19
Boot from the Ubuntu Live CD.  (I'm assuming it's a standard GNOME Ubuntu CD, rather than a Kubuntu one.)

Go to Places &#8594; Computer.

You will see all your partitions.  Find the one which is your main root partition, with Ubuntu installed.  Clicking on the icons will mount the partition.

Click on the little button that looks like a page of writing with a pencil.  That will display the path for the drive.  In my case, it is "/media/Ubuntu".

Your Ubuntu partition is now mounted, and you know where it is mounted.  You just have to put that path in front of any path on your system.

For example, I would hit Ctrl-F2 and type:
```

gksu gedit **/media/Ubuntu**/etc/fstab
```

You can apply the same principle to open /boot/grub/menu/lst.

Remember: if you just put the normal path in, forgetting the extra bit that we worked out above, then you'll just get the _live CD's_ temporary files.  We don't want that.

Also type this at a terminal:

```

sudo blkid -L

```

You should be able to use the live CD to log on to these forums and report the info.  if not, then save the info somewhere (on a USB stick, etc) and then get to the forums using another machine.

No guarantees, but I hope that the info will give me some clue as to what is wrong.

When did it start failing to boot properly?

---

### Post by chrisxhtml on 2008-10-19
Ok. Originally I didn't want to post all of this information because I figured it was too long and drawn out, but here it goes.  Given the nostalgic nature of my personality, I decided I wanted to install DOS 6.22 and Windows 98 on a completely separate physical hard drive. So, I removed my main hard drive (With Dual Boot - WinXp and Ubuntu) and installed another hard drive to try and install DOS (via floppy) and 98 (to no avail). After giving up on that (and removing the floppy drive), and reinstalling my original hard drive (Xp and Ubuntu), my PC became very slow to start up (even very slow to get to BIOS setup). I can still boot to XP (again, slowly - probably takes a full 2.5 minutes to boot to windows). After messing with the other hard drive (DOS and 98 ) and coming back to my original hard drive, I was still able to boot successfully to the Ubuntu gui (GNOME) one last time. I did some updates and shut down and I have not been able to get to the gui since. This makes me think the updates to Ubuntu caused the problems, but I have a feeling it might have something to do with the slowness of the entire bootstrap loading process.

---

### Post by Pro-reason on 2008-10-20
Reading all that made my head hurt.

OK, so at all times, there was only one drive attached, right?  (Two different drives, but only one at any one time.)

Were these of the same type (SATA versus IDE; that is to say, they had the same cables)?

---

### Post by chrisxhtml on 2008-10-20
Yes, that's correct. There were 2 different drives, one at a time, and both were IDE (I don't have SATA on my motherbard). I'm going to check if I can mount the partition now and I'll report the results here soon.

---

### Post by chrisxhtml on 2008-10-20
Well, unfortunately, I cannot boot to Ubuntu even with live CD because I receive a seemingly endless list of I/O errors, however I may have an idea about my problem:
 

I have 4 logical partitions on my main drive:
 [LIST]
[*]C:\ - My Xp Partition
[*]D:\ - Unformatted
[*]E:\ - Formatted - Blank (or so I thought)
[*]F:\ - Formatted - Ubuntu Partition
[/LIST]

I believe that I reformatted my E:\ in Xp (to try to get 98 onto it). I wasn't thinking that there might be Ubuntu data on it since most installs use more than one partition (from what I understand). I *could not* see any data on the disk before I formatted it. 

Could it be that I'm such a noob that I erased some data needed to boot up to Ubuntu??

---

### Post by bodhi.zazen on 2008-10-20
Well, you need to understand what is on each partition.

Also Linux does not use C: , D: , etc, so you will need to understand Linux partitioning.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

Now boot the live CD and look at your partitions. You can use either gparted or the comand line (fstab).

You can mount a partition with :

```
sudo mount /dev/sda1 /mnt
```

Then look at the contents with ```
gksu nautilus /mnt
```

Then look at the next partition :

```
sudo umount /mnt
sudo mount /dev/sda2 /mnt
```

And on ...

You can also try restoring grub with supergrub or from the live CD:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

    [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by chrisxhtml on 2008-10-20
Per Pro-reasons suggestions:

I can't see any of my partitions when I boot with live CD under Places -> Computer. The only one I see is Filesystem and I believe it is actually on the CD because I cannot mount the drive. 

When I do this:

```

sudo blkid -L

``` 

I get this:

blkid: invalid option -- L
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghl] [-o format] [-s <tag>] [-t <token>]
    [-v] [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)

When I do this(lower cased l):

```

sudo blkid -l

``` 

I get this:
The lookup option requires a search type specified using -t

Per bodhi-zazen's suggestions: 

I am still reading through your partition guide and instructions.

---

### Post by bodhi.zazen on 2008-10-20
try:

```
sudo blkid
```

---

### Post by chrisxhtml on 2008-10-20
When I try:

```

sudo blkid

```

I get:

/dev/loop0: TYPE="squashfs"

---

### Post by Pro-reason on 2008-10-20
> **chrisxhtml said:**
> 
I believe that I reformatted my E:\ in Xp (to try to get 98 onto it). I wasn't thinking that there might be Ubuntu data on it since most installs use more than one partition (from what I understand). I *could not* see any data on the disk before I formatted it. 

Could it be that I'm such a noob that I erased some data needed to boot up to Ubuntu??

XP is not very capable when it comes to filesystems.  It can only see NTFS (its own) and FAT (the old filesystem for DOS).  Ubuntu by default creates *swap* partitions and *ext3* partitions.  It can also see *ext2*, *reiserfs* partitions, etc.  XP will typically report to the user that Linux partitions are unformatted.  You may well have deleted something.  I don't know how the installer sets things up by default, because I always partition manually.

---

### Post by Pro-reason on 2008-10-20
> **chrisxhtml said:**
> When I try:

```

sudo blkid

```

I get:

/dev/loop0: TYPE="squashfs"

Yep, that's the fake filesystem that the live CD uses.  I'm fairly sure that “blkid” should be able to see your real drives too, though.

I'm beginning to believe that the problem is with the cables.  Either you didn't attach them correctly when you replaced the old drive, or you damaged them.  IDE cables are very fragile.  I have made my system unbootable before by unplugging and replugging IDE cables too much.  It's easily done.  It's probably one of the many reasons why SATA is replacing IDE.

Sorry about the “-L” switch not working with the “blkid” command.  It works on my machine, running an up-to-date Kubuntu 8.10 beta Intrepid Ibex.  I suppose that the older version of the command on the Hardy live CD does not have all the recent improvements.  The “-L” switch lists the info in a neat table.

---

### Post by chrisxhtml on 2008-10-20
> **bodhi.zazen said:**
> 
Now boot the live CD and look at your partitions. You can use either gparted or the comand line (fstab).

You can mount a partition with :

```
sudo mount /dev/sda1 /mnt
```

Then look at the contents with ```
gksu nautilus /mnt
```


I tried:

```
sudo mount /dev/sda1 /mnt
```

And got this message:

mount: special device /dev/sda1 does not exist

When I tried:

```
gksu nautilus /mnt
```

It just brought up the mnt folder, which was empty (and I believe is coming directly off of the CD)

---

### Post by Pro-reason on 2008-10-20
> **chrisxhtml said:**
> I tried:

```
sudo mount /dev/sda1 /mnt
```

And got this message:

mount: special device /dev/sda1 does not exist
Well, yes.  The system does not seem to be able to see /dev/sda1 or any other drive. We ascertained this with the “blkid” command.

Since this failed, viewing the mounted drive in nautilus of course then failed.

The fact that you are having trouble even booting from the live CD shows that there is a hardware problem.

---

### Post by chrisxhtml on 2008-10-20
> **Pro-reason said:**
> 
I'm beginning to believe that the problem is with the cables.  Either you didn't attach them correctly when you replaced the old drive, or you damaged them.  IDE cables are very fragile.  I have made my system unbootable before by unplugging and replugging IDE cables too much.  It's easily done.  It's probably one of the many reasons why SATA is replacing IDE.


YES!! This worked!! Thank You so much, I was very close to reinstalling and I just replaced the IDE cable. Solved my slow boot problems and was able to boot directly into Ubuntu from the hard drive.

Thanks to both of you guys for all the help!:guitar:

---

### Post by Ducatiboy Stu on 2008-10-20
Did you try [COLOR="Navy"]fdsik -l[/COLOR] from liveCD term...

It should list ALL drives and partitions...

Then you can work out where your Ubuntu is, example /dev/sdx?

X=drive a,b,c
?= partiton number

so you might get /dev/sdb/5 as you Linux location..

I had an issue with loosing grub when re-inst XP..

Get the SuperGrub liveCD and use it to find and re-install grub.


You may also have to edit grub to reflect any new locations for /boot directory

Be vary carefull of re-installing windows over Ubuntu...it can cause much grief ..I am still sorting out a screwed partiton..

[http://ubuntuforums.org/showthread.php?t=951076](http://ubuntuforums.org/showthread.php?t=951076)

[http://ubuntuforums.org/showthread.php?t=951443](http://ubuntuforums.org/showthread.php?t=951443)

[http://ubuntuforums.org/showthread.php?t=953018](http://ubuntuforums.org/showthread.php?t=953018)

---

### Post by Ducatiboy Stu on 2008-10-20
AHHH...you fixed it as I was typing...




:lolflag:

---

