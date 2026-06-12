---
title: "Ubuntu tells me I don't have enough free space; I think I do!"
date: 2017-11-20
forum: New to Ubuntu
---

### Post by sterator on 2017-11-20
Tonight's update to Ubuntu weighed in at 67mb, but I got a system warning me that I didn't have enough space and that I should free up 300-400MB. I actually have 156 GIGA bytes of free space!

A few minutes later, I tried to copy about 400MB worth of photos from a USB drive to the same computer, also told I needed to free up about 466MB - I have the same amt of free space: 156GB!

My trash can is empty, if that makes any difference..

Why would the system not "know" that I have far more free space than it's telling me I do? Is there a remedy to this situation?

Thank you!

---

### Post by deadflowr on 2017-11-20
What does the command below show
```
df -h
```

---

### Post by Geoffrey_Arndt on 2017-11-21
Question is . . . is that space available to Ubuntu?   In other words, is it a linux formatted and within the /home directory?    The other directories are not directly writeable - - and windows partitions are not included in the calculation for obvious reasons.   Even other Linux distro partitions are not included.    Is the space just plain "unallocated" from a prior install that didn't use the whole disk?

---

### Post by vasa1 on 2017-11-21
And the output of```
sudo fdisk -l
```may help as well.

---

### Post by wyliecoyoteuk on 2017-11-21
How much free space do you have in your root partition?
packages are downloaded to /var/cache

copying files may also use cache

If you are using a VM, then dynamically resized virtual disks are often read wrongly.

Using apt on the command line often reads the sizes correctly when a desktop app doesn't..

---

### Post by sterator on 2017-11-21
df -h produces this:

```
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.9G     0  7.9G   0% /dev
tmpfs                        1.6G  9.9M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  442G  419G     0 100% /
tmpfs                        7.9G   30M  7.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
tmpfs                        1.6G  108K  1.6G   1% /run/user/1000
/dev/sdb                     458G  234G  201G  54% /media/maker/Bento_Backup
```

I did my installation of 17.04 last June. I took a Mac Pro and made it a single-boot Linux machine. I had no issues during the installation process and I *believe* that I let the installer decide how big the partitions would be.

I do get what you are saying, but it's confusing to me that if a system window tells me, at the bottom, that I have 150 some gigabytes left, isn't that the System telling me what it thinks is available?

> **vasa1 said:**
> And the output of```
sudo fdisk -l
```may help as well.

Here is the result of sudo fdisk -l:

```
maker@bento:~$ sudo fdisk -l
[sudo] password for maker: 
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1640C185-17C5-4A3C-8312-F6F6CA88BACE

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 976771071 975720448 465.3G Linux LVM


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 449.3 GiB, 482395291648 bytes, 942178304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 16 GiB, 17171480576 bytes, 33538048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by ubname on 2017-11-21
Have you tried to remove unused packages,
maybe you gain enough space:


```
sudo apt autoremove
```

---

### Post by deadflowr on 2017-11-21
> **wyliecoyoteuk said:**
> How much free space do you have in your root partition?
packages are downloaded to /var/cache

copying files may also use cache

If you are using a VM, then dynamically resized virtual disks are often read wrongly.

Using apt on the command line often reads the sizes correctly when a desktop app doesn't..

I'd look at the other /var sub directory: log.
With over 400GB used, either a bad lvm config ( I doubt something like that)
or an error is producing a runaway logging which is actually common.
Consider running the command
```
 du -sh /var/log
```
to see if the log directory is packed full or not.

Here's some more tips to search for where the disk space has gone:
[https://ubuntuforums.org/showthread.php?t=1122670]("https://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by wyliecoyoteuk on 2017-11-21
Odd that it shows the logical volume / as 100% full, yet the physical volume dev/sdb shows half full

---

### Post by Holger_Gehrke on 2017-11-21
> **wyliecoyoteuk said:**
> Odd that it shows the logical volume / as 100% full, yet the physical volume dev/sdb shows half full

Not odd at all, /dev/sdb is a different disk, mounted as /media/maker/Bento_Backup, probably formated as some kind of superfloppy (no partition table, just a filesystem starting at Block 0), while '/' is in a logical volume on sda. And yes '/' is full, according to df. If sterator thinks he should have about 150G free, something is strange. Either some process has gone **way** overboard on the logging (150 Billion bytes of log entries ?!?) or a simple typing mistake in the shell has produced copies of some really big files (misconfigured backup, perhaps ?).

Holger

---

### Post by wyliecoyoteuk on 2017-11-21
Of course, my bad.
Phones aren't the best for reading posts.
I suspect you're right, a copy of that backup in the wrong place perhaps?

---

### Post by sterator on 2017-11-21
running this now...it seemed to promise to remove 2gb worth of items, I believe...

...and it appears to have removed closer to 4GB.

Thank you..gonna tuck that away for later.

I've also - independently of the helpful suggestions - begun offloading music onto thumb drives..I'm now up to about 72 gb free.

still not quite where it ought to be, according to my unscientific memory/calculation, but at least the system has room to blink its eyes now!

;-)

Bento_backup is my backup. I use grsync.

my 2 discs are the same model of samsung ssd. so far, the arrangement's been working nicely.

I need to stay more on top of things, especially as I get more comfortable with Linux and what it needs and does..

> **deadflowr said:**
> I'd look at the other /var sub directory: log.
With over 400GB used, either a bad lvm config ( I doubt something like that)
or an error is producing a runaway logging which is actually common.
Consider running the command
```
 du -sh /var/log
```
to see if the log directory is packed full or not.

Here's some more tips to search for where the disk space has gone:
[https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)


here's what I get when I run the above command:


> maker@bento:~$ du -sh /var/log
du: cannot read directory '/var/log/speech-dispatcher': Permission denied
618M    /var/log

Well..that's weird..now grsync can't "see" Bento_Backup!

yikes!

---

### Post by leunam12 on 2017-11-22
There is a disk usage analyzer that shows you graphically your disk usage

---

### Post by VMC on 2017-11-22
"**ncdu**" is my favorite disk usage tool. Once installed point it to what mount partition you want. "**ncdu /**" will obviously show your current root.

---

### Post by wyliecoyoteuk on 2017-11-22
Filelight is a good graphical tool to tell you what size your files are.

---

### Post by sterator on 2017-11-22
Is there a reason grsync can't "see" my backup?

I can see that backup at the system window level and prior to yesterday afternoon, grsync could see it too.

---

### Post by leunam12 on 2017-11-23
post the output of lsblk

---

### Post by sterator on 2017-11-23
the output after I type lsblk into a terminal is:




```
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1                  8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2                  8:2    0 465.3G  0 part 
  &#9500;&#9472;ubuntu--vg-root   253:0    0 449.3G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 253:1    0    16G  0 lvm  [SWAP]
sdb                     8:16   0 465.8G  0 disk /media/maker/Bento_Backup
sr0                    11:0    1  1024M  0 rom
```

---

### Post by leunam12 on 2017-11-23
your backup drive is mounted at /media/maker/Bento_Backup, can rsync see it? Try this```
mkdir test
touch test/example1.txt
rsync -a test /media/maker/Bento_Backup
```
now go to your backup drive, there should be a new directory named test and a file inside named example1.txt. If this is successful rsync is working just fine, maybe all you need to do is restart your system.

---

### Post by sterator on 2017-11-23
That worked..the folder and example1.txt file are on Bento_Backup

going to restart now.

thank you

fingers crossed

restarted, launched grsync, grysync throwing same "can't find path" error.

So, while rsync seems to work, the GUI tool "grysnc" is having a snit for some reason?

restarted, launched grsync, grysync throwing same "can't find path" error.

So, while rsync seems to work, the GUI tool "grysnc" is having a snit for some reason?

---

### Post by leunam12 on 2017-11-23
Pretty weird. Try purging and re-installing```
sudo apt remove --purge grsync
sudo apt install grsync
```I don't know what else to do.

---

### Post by sterator on 2017-11-23
> **leunam12 said:**
> Pretty weird. Try purging and re-installing```
sudo apt remove --purge grsync
sudo apt install grsync
```I don't know what else to do.

Purged and tested - successful: no grysnc

Installed grsync, launched, same error.

I guess I need now to do my rsync-ing via terminal commands.

Thank you for your help..this has been informative.

also, if I do my backups from now on with rsync, will it "know" of the existing back up?  It's been rsync all the time, only with the GUI of grsync as the "control panel"

---

### Post by leunam12 on 2017-11-23
Yes, it will "know".
It is very easy to use from the terminal: ```
rsync -avP /source/ /destination/
```if you put a "/" at the end of your source directory it means: "the contents of"; if there is no / it will copy the directory with the contents. Example:```
rsync -a /path/to/A /path/to/B
```will create a new directory named "A" inside of directory B. On the other hand```
rsync -a /path/to/A/ /path/to/B
``` will place **the contents** of A inside of directory B.

---

### Post by sterator on 2017-11-24
Thank you...

is it ok if directory B is an entire drive?

IOW, is an SSD itself a "directory?"

---

### Post by leunam12 on 2017-11-24
If it only has one partition. I imagine you want to backup everything, then the command is ```
sudo rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} /* /media/maker/Bento_Backup
```

---

### Post by leunam12 on 2017-11-24
Sometimes packages break and they are fixed when you update. Free up some space on your hard drive and update your system and try grsync again.

---

### Post by SeijiSensei on 2017-11-24
> **sterator said:**
> restarted, launched grsync, grysync throwing same "can't find path" error.

So, while rsync seems to work, the GUI tool "grysnc" is having a snit for some reason?

Are you running grsync as root?  Running rsync as root?  If you run grsync as an ordinary user, you need to have full permissions on the backup device.

---

### Post by sterator on 2017-11-24
well, I am the admin and until the other day, grsync simply ran without issue. I haven't run it as root.

---

### Post by vasa1 on 2017-11-24
> **sterator said:**
> well, I am the admin and until the other day, grsync simply ran without issue. I haven't run it as root.

So you ran it as "admin"?

---

### Post by sterator on 2017-11-27
> **vasa1 said:**
> So you ran it as "admin"?

Yes, I have run both grsync and rsync as "admin"

To be clear, I have one user on this computer..should I not run rsync as admin and should I have a non-admin User?

I may have found what was chewing up my space, tho I don't know the fix:

while I loaded a fair amount of music onto this computer, for some reason there were 2, 3, sometimes 4 copies of each track.

I'd googled that rhythmbox sometimes will *display* duplicates, but in my case, there were actual duplicates at the file level.

This isn't something one would absent-mindedly do, in all likelihood...although..if one were absent-minded while doing it...how would they know they did it?

My method is to drag files to a folder on the computer, sort them, and in the case of music, import them into Rhythmbox, which does whatever it does...

I removed all of the music from this computer and will add a few things at a time, see what the result is. I'd loaded perhaps around 100GB of music (and knew it) but wound up with far more through some kind of whack duplication.

---

