---
title: "Urgent - all data seems to have vanished"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by doggo on 2012-09-23
I'm running an very old, outdated Ubuntu - because I'm too useless to update it myself and haven't seen my Ubuntu-savvy friend for a while - and recently it's seemed to be falling apart a bit. First of all it wasn't booting all the way (just got stuck on some text about Postfix configuration) so I had to use Ctrl+Alt+F1 and log in that way with sudo gdm (after which the Ubuntu login screen would appear and everything would continue as normal). So I've been hanging on meaning to get it properly updated ASAP.

Unfortunately, I got up this morning to a nasty surprise. Instead of the usual Postfix configuration stuff, I got a repeating message about some kind of error (I'm too ignorant in Ubuntu nuts and bolts to understand it). Managed to get past that and log in - it took a VERY long time to load the login screen, but it worked in the end. 

But *all my data seems to have gone*. I have a smallish hard drive which came with the computer which contains my home directory and everything, then a terabyte hard drive which I bought separately and installed, which contains all my data (pictures, personal stuff, music etc). My desktop picture was a photo from in there - the desktop is now black. I open Nautilus and all the bookmarks I put in down the side panel for folders in the data drive (Music, Pictures etc) have disappared. I tried opening OpenOffice and loading a piece of work from Recent Documents (work with a deadline of tomorrow morning, incidentally) and it said it didn't exist.

The folder "Data" was still there but locked. Maybe that's the problem, I thought, and changed the permissions. No, it still claims to be empty. Although weirdly, when I go in there, the amount of free space listed is still the free space left on the home drive rather than what was left on the data drive. 

I ran sudo blkid, and the output was this:

/dev/sda1: UUID="616b339c-baee-49ab-8954-e1165332b5d1" TYPE="ext4" 
/dev/sdb1: UUID="d104e6c0-1c5b-40b0-b0f0-90321ffe1eb9" TYPE="ext4" 
/dev/sdb2: UUID="66c7c64b-a53e-4c0d-8596-849225aabd7b" TYPE="ext2" 
/dev/sdb3: UUID="e80e5f6c-0d34-45b4-8ab3-9ea86e31cee3" TYPE="swap" 
/dev/sdb4: UUID="b6dc1fef-4fc6-4f73-b360-4aa9f7efff6f" TYPE="ext4" 

No idea if that's any use.

I opened a terminal and used locate to try and find stuff - it's not finding it.

I have no idea what could have caused this, all I know is that I should have a terabyte of stuff here, only about half of which is backed up (I know, I know), some of which is irreplaceable... and it seems to have vanished.

Any suggestions very gratefully received... but if this has all gone, that's a very very big deal indeed, so break it to me gently.

---

### Post by sandyd on 2012-09-23
It sounds like the data drive is failing to mount

Can you post the output of
```

sudo mount -l
```

Thanks!

---

### Post by ibuclaw on 2012-09-23
What filesystems are mounted?  And where do you expect the data to be located?

To get a list of mounted filesystems through a terminal, run:
```
df -h
```

Regards

---

### Post by doggo on 2012-09-23
Thanks for the quick replies.

Here's the output from df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19G   12G  5.6G  68% /
udev                  497M  292K  496M   1% /dev
none                  497M  2.4M  494M   1% /dev/shm
none                  497M  196K  496M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda1             459G   76G  360G  18% /data500
/dev/sdb2             449M  112M  314M  27% /boot


I've actually forgotten which one the data's on - yes, I'm an idiot - but I do know that it's none of these. And I do remember that the error message at startup related to sda4, so I suspect it's that one. "Data500" is a backup partition thing with the bare essentials in it (baby pictures, etc) but the main data section is a terabyte and would be at least 95% full (yes, again, I'm an idiot). It's obviously not mounted.

---

### Post by doggo on 2012-09-23
Sorry, can I be really impertinent and ask what sudo mount -l does before I do it? I'm treading extremely carefully here just in case there's hope... would that attempt to mount any unmounted filesystem?

---

### Post by ibuclaw on 2012-09-23
> **doggo said:**
> Sorry, can I be really impertinent and ask what sudo mount -l does before I do it? I'm treading extremely carefully here just in case there's hope... would that attempt to mount any unmounted filesystem?

mount -l lists all mounted filesystems - similar to df, but shows more information related to each filesystem, unlike df which only shows disk usage. PS: You also don't need sudo to run that. ;)


To mount all filesystems listed in /etc/fstab, you would run:
```
sudo mount -a
```
Does any error come from the above?  If not, check the location where you expect your files to be.

---

### Post by doggo on 2012-09-23
OK, thanks.

Output from mount -l:

/dev/sdb1 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /data500 type ext4 (rw)
/dev/sdb2 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/USERNAME/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=USERNAME)

Do you think I should run sudo mount -a and see what happens? Could anything go wrong? I mean... more wrong.

---

### Post by Elfy on 2012-09-23
I'd post the results of

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by doggo on 2012-09-23
OK... sudo fdisk -l:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001fc47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        2493      489982+  83  Linux
/dev/sdb3            2494        2991     4000185   82  Linux swap / Solaris
/dev/sdb4            2992      121601   952734825   83  Linux



And cat /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d104e6c0-1c5b-40b0-b0f0-90321ffe1eb9 /               ext4    errors=remount-ro,user_xattr 0       1
# /boot was on /dev/sdb2 during installation
UUID=66c7c64b-a53e-4c0d-8596-849225aabd7b /boot           ext2    defaults        0       2
# /data was on /dev/sdb4 during installation
UUID=b6dc1fef-4fc6-4f73-b360-4aa9f7efff6f /data           ext4    defaults        0       2
# /data500 was on /dev/sda1 during installation
UUID=616b339c-baee-49ab-8954-e1165332b5d1 /data500        ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=e80e5f6c-0d34-45b4-8ab3-9ea86e31cee3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by sandyd on 2012-09-23
does
```

sudo mount /dev/sdb4 /data

```
do anything?

(/data shows as not mounted currently)

---

### Post by doggo on 2012-09-23
Thanks again... I'll try it. Presumably that will try to mount it? Can I just double-check that that's totally safe, and it's definitely not going to be break / overwrite anything or whatever? Sorry to be a drag, but I like to know what's going on as I go along, and because I'm so ignorant that can sometimes involve asking dumb questions like this...

---

### Post by doggo on 2012-09-23
Oh - and is it worth me running sudo fsck.ext4 -y /dev/sdb4 before I try to mount it? As far as I can tell sdb4 is not mounted at the moment...

Thanks again

---

### Post by doggo on 2012-09-24
Really sorry to bump this but I'm not sure exactly what to do here. Could anyone help me out?

---

### Post by Cheesemill on 2012-09-24
```
sudo mount /dev/sdb4 /data
```
Will attempt to mount the drive, If this command is not successful it should give an error message that will help us to diagnose the problem. There is no risk to your data by trying this command.

---

### Post by doggo on 2012-09-24
Thank you!

Amazingly enough, it mounted without a complaint and everything's still there. The only thing which seems peculiar is that when I navigate to various folders in Nautilus, there's a VERY long pause and everything hangs for ten or fifteen seconds before eventually the hard drive starts whirring, and the contents show up and are accessible. This actually happened first the night before this trouble started...

I have no idea whether one or the other of my hard drives is starting to fail or whether the issue is with my ancient (and now unsupported) Ubuntu. I haven't made any changes to fstab, but then again the fact that it's started to boot to a prompt and I have to login and start gdm that way doesn't inspire confidence. I'm about to start backing up essential data now, but can anyone suggest whether this is more likely to be hardware problems, or an issue with running Ubuntu 9.10 in 2012? Because if it's just the latter I'll breathe more easily.

Thanks again for the help, sorry to be a dunce.

---

### Post by funicorn on 2012-09-24
after you have backed up your data and umount /data.
then run 'e2fsck -f -v /dev/sdb4'
see what it outputs, especially its exit code.

---

### Post by doggo on 2012-09-24
Thanks very much, I will do. It won't be until tomorrow at least, as I have a LOT of data to backup here, but I'll bump this thread when I'm done.

---

### Post by sandyd on 2012-09-25
> **doggo said:**
> Thank you!

Amazingly enough, it mounted without a complaint and everything's still there. The only thing which seems peculiar is that when I navigate to various folders in Nautilus, there's a VERY long pause and everything hangs for ten or fifteen seconds before eventually the hard drive starts whirring, and the contents show up and are accessible. This actually happened first the night before this trouble started...

I have no idea whether one or the other of my hard drives is starting to fail or whether the issue is with my ancient (and now unsupported) Ubuntu. I haven't made any changes to fstab, but then again the fact that it's started to boot to a prompt and I have to login and start gdm that way doesn't inspire confidence. I'm about to start backing up essential data now, but can anyone suggest whether this is more likely to be hardware problems, or an issue with running Ubuntu 9.10 in 2012? Because if it's just the latter I'll breathe more easily.

Thanks again for the help, sorry to be a dunce.

That sounds like it is in the stages of failure (the pausing). I would advise you immediately backup the drive, or mirror it to somewhere before it does.

---

### Post by doggo on 2012-09-25
> **funicorn said:**
> after you have backed up your data and umount /data.
then run 'e2fsck -f -v /dev/sdb4'
see what it outputs, especially its exit code.


Alright, I just went through the whole process hitting "y" over and over, even though I didn't understand 50% of what was coming up, because a.) I read that this was the best plan, and b.) I had nothing to lose. Final output is this:


/dev/sdb4: ***** FILE SYSTEM WAS MODIFIED *****

  102640 inodes used (0.17%)
    4387 non-contiguous files (4.3%)
      56 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 100890/1722/17
221946163 blocks used (93.18%)
       0 bad blocks
       3 large files

   99073 regular files
    3554 directories
       0 character device files
       0 block device files
       0 fifos
4294967294 links
       4 symbolic links (1 fast symbolic link)
       0 sockets
--------
  102554 files


Does that tell us anything? I suppose I should try rebooting now and seeing what happens...

---

### Post by doggo on 2012-09-25
I made sure I backed everything up to an external hard drive, by the way, but I noticed that quite a lot of one particular folder (the music folder, luckily - i.e. ripped CDs, replaceable data) had vanished. No idea why... I'm assuming this data has gone for good, but we'll see.

What I don't understand is that this is a decent quality hard drive and only 2 years old. Is there any reason why it might be failing like this? I did have to power-flip the other night when everything froze... but it wasn't the first time I'd noticed everything hanging recently (specifically when going in and out of that drive) so I'm not sure that was the cause. Are there any other obvious causes of disk failure, more or less out of the blue? Or am I just plain unlucky?

---

### Post by sandyd on 2012-09-26
*shrug*
Hard disks are moving things - they will fail from time to time. Even enterprise HDDs fail. I had one RE3 die on me within a year.

---

### Post by doggo on 2012-09-29
Sorry - thought this thread had died and stopped checking. 

Anyway, fsck fixed my hard drive (at least temporarily) which allowed me to back up everything on it. It's now mounting at boot as normal and behaving fine, although I'm ready for it to go kaput at any moment. Thanks for your help, I learned a fair bit here. Basic stuff maybe, but I needed to learn it.

---

### Post by mips on 2012-09-30
> **doggo said:**
> Sorry - thought this thread had died and stopped checking. 

Anyway, fsck fixed my hard drive (at least temporarily) which allowed me to back up everything on it. It's now mounting at boot as normal and behaving fine, although I'm ready for it to go kaput at any moment. Thanks for your help, I learned a fair bit here. Basic stuff maybe, but I needed to learn it.

If you use a offline mail client like thunderbird, evolution etc also remember to backup your mail store which lives in a different location (usually a hidden folder).

Get a new hard drive and do a fresh install of Ubuntu when you are ready.

---

