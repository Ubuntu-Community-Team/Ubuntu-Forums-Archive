---
title: "[SOLVED] Write problems on partition?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by matthewhaworth on 2008-06-23
Every time that I go to partition my drive in the ubuntu installation it takes forever on 0% then eventually states that there have been some sort of write problem.  (I did printscreen the error message before i came back to windows but i don't know where it saved, which is annoying because i did exactly the same thing as i did last time when i took a screenshot in ubuntu).. any suggestions as to how to fix it?  I'm hoping it's a popular error with an easy fix?

Thank you in advance.

ps the screenshot below is one i took earlier, hope it helps?

---

### Post by Rocket2DMn on 2008-06-23
Are you trying to write to that FAT32 partition?  Please post the output of these commands in terminal:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by Duck2006 on 2008-06-23
Were you running gparted from ubuntu your the live cd. You can only partition the drive if it is not mounted, i like to use parted magic to do that with.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by matthewhaworth on 2008-06-23
I am very new to Ubuntu, so I don't really know where to type those commands lol.. any help? 

Also, what's really annoying is that I can't get the internet on it, it finds my wireless router, but when i type in the passcode, it takes a while and then asks me for the code again?  So I have to keep coming out and going into windows to talk on here.

Also, yes, I am running from the LiveCD.

I am grateful for your help : ).

---

### Post by Rocket2DMn on 2008-06-23
To get to terminal, go to Applications->Accessories->Terminal.
You can copy and paste in those commands, then copy and paste the output back here.

What are you trying to do anyway?  Are you just testing Ubuntu with the LiveCD?  Are you going to install?  Are you trying to partition your drive in advance?  Setting up a dual boot with Windows?

It will be easier to setup networking after you install.  Are you sure you chose the correct WEP encryption type (there are a few, try some different ones) - or are you using WPA encryption?  Did you type in the passphrase or the actual 10 alphanumeric character password?

---

### Post by matthewhaworth on 2008-06-23
I am presently running the LiveCD to install Ubuntu, I plan to partition my currently existant Windows partition, that is NTFS, to make space for it for a dual-boot.  The version of Ubuntu that I'm trying to install is 8.04, I will go back into Ubuntu soon and try your suggestions.  
Thanks a lot.
Any further help is greatly appreciated : ).

---

### Post by Rocket2DMn on 2008-06-23
No problem, be sure to defragment your windows partition first - this helps to prevent problems when resizing the NTFS partition to make room for Ubuntu's ext3 and swap partitions.

---

### Post by matthewhaworth on 2008-06-23
> **Rocket2DMn said:**
> No problem, be sure to defragment your windows partition first - this helps to prevent problems when resizing the NTFS partition to make room for Ubuntu's ext3 and swap partitions.

Done so three time :)

---

### Post by Rocket2DMn on 2008-06-23
> **matthewhaworth said:**
> Done so three time :)

Nice.  Post back if you have any questions during the installation.  Good luck and welcome to Ubuntu!

---

### Post by ajgreeny on 2008-06-23
Also make sure the hard disk is not mounted when you try to do anything to it.  In gparted right click on the partitions and click "unmount" if that is showing in the context menu.  You are not able to work on a mounted drive or partition, as Duck2006 has already stated.

---

### Post by matthewhaworth on 2008-06-23
> ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb6dbb6d
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         621        7295    53616937+   7  HPFS/NTFS
/dev/sda2               1         620     4980118+  12  Compaq diagnostics

Partition table entries are not in disk order
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="5C803F8D803F6CA0" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERY" UUID="73E1-7A9C" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
ubuntu@ubuntu:~$

There's everything you ask for, does that mean anything to you? Hope so, thanks for the help so far : ).

---

### Post by Rocket2DMn on 2008-06-23
Well I can pull information from that, but are you still having problems?  If so, can you please explain them in detail.  Is the installation just not moving forward?
You don't need to fiddle with the partitions beforehand, you can do it during the install process when it comes to that step.  You will end up resizing the NTFS partition to make room for Ubuntu at that time.

---

### Post by matthewhaworth on 2008-06-23
Well I haven't changed anything so I presume that I'm still going to have the same problem : (.  I'll try it again though, but the problem is when I go to actually partition the drive during the installation.. it says it's done 0% for quite some time, and then says there was a write error, I'll print screen it if it happens again.
Thanks for all of your help, Matthew H : ).

---

### Post by Rocket2DMn on 2008-06-23
If it still doesn't proceed, you may want to try the alternate install cd which uses a text based installer rather than a live session - don't worry, it's intuitive and easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.
Don't forget to check the md5sum:
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then burn at a slow speed like 4x to prevent write errors.
Good luck.

---

### Post by matthewhaworth on 2008-06-24
Okay, I'm downloading the alternate version now because I've tried it again and got the same error message.

(I had to take a picture on the phone because it wouldn't let me save a screenshot to my hard drive and my only pen drive's broken :( )

It reads "An error has occurred writing changes to the storage devices.  The resize operation has been aborted."

---

### Post by Rocket2DMn on 2008-06-24
OK hopefully the alternate cd will do better.  It could be that the device is still so fragmented that it won't allow it to resize, which means it won't let you install unless you format the drive clean and setup a dual boot from scratch.  Let's hope that is not the case.  Also let's hope that your drive is not malfunctioning.

---

### Post by matthewhaworth on 2008-06-24
I tried the Alternate version today and got the exact same error message, which is annoying.  I defragmented my drive a further three times today and now it only takes about five minutes to complete.  It appears as though there's some sort of read-only, write-block kinda thing on it? I don't know, it's starting to annoy me now lol.

Thanks for your help so far,

Edit:
I've just asked my defragmentation software to perform a defrag on system reboot, this can apparently 'defragment files that cannot be safetly moved while Windows is running.'  It says it'll also defragment the Master File Table and Paging file if necessary.  Is this worth a shot?

---

### Post by unutbu on 2008-06-24
Perhaps try this: boot from the regular (graphical) liveCD. Click System>Administration>Partition Editor. (This is GParted). 

Now try resizing the NTFS partition first (before you install). You just have to create a block of free space, you don't need to create a partition -- the installer can do that.

If you need to do multiple operations, like delete, then move, then resize, the do each operation separately, clicking the "Apply" button between each operation. That way, at least you'll see on which operation GParted gags. (Hopefully it won't gag...)

If that doesn't work, perhaps GParted is having trouble dealing with your NTFS partitions. (I have heard that Vista partitions should be edited using Vista tools, not GParted, but I don't know if that is an unfounded rumour or if it's true). So if GParted doesn't work, perhaps the rumour is true, and you'll have to use a Vista or Windows partition editor.

---

### Post by matthewhaworth on 2008-06-24
Okay then, I tried doing what unutbu suggested.  It still didn't work, however I now have some sort of report that may help?

> 
GParted 0.3.5

Libparted 1.7.1

Shrink /dev/sda1 from 51.13 GiB to 36.92 GiB  02:34    ( ERROR )
     	
calibrate /dev/sda1  00:01    ( SUCCES )
     	
path: /dev/sda1
start: 9960300
end: 117194174
size: 107233875 (51.13 GiB)
calculate new size and position of /dev/sda1  00:00    ( SUCCES )
     	
requested start: 9960300
requested end: 87393599
requested size: 77433300 (36.92 GiB)
new start: 9960300
new end: 87393599
new size: 77433300 (36.92 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:16    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 54903742976 bytes (54904 MB)
Current device size: 54903744000 bytes (54904 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38956 MB (71.0%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 42516 MB 0
Multi-Record : 54871 MB 9
$MFTMirr : 1 MB 1
Compressed : 48458 MB 278004
Ordinary : 54871 MB 12885
You might resize at 38955913216 bytes or 38956 MB (freeing 15948 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  02:00    ( ERROR )
     	
run simulation  02:00    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 39645849599 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 54903742976 bytes (54904 MB)
Current device size: 54903744000 bytes (54904 MB)
New volume size : 39645843968 bytes (39646 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38956 MB (71.0%)
Collecting resizing constraints ...
Needed relocations : 1764874 (7229 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1808 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:16    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 54903742976 bytes (54904 MB)
Current device size: 54903744000 bytes (54904 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38956 MB (71.0%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 42516 MB 0
Multi-Record : 54871 MB 9
$MFTMirr : 1 MB 1
Compressed : 48458 MB 278004
Ordinary : 54871 MB 12885
You might resize at 38955913216 bytes or 38956 MB (freeing 15948 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:01    ( SUCCES )
     	
run simulation  00:01    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 54903742976 bytes (54904 MB)
Current device size: 54903744000 bytes (54904 MB)
New volume size : 54903738880 bytes (54904 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 54903742976 bytes (54904 MB)
Current device size: 54903744000 bytes (54904 MB)
New volume size : 54903738880 bytes (54904 MB)
Nothing to do: NTFS volume size is already OK.

========================================


Any use?
I am actually on Ubuntu (LiveCD) now, I decided to wire it to my router because I couldn't be bothered starting Windows again...

---

### Post by Rocket2DMn on 2008-06-24
Try the defrag on boot since there are large files that can't be moved when Windows is already booted.

---

### Post by ajgreeny on 2008-06-24
Also worth trying to boot windows in safe mode (press F8 as it starts up) and then you may get a better defrag.  
Secondly, try disabling the virtual memory in windows while you run defrag as that means there is no swap equivalent.  It's this that often can not be moved.  Remember to turn virtual memory back on if you need to use windows again.

---

### Post by unutbu on 2008-06-24
Regarding 
> 
ERROR: Extended record needed (1808 > 1024), not yet supported!


take a look at [http://ubuntuforums.org/showthread.php?p=1689709](http://ubuntuforums.org/showthread.php?p=1689709).

I don't know if it provides a solution, but at least it hints at the nature of the problem (unmovable files like windows paging files?)

---

### Post by matthewhaworth on 2008-06-25
The problem is now solved : ].  Disabling the page file whilst I did the installation seemed to work perfectly.

Thanks for all your help.

---

### Post by ajgreeny on 2008-06-25
So I suspect that defrag with no page file (virtual memory) as I suggested would have done the trick as well.  That blasted page file can be a pain in the a**e when you need to move it, particularly if you have set a specific page file size manually.

---

