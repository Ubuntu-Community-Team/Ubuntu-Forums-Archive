---
title: "[SOLVED] LTS 6.06 Boot failure"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Piddell on 2008-06-07
Hi there,
My system has a problem booting, as follows:

Uncompressing Linux... Ok, Booting the Kernal.
mount: Mounting /dev/hda1 on /root failed:invalid argument

Followed by lots of no such file errors.

I am then landed in a busybox Debian built in shell

I can list files but have no idea where to start.

Any thoughts would be very welcome

Thanks

Phill

---

### Post by Oldsoldier2003 on 2008-06-07
> **Piddell said:**
> Hi there,
My system has a problem booting, as follows:

Uncompressing Linux... Ok, Booting the Kernal.
mount: Mounting /dev/hda1 on /root failed:invalid argument

Followed by lots of no such file errors.

I am then landed in a busybox Debian built in shell

I can list files but have no idea where to start.

Any thoughts would be very welcome

Thanks

Phill

sounds like you have a problem with /dev/hda1 have you done any partition changes lately? if not you might want to boot a live cd and take a peek. if everything appears like its there then you should take a look at the /boot/grub/menu.lst and check to make sure its good. if that looks good I would fsck /dev/hda1

---

### Post by rraj.be on 2008-06-07
i thnk you messed up with your partition.

The Grub is corrupted.
Just reinstall GRUB.

To reinstall Grub 

boot into live cd

open terminal  [Applications-->accessories-->terminal]

and type 
```

sudo grub

find /boot/grub/stage1
```

if it returned like hd(X,Y)
then type

```
root (x,y)

setup (x)

quit

sudo reboot.
```


now your GRUB is restored.

---

### Post by Piddell on 2008-06-07
I've not messed with anything - it was working ok last night.... (honest)

I booted from a live CD and that was ok.
I ran grub and it returned hd0,0 which got me worried!

From a live CD can I view the HD?  I thought it was locked.

Thanks for the help so far.

Phill

---

### Post by rraj.be on 2008-06-07
Then what happened when you Completed the restoration of the grub.

```
Had you ran 

root (0,0)
setup (0)

quit
sudo reboot
```

You can view all your disk's.

Nothing will be lost.

Only the pointer to the kernal was changed.

Try it and reply to me.

---

### Post by Piddell on 2008-06-08
Thanks for you help with my booting problem

I ran the find /boot/grub/stage1 command which returned (hd0,0)

I typed root (0,0) and got back
Error 11: Unrecognised device string.

I am using a slightly different live CD to the version which is on the machine.
The machine had a downloaded version of 6.06 and the CD is still 6.06 but was from a magazine.

Thanks

Phill

---

### Post by Herman on 2008-06-08
> sounds like you have a problem with /dev/hda1 have you done any partition changes lately? if not you might want to boot a live cd and take a peek. if everything appears like its there then you should take a look at the /boot/grub/menu.lst and check to make sure its good. if that looks good I would fsck /dev/hda1I agree with Oldsoldier2003.
Please post the output from 'sudo fdisk -lu'
```
sudo fdisk -lu
``` You can do that from a Live CD.
Also, can you mount your Ubuntu file system in your hard disk with the Live CD and post a copy of the bottom half of your /mnt/ubuntu/boot/grub/menu.lst here please?

---

### Post by Piddell on 2008-06-09
fdisk -lu
Disk /dev/hda: 200Gb
255 headsa, 63 sectors etc

Device Boot Start End Bocks Id System
/dev/hda1 * 63 388467764 194233851 83 Linux
/dev/hda2   388467765 390716864 1124550 5 Extended
/dev/hda5   388467828 390716864 1124518+ Linux swap / Solaris

I tried fsck /dev/hda1
fsck 1.38 (30 Jun 2005)
e2fsck 1.38 (20 jun 2005)
fsck.ext3: Attempt to read block from filesystem resulted in short read wile trying to open /dev/hda1
Could this be a zero length partition?

You said "mount your Ubuntu file system in your hard disk with the Live CD 
which I'm not sure about, I tried using disks manager but it just says inacessable for status (under partitions), not sure if this is what you mean?

Thanks

Phill

---

### Post by Herman on 2008-06-09
:) Okay then, boot your live CD and try this,
```
sudo e2fsck -C0 -p -f -v /dev/hda1
```
If that doesn't fix it, it will give you an error message advising you what to do next.
This link contains more information in case you're need it,  [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

Here is some info about how to 'mount' another file system, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")
If you just scroll down past the menu there, in the page that link gives you, you'll see some screencaps showing how to do it with the Hardy Heron live CD.
Otherwise, if you're using an older vintage Live CD, then look in this link, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000][/COLOR].

[/COLOR]

---

### Post by Piddell on 2008-06-10
Thanks for the advice,
All the e2fsck commands I have tried result in the following
Attempt to read block from filesystem resulted in short read whicle trying to open /dev/hda1
Could this be a zero-length partition?
I tried e2fsck -y -f -v /dev/hda1
-C0 -f -v /dev/hda1
-c -c -k -v /dev/hda1

so I tried to mount the drive
mkdir /media/ubuntu
mount -t ext3 /dev/hda1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error
In some cases useful infor is found in sysloh - try
dmesg | tail or so

dmseg | tail
[429550.521000] hda: dma_intr: status-0x51 {DriveReady SeekComplete Error }
.... {UncorrectableError}, LBAsect=144, high=0, low=144, sector=143
.... ide: failed opcode was: unknown
..... bad_request: i/O error.
etc etc(sorry am re-keying this on another machine!)

Phill

---

### Post by regomodo on 2008-06-10
To me, it sounds like a dead harddrive. If an fsck or e2fsck fail to work it may be possible to repair (if it's only a corruption issue) but ensure to dd the drive 1st before you go rebuilding the superblock.

I've been there before and after 2 hard drives dying on me (and trying to rebuild superblocks), i now give up at this point. Backups help too.

---

### Post by Piddell on 2008-06-10
ubuntu@ubuntu:/media/ubuntu$ dmesg |tail
[4303103.830000] ide: failed opcode was: unknown
[4303103.830000] end_request: I/O error, dev hda, sector 141
[4303103.830000] Buffer I/O error on device hda1, logical block 39
[4303105.891000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4303105.891000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=144, high=0, low=144, sector=143
[4303105.891000] ide: failed opcode was: unknown
[4303105.891000] end_request: I/O error, dev hda, sector 143
[4303105.891000] Buffer I/O error on device hda1, logical block 40
[4303141.941000] FAT: bogus number of reserved sectors
[4303141.941000] VFS: Can't find a valid FAT filesystem on dev hda2.

How dead is the drive?   I would like to get some files from it, but its not the end of the world if I can't.

---

### Post by Piddell on 2008-06-10
Just tried this

ubuntu@ubuntu:/media/ubuntu$ sudo badblocks -n -v /dev/hda1
Checking for bad blocks in non-destructive read-write mode
From block 0 to 194233851
Testing with random pattern: 0
1
2
........etc......
42
43
then it just hangs

---

### Post by Herman on 2008-06-10
Normally, you should see something like:
> user@hostname:~$ sudo badblocks -n -v /dev/sda
[sudo] password for user:
Checking for badblocks in non-destructive read-write mode
From block 0 to 194233851
Testing with random pattern: ...and nothing will happen for a very long time, like say fifteen minutes, half an hour or maybe even an hour or more, depending on the size of your hard disk. 
Your hard drive light in the front panel of your computer should be on, (indicating 'busy').

There will be no username@hostname prompt in your terminal while the badblocks program is in operation.
You'll know when the badblocks test is over when your usernam@hostname$ prompt appears in your terminal.
If you don't see any output, that means the badblocks program didn't find any badblocks. A bad block is an area of your hard disk which is losing its ability to hold a magnetic field, and thus reliably retain information. It can be a matter of opinion eaxctly how weak the block's magnetic properties can be before it's called 'bad', so some programs are set to be fussy and may find more bad sectors than other programs.

When mine finished, the output was:
> Testing with random pattern: Pass completed, 0 badblocks found.
herman@mx:~$The fact that yours output some numbers makes it look to me as if it found something, which is a bad sign, but I would have expected more output than that. 

Something else that would be interesting to try would be to check on what's recorded in the hard disk firmware's memory and see if that tells a story. You can read your hard disk's memory with smartmontools if S.M.A.R.T. is enables in your hard disk. Most hard disks support S.M.A.R.T.
You can do this from a live CD or an operating system in a hard disk, etc.
The output may or may not be conclusive, and it may take an expert to make any sense out of it. Most hard disk companies have their own software and keep their exact quality control info secret, but you can still get an indication as to what might be going on there inside your hard disk, or not going on as the case may be. If you want to try it,
```
sudo apt-get install smartmontools
``````
sudo smartctl -a /dev/sda > harddiskreport
```That should work instantly, and as quick as lightning you should see a new text file in your /home/username directory which just appeared, titled 'harddiskreport', which you can open with your text editor and read.
If it says anything about smart not being enabled, close the file and do 'sudo smartctl -s on /dev/sda', and try again, and you may get a more favorable output.
The output may or may not be conclusive, but it should be interesting and should give you some idea about the health of the hard drive.
[Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").

---

### Post by Piddell on 2008-06-12
Thanks Herman,
It was looking pretty bad, so I figured nothing to loose, so I ran "HDD Regenerator V1.51", which is a boot CD.  I borrowed it from a friend.
It found something horrible in a moment, and "fixed" it, great I thought so I rebooted but with the same result.
I then ran the program to the end (all night), no other problems.  
So I figured something had been fixed at the "hardware" level, but Ubuntu still was not happy.  I then ran 
sudo e2fsck -C0 -p -f -v /dev/hda1
More as a last ditch effort, and it now ran as you would expect, and found LOADS of errors, which it helpfully fixed (over 400)
It finished it's thing and reported on the outcome.  Reboot and all back to normal.
I shall backup my files now (had most stuff anyway) and upgrade to the latest Ubuntu, well we're on a roll now!

:)

Phill

---

