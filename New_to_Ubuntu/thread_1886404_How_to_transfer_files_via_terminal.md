---
title: "How to transfer files via terminal?"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by Alexalad on 2011-11-24
I uninstalled xorg, which broke my gui. So I'm stuck with the terminal, and for whatever reason, cannot reinstall it because it is ALWAYS unable to fetch certain archives when I try to. I've posted 2 threads asking for advice with no avail. So i'm forced to start all over by reinstalling ubuntu. And I was wondering, am I going to have to move the files onto my external hardrive individually, or is there any quicker way? Remember I only have a terminal to work with. Your help would be greatly appreciated.

---

### Post by Homicide on 2011-11-24
you probably want the mv command, tyr 'man mv' (without quotes ofc)

---

### Post by wolfen69 on 2011-11-24
A quicker way might be to boot to a live cd and transfer to an external drive.

---

### Post by donkyhotay on 2011-11-25
mv works, though I would recommend cp. mv will move a file around however cp will copy it to something else. Copying is a better idea in case something goes wrong, you still have the original (at least until the reinstall). The idea to use a liveCD is slower but will give you temporary GUI to move files around that way if you're not comfortable with CLI.

---

### Post by Alexalad on 2011-11-25
Would it be possible to fix my gui with the files from the live CD?

---

### Post by Jagoly on 2011-11-26
Possibly; but just out of curiousity, how did you manage to uninstall xorg?

What packages is it unable to find? Do you eve still have a network connection? If you were using wireless then that may be the problem.

EDIT: sorry I will read your other threads first

---

### Post by insomniaccanuck on 2011-11-26
you should be able to create an xorg.conf in your live cd boot by running this:

sudo X -configure

you shouldn't need a password to run it while running the live cd. I think just pressing enter if it asks you for it should suffice.


You don't have to copy (cp command) the file but if you may as well.
Move (mv) moves a file which will work (and by default the file is deleted from where it was).

---

### Post by Jagoly on 2011-11-26
Ok, I've had a bit of a look at your other threads, and there is still hope. If it's just for he wireless issues, there is still hope. 

On a live cd, run 
apt-cache depends xorg-xserver

Then list all of it's output. You can then, from either apt-get install --download or packages.ubuntu.org, download those things, and then copy them to your broken installation's /var/cache/apt/archives directory, and then install them with apt-get on the cli install.

---

### Post by Alexalad on 2011-11-26
@jagoly's first reply:
     I uninstalled xorg in my terminal after I selected 'end process' with xorg highlighted on my cpu monitor. I intended to reinstall it, but then...well, everything went to hell quite honestly. And no, I don't have an internet connection anymore which is putting me in an even deeper hole. I mean, I do, but I'm finding it near impossible to connect to my wifi through my terminal.


@insomniaccanuck's reply: I am currently on the live cd, and your suggested command output:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

@Jagoly's second reply: I tried your command and it output:

W: Unable to locate package xorg-xserver


And I am most definitely connected to wifi on the live cd, because how else could I post a reply on the forum.
Plus, to make matters worst, I can't get my original installation to recognize my external hardrive. which is what I was planning on transfering all my important files onto. I cannot catch a break lately. :/

---

### Post by Alexalad on 2011-11-26
I'm trying to get all of my important files out of my broken installation by transferring the files onto a external hardrive via the terminal, but when I connect my external hard drive, my terminal just outputs:

[     55.238607] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[     55.241349] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[     55.281440] sd 5:0:0:0: [sdb] Assuming drive cache: write through

So I guess trying to replace the broken packages with external files will be basically impossible, now.

Oh, and I assumed (which i'm learning is a very bad thing to do) that a live cd is no different than a usb, because i'm using a usb. Not a cd.

---

### Post by insomniaccanuck on 2011-11-26
The usb 'livecd' is more or less the same for what you're trying to do.
It does allow you to add software etc to the USB boot though.

You should be able to copy the files out with it.
I've done that a number of times before.

Also:
cp -r
allows you to copy the directory's files and all the subdirectories and files

EG:
cp -r home/username/Photos media/USBdrive/
might be something you want to do.

---

### Post by Alexalad on 2011-11-26
Well, i've encountered another complication. I've got all the replacement files I need from the live usb, but when I boot up my original broken installation, it won't recognize my external hardrive. I'll boot the original, login to the terminal, connect my external hardrive, but it says, soonafter I plug-in: 

[55.238607] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 55.241349] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 55.281440] sd 5:0:0:0: [sdb] Assuming drive cache: write through

And so I can't access the replace files in my external hardrive.

---

### Post by Jagoly on 2011-11-26
hang on, so you can not access you original install FROM the live CD/USB? trying to do the backup from the broken installation seems silly. you should be able to open up nautilus (GUI File Browser) from the live usb and easily access the data on the broken install to back it up. You should do that before trying any of the stuff below.

Also, as for apt-cache depends xorg-xserver, I meant xserver-xorg. but don't worry about that command any more.

If I run
```
sudo apt-get remove xserver-xorg
```
it says it will remove
```
xserver-xorg xorg ubuntu-desktop
```
so those should be the things you accidentally removed. you should be able to get those missing packages by typing, on the live CD,
```
sudo apt-get download xserver-xorg xorg ubuntu-desktop
```

then, again from the live cd, copy every .deb file in the live usb's home folder (hint: type "ls" without the quotes in the same terminal as you ran apt-get just after downloading the files to see what I mean) to /var/cache/apt/archives on the broken install. There be no need to use the command line to actually copy them. just use nautilus.

Then, exit the live cd, log in (terminal) to the broken install, and run
```
sudo apt-get install xserver-xorg xorg ubuntu-desktop
```
You may then need to, from the same broken install, run sudo X to start the GUI.

---

### Post by Alexalad on 2011-11-26
Wait. So I should be able to access all the directories of my broken installation through my live CD? But how? When I open the gui file browser on the liveCD, I only see files that are on my USB, or all the files that were made to trial ubuntu.

Does it have to do with the start screen when I boot up my LiveCD? It lists like five other things I haven't read. I always just choose "boot from USB/CD" Is this where I'm messing up? Because I'm on the livecd right now, but I can't find any files from my broken installation. 

OR are you saying that I SHOULD be able to login to my original installation, then access the liveCD from there?

I just want to get this straight, before I try the rest of the steps. This is probably all my fault for not knowing enough, but please, bare with me. Everyone else, including me, has given up hope.

---

### Post by azmyth on 2011-11-26
When you boot from the LiveCD, I suspect your bad install isn't automatically being mounted thus you can't see it to grab your files. I'm not sure how to mount it in ubuntu since I use KDE which displays the hard drive in the list of available devices.

If I was you, I'd move the computer closer to the router and hook up a cable and just repair your install by following the directions Jagoly gave you.

---

### Post by Alexalad on 2011-11-26
I tried using my ethernet cord, but when I plug-in, I'm still not connected to the internet, so I can't use the ethernet cord, either.

---

### Post by fdrake on 2011-11-26
@Alexalad
hi there, it looks like you are still stuck with that problem. Do you have a live cd? good that should be easier fro you..
boot from the live cd.
go to accessorie> terminal > type:
```
sudo fdisk -l (or "su fdisk -l")
```
and post here. you can connect with the wifi using the live cd easily.

---

### Post by Alexalad on 2011-11-26
Ok, awesome. Here's my feedback:

```

```ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068133

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29746   238932992   83  Linux
/dev/sda2           29747       30402     5263361    5  Extended
/dev/sda5           29747       30402     5263360   82  Linux swap / Solaris

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    c  W95 FAT32 (LBA)```

```

---

### Post by fdrake on 2011-11-26
copy and paste 1 by 1
```

sudo umount /dev/sda2
sudo mkdir /media/myHDD
sudo mount /dev/sda2 /media/myHDD
sudo nautilus /media/myHDD

```

can you see now your file?

---

### Post by Alexalad on 2011-11-26
I'm afraid not. It opened a gui file browser for a /media directory named myHDD. Just to check that I didn't mess anything up, here's what my terminal looks like:

ubuntu@ubuntu:~$ sudo umount /dev/sda2
umount: /dev/sda2: not mounted
ubuntu@ubuntu:~$ sudo mkdir /media/myHDD
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/myHDD
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo nautilus /media/myHDD
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by fdrake on 2011-11-26
> **Alexalad said:**
> I'm afraid not. It opened a gui file browser for a /media directory named myHDD. Just to check that I didn't mess anything up, here's what my terminal looks like:

ubuntu@ubuntu:~$ sudo umount /dev/sda2
umount: /dev/sda2: not mounted
ubuntu@ubuntu:~$ sudo mkdir /media/myHDD
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/myHDD
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo nautilus /media/myHDD
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
sorry my mistake!
```

sudo umount /dev/sda1
sudo mkdir /media/myHDD
sudo mount /dev/sda1 /media/myHDD
sudo nautilus /media/myHD

```

---

### Post by Alexalad on 2011-11-26
Ok. So that opened a gui file browser of a directory called myHDD. This directory only has files that are on my usb drive. It's essentially my USB drive with a different name. This USB drive was just the memory space I was using to boot up the livecd. How does this help, exactly? Because I was able to access it before too, but it had a different name before. I'm slow, so bare with me. It could take me awhile to put the pieces together.

---

### Post by fdrake on 2011-11-26
> **Alexalad said:**
> Ok. So that opened a gui file browser of a directory called myHDD. This directory only has files that are on my usb drive. It's essentially my USB drive with a different name. This USB drive was just the memory space I was using to boot up the livecd. How does this help, exactly? Because I was able to access it before too, but it had a different name before. I'm slow, so bare with me. It could take me awhile to put the pieces together.

are you typing /dev/sda1 or /dev/sdb1? from your outout sdb1 should be you usb driver and sda1 should be your hdd?

---

### Post by Alexalad on 2011-11-26
Well, this is what my terminal has:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo mkdir /media/myHDD
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/myHDD
ubuntu@ubuntu:~$ sudo nautilu /media/myHDD
sudo: nautilu: command not found
ubuntu@ubuntu:~$ sudo nautilus /media/myHDD
ubuntu@ubuntu:~$ 

```

Other than the typo, that's all correct, right?

---

### Post by fdrake on 2011-11-26
that's strange.... can you please do:```

sudo umount -a
sudo mount -a
mount
sudo fdisk -l
sudo nautilus /media

```
do you have anything of you hdd in the media folder? check all the folders please.
just to double check you are on a usb(4GB)-live disk right?

---

### Post by Alexalad on 2011-11-27
sudo umount -a output:

```
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /tmp: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /rofs: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```And this is what the rest of my terminal looks like:
```
ubuntu@ubuntu:~$ sudo mount -a
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068133

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29746   238932992   83  Linux
/dev/sda2           29747       30402     5263361    5  Extended
/dev/sda5           29747       30402     5263360   82  Linux swap / Solaris

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    c  W95 FAT32 (LBA)

```And no, sorry, I don't. But i'm actually running into a problem with it. In the myHDD directory I have all the special subdirectories...I forget what they're called, but they're the ones with names like bin, boot, lib, dev, sys, usr. So it's got all of those, but I can't actually open any of them. Whenever I double click any of them and error window pops up, saying:  "The folder contents could not be displayed. "lib" could not be found. Perhaps it has recently been deleted."

But it hasn't been deleted, because I've refreshed, and everything's still there. Is this supposed to happen? And when I select the properties of the subdirectories, it says the content are unreadable? and yes I'm booting off a 4GB usb drive. I'm very confused at this point...

---

### Post by fdrake on 2011-11-27
```

sudo gparted

```
select driver /dev/sda
righ-click the bar-size and select "mount"
do you see any window popping-up

----------------------
if stll nothing shutdown the pc > unplug the usb > unplug the AC power cord for 30sec (if it's a laptop take aout the battery) > plug the usb back > boot the pc
> selct boot from cd-ro/usb > select "try ubuntu"

you hard disk should automatically be mounted  : check /media and /mnt folders

---

### Post by Alexalad on 2011-11-27
I'm confused. What 'bar' am I supposed to right-click? If it's the '/dev/sda1' near the top, it doesn't give me the option to mount. Here's what my window looks like if this helps.

I'm gonna go ahead and do your other instruction, too.

---

### Post by fdrake on 2011-11-27
something (maybe a process is not letting your disk to be mounted). follow my instruction to shutdown and reboot the pc. If the disk does not mount automatically try 
```

sudo umount /dev/sda1
sudo fsck /dev/sda1
sudo mkdir /media/hdd
sudo mount -t ext4 /dev/sda1 /media/hdd
sudo nautilus /media/hdd

```

---

### Post by Alexalad on 2011-11-27
I shutdown and rebooted just following your instructions quite specifically. And after following your instructed commands, my terminal looks like this:
```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1 has been mounted 36 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 500055/14934016 files (0.3% non-contiguous), 12128038/59733248 blocks
ubuntu@ubuntu:~$ sudo mkdir /media/hdd
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda1 /media/hdd
ubuntu@ubuntu:~$ sudo nautilus /media/hdd
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


```And the last command did the same thing with the myHDD command. It just made a file browser of my usb drive with a different name.

Oh. and before i entered those commands, there was nothing mounted in those files other than my USB drive, which was mounted in the media directory.

---

### Post by fdrake on 2011-11-27
can you post the result of these:
```

ls -al /media/hdd
ls -al /media/hdd/home

```

---

### Post by Alexalad on 2011-11-27
Oh my God. Nothing is making sense, but I've finally made progress.
Here is what my terminal looked like:
```
ubuntu@ubuntu:~$ ls -al /media/hhd
ls: cannot access /media/hhd: No such file or directory
ubuntu@ubuntu:~$ ls -al /media/hdd/home
total 12
drwxr-xr-x  3 root root 4096 2011-02-10 00:26 .
drwxr-xr-x 24 root root 4096 2011-11-26 16:52 ..
drwxr-xr-x 85 1000 1000 4096 2011-11-26 03:44 grant
ubuntu@ubuntu:~$ ls -al /media/hhd
ls: cannot access /media/hhd: No such file or directory
ubuntu@ubuntu:~$ 

```

How could /media/hhd not exist when /media/hhd/home does?
So anyways, I went back to the gui file browser for /media/hhd clicked home, and boom. All my files from the broken installation. I'm sorry I didn't see that earlier, and caused you all this trouble. I should have recognized the home folder. But anyways, the way I see it, that hdd directory has all the directories of my usb + a directory with my username which has everything from my broken installation. So essentially, it...like joined my hdd and my usb, or something of the sort, right?

So thanks a bunch for that. I seriously cannot express my gratitude for this feat alone, And I feel really selfish asking, but what should I do now, to attempt to fix my original installation's gui? If anyone knows, its you at this point.

---

### Post by fdrake on 2011-11-27
ok at least we know the files are there ....
if you want to back up your files you can to anytime you want. 
give me few minutes i am searching to get you to download the package for xorg. let you know in 5 mins...

if i don't remember wrong your broken system is Lucid 10.4 right? i think we have the same system since i told you to download my source list. correct me if i am wrong.
i frogot to ask do you run an intel or an amd64 pc?

---

### Post by Alexalad on 2011-11-27
Right, I'm using 10.04. My broken installation was 10.04 as is the livecd i'm using.

And my processor is an amd v120. This is satellite c655 laptop if that means anything.

---

### Post by fdrake on 2011-11-27
> **Alexalad said:**
> Right, I'm using 10.04. My broken installation was 10.04 as is the livecd i'm using.
great so we may not need to download anything then.reboot your sys without the usb. once u are logged in plug the usb.

---

### Post by Alexalad on 2011-11-27
After I logged in, I plugged the usb in and waited. About 7 seconds later, a message very similar to this is output:

[55.238607] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 55.241349] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 55.281440] sd 5:0:0:0: [sdb] Assuming drive cache: write through

---

### Post by fdrake on 2011-11-27
once you have rebooted with the console plug the usb.
type these commands:
```

sudo umount /dev/sdb1
sudo mkdir /tmp/deb
sudo mkdir /media/usb
sudo mount -t vfat /dev/sdb1 /media/usb
sudo cp -v `sudo find /media/usb | grep ".deb"` /tmp/deb   

```
then ...

---

### Post by Alexalad on 2011-11-27
My bad, the message is actually:

[ 35.649597] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 34.652885] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 35.656964] sd 4:0:0:0: [sdc] Assuming drive cache: write through

It changed.

---

### Post by fdrake on 2011-11-27
what do you have with:
```

sudo fdisk -l

```

---

### Post by Alexalad on 2011-11-27
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068133

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29746   238932992   83  Linux
/dev/sda2           29747       30402     5263361    5  Extended
/dev/sda5           29747       30402     5263360   82  Linux swap / Solaris

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         488     3919841    c  W95 FAT32 (LBA)

---

### Post by fdrake on 2011-11-27
try
```

sudo umount /media/usb
sudo rmdir /media/usb
sudo mkdir /media/usb
sudo mount /dev/sdc1 -t vfat /media/usb

```

---

### Post by fdrake on 2011-11-27
let me know if you reach the last step.

---

### Post by Alexalad on 2011-11-27
First command output:
umount: /media/usb: not found

Second output no such file or directory

The last two must have been successful as there is no output.

---

### Post by fdrake on 2011-11-27
that's good! now those:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk2
sudo cat >/etc/apt/sources.list
deb /media/usb/ .   <press enter>
< press CTRL + d >

```

---

### Post by Alexalad on 2011-11-27
The cp command worked.

The cat command output:
-bash: /etc/apt/sources.list: Permission denied 

This makes no sense, as I did it twice. Both times using sudo.

The deb command output:
No command 'deb' found, did you mean:
*List of commands*

I didn't really understand the last 2 lines of your instructions, though.

---

### Post by fdrake on 2011-11-27
the cat command will give you a prompt (in witch you have to write the deb line- deb is not a command). so it's
cat .... <press enter>
deb ....<press enter>
<press CTRL + d keys - to exit from the cat prompt>

---

### Post by Alexalad on 2011-11-27
Oh. My apologies.
Anyways, the cat command or whatever that was must have been successful. I received no feedback and my terminal just shows:

$ sudo cat
deb
deb
$


Everything good so far.

---

### Post by fdrake on 2011-11-27
just to dd check
```

less /etc/apt/sources.list

```
what does it output?

---

### Post by Alexalad on 2011-11-27
It just shows:
/etc/apt/sources.list

---

### Post by fdrake on 2011-11-27
let's try this again:
type:
```
sudo cat >/etc/apt/sources.list

``` now press anter and type
```
deb /media/usb/ .
```press enter
press key "ctrl" and "d"

then post the output of
```

less /etc/apt/sources.list

```

---

### Post by Alexalad on 2011-11-27
So my first line should read:

$ sudo cat >/etc/apt/sources.list 

Before I hit enter, right? If this is the case, I get this feed back:
-bash: /etc/apt/sources.list: Permission denied

---

### Post by Alexalad on 2011-11-27
Oh I swore I saw ls in the place of less. In that case, I get a whole file. And I can't type the whole thing out cause i'm using my phone to text replies. But it has ## signs and deb links followed by deb-src links.

---

### Post by Alexalad on 2011-11-27
Deb cdrom is on one of the first lines. Followed by ubuntu 10.04.1.  Which wasn't the version I remember having. I remember having 10.04.3. So the file has definitely been changed.

---

### Post by Alexalad on 2011-11-27
Well fdrake, I sincerely can't thank you enough for how far you've brought me, but its almost 3:30 in the morning here. So I guess i'll have to pick up on this another time. Hopefully i'm not too much further from fixing my gui.

---

### Post by fdrake on 2011-11-27
ok that's finish this you are very close. 2-3 commands left!
tasl -1---------------------------
so boot the pc > login > insert the usb and type:
```

sudo fdisk -l

```
----------------------------------
task-2
check the output: you chould see ether Disk /dev/sdb or /dev/sdc with a size of 4022 MB. that's your usb disk.
if you see sdb do:
```

sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/usb

```

instead it you see sdc sobstitu "sdb1" with "sdc1" to have:
```

sudo umount /dev/sdc1
sudo mount -t vfat /dev/sdc1 /media/usb

```
-----------------------------------
task-3
now type:
```

echo "deb file:///media/usb/ lucid main restricted
" | sudo tee /etc/apt/sources.list

```

-----------------------------------
task -4
```

sudo aptitude install xorg
sudo startx

```

---

### Post by Alexalad on 2011-11-27
Ok, when I plug the usb, I still get that same 'sdc assuming drive cache: write through' message. I guess that's normal.

Heres my output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068133

Device Boot Start End Blocks Id System
/dev/sda1 * 1 29746 238932992 83 Linux
/dev/sda2 29747 30402 5263361 5 Extended
/dev/sda5 29747 30402 5263360 82 Linux swap / Solaris

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 488 3919841 c W95 FAT32 (LBA)

Everythings the same as the last time I entered this command.

---

### Post by Alexalad on 2011-11-27
Nothing returned an error other than the last message 'sudo start x'
Which output:

xauth: /home/*username*/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/user/.Xauthority

exec: 3: /usr/bin/X: not found
giving up.
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error.
xauth: error in locking authority file /home/user/.Xauthority

I'm not connected to the internet. Would this complicate things?

---

### Post by Alexalad on 2011-11-27
Wait, the install command output that the "xorg" package couldn't be found.

---

### Post by Jagoly on 2011-11-27
That is where you need to follow my advice of downloading the packages on a live cd and then putting them into the broken installation's /var/cache/apt/archives folder. So, follow fdrake's advice, however, instead of following the instructions in task four, either
A: do exactly what I said in my last reply, or

B: download, on any other computer, or, if you have 2 usb drives, the live usb, these three files:
[http://packages.ubuntu.com/lucid/i386/ubuntu-desktop/download]("http://packages.ubuntu.com/lucid/i386/ubuntu-desktop/download")
[http://packages.ubuntu.com/lucid/i386/xserver-xorg/download]("http://packages.ubuntu.com/lucid/i386/xserver-xorg/download")
[http://packages.ubuntu.com/lucid/i386/xorg/download]("http://packages.ubuntu.com/lucid/i386/xorg/download")

Copy those, from either the live usb (if you can) or from the broken installation off of another usb using
```
sudo mount -t vfat /dev/sdb1 /media/usb
``` to mount the usb. have only one usb plugged in when you do this to avoid complications

```
sudo cp /media/usb/*.deb /var/cache/apt/archives
``` to copy them

now, run
```
sudo apt-get install xorg xserver-xorg ubuntu-desktop
``` to install X

if you get errors with that, try
```
sudo apt-get install xorg xserver-xorg ubuntu-desktop --no-install-recommends
```

then run, ONLY if there have been no major errors,
```
sudo startx
```

---

### Post by Alexalad on 2011-11-29
Ok, I copied all of the packages successively, but the install command output:
E: Couldn't find package xorg.

The no-recommends command gave the same output.

And I was wondering if I needed to change the names of the packages. Because the filename for the package, xorg, was saved as: xorg_7.5+5ubuntu1_i386.deb
I assumed that it would be best to not change the file name.

I followed the instructions as precisely as possible, despite not knowing anything about how package installation works.

Does it matter that I ran the installation from the mounted '/media/usb' directory?

I went to my var/cache/apt/archives directory and typed 'ls'. Which output a long list of pink .deb files, 1 purple file named "partial", 1 gray file named "locked", and the 3 green xorg and ubuntu packages that I copied. Why are they green? I'm guessing that's where the problem is. But I have no idea. What do the colors mean?

---

### Post by Jagoly on 2011-11-29
hmm... They would be green because they have different access permissions. But that shouldn't make a difference, because apt-get was run as root.

I thought that would work, sorry. I have done it numerous times myself, usually to install large programs like nexuiz (a game) on my younger brother's computer as well as mine to save on my limited monthly download allowance. However, those times we both had an internet connection. I think that the way apt-get works is:
1: check local catalog to see if it exists and if it is already installed
2: looks up packages.ubuntu.org for more info
3: installs, and if necessary, downloads it

There is a way to install packages manually without apt-get, using dpkg. dpkg is the program (apt also uses it) that actually installs the .deb files once apt-get has them. It can, however, be used stand alone as well. But you have to be careful or you may end up in dependency hell (don't want to be there)

from the broken install, assuming you already have copied the xorg stuff to /var/cache/apt/archives, (you will no longer need a usb), type:
```
cd /var/cache/apt/archives
sudo dpkg -i [green package 1] [green package 2] [green package 3]
``` you will need to use the entire file names, do not rename them.

now, reboot the computer. If X starts up, then
1: Scream "YEEEESSSSS!!!!!"
2: enjoy your now working install

If X does not start up, then we may need to reconfigure X. Depennding on your graphics card (or intel GPU) there may be a best way to do that. I'm sorry if you've already posted it

---

### Post by Alexalad on 2011-11-29
It said I couldn't install those packages because "xserver-xorg-core" and "xserver-xorg-video-all" and a bunch of other packages with similar names, weren't installed. Does that mean i'll have to download all of those packages, copy them over to the archives directory and dpkg all of them at the same time?

---

### Post by Jagoly on 2011-11-30
yes. If there are other dependencies, you will need all of them too. When i checked it on 11.10, I would have only needed those three (but I would need the 11.10 packages not the 10.04 ones I linked you too), but xorg may have had more dependencies in 10.04.

You can download all of the .debs from packages.ubuntu.org

---

### Post by Alexalad on 2011-12-03
Well I downloaded and copied all of the packages and dependencies it said I needed, and still nothing. To install one package, I need another package to already be installed. Its a circle of errors, and I install any of them. 

I did however, find a way to connect to wifi. This can help, right?

---

### Post by fdrake on 2011-12-04
to verify that you are actually online can you do :
```

ping google.com

```
if you see different line showing it means you ar online then you can do :```

sudo apt-get install xorg xserver-xorg ubuntu-desktop
sudo startx

```
post here fi you encounter errors.. we will try our best to hep you.

i really hope you can get this done and I admire your persistence in trying and learning..

---

### Post by Jagoly on 2011-12-04
> **Alexalad said:**
> Well I downloaded and copied all of the packages and dependencies it said I needed, and still nothing. To install one package, I need another package to already be installed. Its a circle of errors, and I install any of them. 

I did however, find a way to connect to wifi. This can help, right?

Yup. That's the definition of dependency hell.

If you can connect to wifi, then you should just be able to run sudo apt-get install [packages] normally.

Like fdrake, I greatly admire you persistence.

---

### Post by Alexalad on 2011-12-13
Ok! My apologies for taking so long to reply, but my schedule has been tight. I'm still in high school, so exams, soccer and theatre practice have consumed me this week. But before I tell you my life story, I hope you guys are still willing to help out a desperate novice.

So, I ping'd google.com to get a ceaseless amount of feedback, all starting with "64 bytes from..." and ending with "time=x.x ms." I was unaware that ctrl + C was the only way to stop it. Afterwards it output my "google.com ping statistics". I am certainly connected, though...right?

Unfortunately, I still can't install the oh so precious xorg packages and I get a similar error message. Doing nothing else after pinging, I tried the "sudo apt-get install xorg xserver-xorg ubuntu-desktop"
But it output an all too familiar error code:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xorg

Startx output something slightly different:

exec: 3: /usr/bin/X: not found
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

I love how the words "giving up." are in the feedback. Its like my terminal is trying to tell me something...

---

### Post by Alexalad on 2011-12-13
Oh. I thought it might be worth noting that I had to shut down my network manager to connect to my wifi using the command "sudo /etc/init.d/network-manager stop".

So I, being stupid, was hoping that the command "sudo /etc/init.d/network-manager start" would fix this. Although, i'm fairly confident that it didn't change anything...

---

### Post by Alexalad on 2011-12-17
Well bad news, I got impatient and attempted a fix that requested I remove nividia packages. It did not work at all. After rebooting, I can't connect to wifi anymore. I have an ethernet chord, but I don't know how to connect it because just plugging it in does nothing. Even if I could connect to the internet, I took the silence as a sign that everyone was out of suggestions.

I posted 3 threads for this problem and all 3 have come to a complete halt. And its hard for me to try and understand how killing one process can crash my whole installation. I appreciate all of your help, and I apologize for letting all that help go in vain, but I hope you won't condemn me too much when I tell you...I.GIVE.UP. 

But before I reinstall, I just wanted to confirm that nuking is the right decision. I've already backed everything up and plan on nuking tomorrow. So if you agree or disagree that I am making the right move (however dishonorable it might be), please leave a reply telling me so. It will help me feel less guilty.

Also, should I do anything to this thread since it's basically done for? Thanks again.

---

### Post by fdrake on 2011-12-17
> **Alexalad said:**
> Well bad news, I got impatient and attempted a fix that requested I remove nividia packages. It did not work at all. After rebooting, I can't connect to wifi anymore. I have an ethernet chord, but I don't know how to connect it because just plugging it in does nothing. Even if I could connect to the internet, I took the silence as a sign that everyone was out of suggestions.

I posted 3 threads for this problem and all 3 have come to a complete halt. And its hard for me to try and understand how killing one process can crash my whole installation. I appreciate all of your help, and I apologize for letting all that help go in vain, but I hope you won't condemn me too much when I tell you...I.GIVE.UP. 

But before I reinstall, I just wanted to confirm that nuking is the right decision. I've already backed everything up and plan on nuking tomorrow. So if you agree or disagree that I am making the right move (however dishonorable it might be), please leave a reply telling me so. It will help me feel less guilty.

Also, should I do anything to this thread since it's basically done for? Thanks again.

there is nothing wrong in nuking if you have bucked-up all your files.:) actually that would have taken lesssssssssss time , but it was a good learning experience for both sides(you and us). If someone tells you they never needed to reinstall the system well : that's a lie :D

---

### Post by audiomick on 2011-12-17
> **Alexalad said:**
>  So if you agree or disagree that I am making the right move (however dishonorable it might be), please leave a reply telling me so. It will help me feel less guilty.

I haven't read all of the thread, but you seem to have spent a lot of time on this. If it is time for you to re-install, then do it. There are those who are willing and able to persevere. There are others who re-install at the first sign of problems. It is all a matter of how much time and energy you have for learning. If you need the computer to work, do what is needed to make that happen.


> 

Also, should I do anything to this thread since it's basically done for? Thanks again.

Mark it as solved. That is an option under the drop-down menu "thread tools" at the top of threads you have started.

---

