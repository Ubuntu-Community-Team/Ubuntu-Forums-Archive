---
title: "rdiff-backup howto and script"
date: 2006-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by nanotube on 2006-07-06
This is a quick howto on using rdiff-backup (available in official repositories as package rdiff-backup) on Ubuntu. rdiff-backup lets you make backups of your files, and conserves disk space by storing only the differences between new and old files. See the homepage of rdiff-backup here: [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

This howto will show you how to quickly make backups to an external usb disk (rdiff-backup is also capable of making backups over the net, through ssh, but that is not what I do, and I figure that will hold for desktop users.)

**1. Install rdiff-backup by running commands**:
```
sudo aptitude update
sudo aptitude install rdiff-backup
```

**2. Create an rdiff-backup script that will store your options**, for ease of use (and for possible automation). My script is as follows:
```
#!/bin/bash
sudo /usr/bin/rdiff-backup --exclude /tmp --exclude /var/log --exclude /mnt --exclude /media --exclude /proc --exclude /sys --exclude /var/cache/apt --exclude /home/dfolkins/.Trash --exclude /data/.Trash-dfolkins --exclude /data/Documents / /media/usbdisk/dfolkins_backup/
```

Lets look at the details of the command. First comes sudo (because i am backing up everything, not just my user files), then comes rdiff-backup itself. Then, we have a bunch of --exclude statements, that exclude the directories you don't want to back up. The only one that you really need to exclude is /proc, everything else i just exclude because i don't need it. after that, comes your source dir (just / for me), and your destination dir (/media/usbdisk/dfolkins_backup for me). so it will take everytihng from /, and shove it onto that usbdisk, with the exception of the directories that are excluded.

**3. Name the text file something like** "rdiff-backup-script.sh", save it somewhere, say in your home directory, and make it executable by running
```
chmod u+x rdiff-backup-script.sh
```

**4. Preparing the usb disk.** Usually a new drive (or an old one) will be formatted with fat32. The problem with fat32 is that it has no capability to store permissions, so rdiff-backup may give you errors. If you are just backing up your personal data files, and not the whole system, fat32 may be ok, but for whole-system backups, you need to create an ext3 partition on your disk. If the disk currently has no data on it, you can just resize or delete the fat32 partition, and make an ext3 (using, for example, gparted partition editor, which you can install from the repositories.) If you already have data on your disk that you don't want to lose, then you have to be careful about moving things around (look around on these forums about repartitioning hard drives).

The next thing to do with the disk is to create a directory that you will use as the target for your backups, and make sure your user can write to it (give it the right permissions).

**5. now, just run the command with** 
```
./rdiff-backup-script.sh
```
and sit back and wait. The first time around it will take you longer, since it copies everything over. subsequent backups will take much less time, since it only copies the diffs.

---

### Post by Gen2ly on 2007-01-22
Sounds neat.  Anyone ever try this?  I just just Heliodes Howto on restore and backup  using tar.  But the idea up making additional backups that just update the changed files on the systems is definitly appealing.

---

### Post by kilou on 2007-01-25
Don't you have to recreate the excluded directories manually afterwards?? I have this issue with the TAR method when doing the restore from the LiveCD (assuming your system was not bootable and you had to reformat its partition). As I had to recreate the excluded folders from the LiveCD, they didn't get the correct permissions and I got an error after login because the /tmp was not accessible. I'm unsure if this method would cause the same problem but it is likely it would because it really exclude some folders instead of just excluding their content. It would be nice if it was possible either with this rdiff method or with TAR to exclude only the content of some folders but leaving these folders as empty folders so that their permissions are backed up in the archive. It may not be important if you restore from a working system because you don't need to recreate the excluded folders but when restoring from the LiveCD after a complete system breakdown, it definitely is a problem.

Do you know if this is possible either with TAR or rdiff????

---

### Post by ykhun on 2007-02-19
Nice tutorial. Thanks.

I always seem to get the following error everytime i fire up rdiff-backup.
```
UpdateError dev/bus/usb/.usbfs/devices Updated mirror temp file /media/usbhdd/ping/dev/bus/usb/.usbfs/rdiff-backup.tmp.4 does not match source

```

I tried restoring files etc, they all work. Anyone knows if i should worry about this at all?

---

### Post by nanotube on 2007-02-20
> **ykhun said:**
> Nice tutorial. Thanks.

I always seem to get the following error everytime i fire up rdiff-backup.
```
UpdateError dev/bus/usb/.usbfs/devices Updated mirror temp file /media/usbhdd/ping/dev/bus/usb/.usbfs/rdiff-backup.tmp.4 does not match source

```

I tried restoring files etc, they all work. Anyone knows if i should worry about this at all?

i think the error just means that the file was changed while rdiff was working on it. i don't know exactly what that file is supposed to be, but it seems to have something to do with usb hard drive. and since you are backing things up TO a usb hard drive, it's no wonder that it changed. :) i'd say don't worry about it.

---

### Post by ykhun on 2007-02-21
> **nanotube said:**
> i think the error just means that the file was changed while rdiff was working on it. i don't know exactly what that file is supposed to be, but it seems to have something to do with usb hard drive. and since you are backing things up TO a usb hard drive, it's no wonder that it changed. :) i'd say don't worry about it.

Yeah, i guess u have a point there. It is always that same file whenever i backup with rdiff-backup. Anyways, i had another question related to rdiff-backup but i guess i should start a [new thread here](http://ubuntuforums.org/showthread.php?p=2187463#post2187463).

---

### Post by shane2peru on 2007-09-23
nanotube,  Nice howto, however I noticed you are lacking a restore method.  I'm sorry if it is obvious, I don't know what it is.  :)  Obviously if a file is corrupted you could just copy that file over, however if you want to restore your entire system from this backup, what would be the proper procedure?  Thanks.

Shane

---

### Post by pingpongboss on 2007-09-24
hey thanks for this script! i found it a month or so ago and have been using it to backup my system ever since. Only question: is there a way to view the backed up files over a timeline or something? I want to know what versions of the file were backed up, and when.

---

### Post by rdnk on 2007-10-07
> **pingpongboss said:**
> hey thanks for this script! i found it a month or so ago and have been using it to backup my system ever since. Only question: is there a way to view the backed up files over a timeline or something? I want to know what versions of the file were backed up, and when.

You can do
```
rdiff-backup -l **/backupdir/backupfile**
```
to list all the available increments and their times. Additionally,
```
rdiff-backup --list-increment-sizes **/backupdir/backupfile**
```
track the space taken by the increments.

---

### Post by hollerith on 2007-10-07
The script has a sudo in it.  Surely, it will only work if you have recently used sudo on some command and it remembers what password you typed in?  
Why do you need a script at all?  If you wanted the same exclusions every time wouldn't you use a file on the target anyway and use the globbing option?  
I'd like xscreensaver to run my script sort of like a lunch-break autosave - but without asking for a password - any ideas?


I still don't know why the setuid is not working for rdiff-backup - I can setuid other scripts like bash &c.  However, I have found :

```

# Allow rdiff-backup without password prompt
hollerith ALL=NOPASSWD: /usr/bin/rdiff-backup

```

Which should work?  Altho - it might be that I've just sudo to edit the sudoers file.  I'd like to know where the timeout for a sudo password is set.

---

### Post by nanotube on 2007-10-07
to set a different sudo timout, see this thread:
[http://ubuntuforums.org/showthread.php?t=179048](http://ubuntuforums.org/showthread.php?t=179048)
(it can be set in /etc/sudoers)

that NOPASSWD sudoers entry should allow you to run rdiff-backup without sudo... does in not work?

i wrote the script so that i don't have to retype all those exclude options etc, all i have to do is launch the script.

i didn't care to have it run unattended, because it was backing up to a usb drive, with wasn't always connected - only when i needed to do a backup. if you need it to run unattended, then obviously there is more to be done (ie, all that sudoers tweaking) :)

---

### Post by hollerith on 2007-10-08
> **nanotube said:**
> 
that NOPASSWD sudoers entry should allow you to run rdiff-backup without sudo... does in not work?


I wasn't sure if it was just because I had just done a sudo.  I had originally tried to 

```

sudo chmod 4755 `which rdiff-backup`

```

but still got permissions problems on the destination! 

> **nanotube said:**
> 
i wrote the script so that i don't have to retype all those exclude options etc, all i have to do is launch the script.


I was just saying that you could put all those excludes in a globbing file on the destination instead.  But I like this way too.  

Incidentally, what I'm doing is weird anyway - I'm running the script from xscreensaver so that I get 'many and often'.  I tend to work in bursts so its like an autosave/undo option!  

Also, I use quoted excludes with wildcards so I get empty directories on the destination.

```

#!/bin/bash

sudo rdiff-backup --print-statistics --exclude '/media/*' --exclude '/proc/*' --exclude '/tmp/*' --exclude '/dev/*' --exclude '/sys/*' --exclude /root/.cache --exclude '/var/log/*' / /media/Maxtor/backups &

```

I'd be interested to hear other peoples exclude lists for 'everything essential' and perhaps some examples with ignoring types of files.

I was going to give this point and drool interface for rdiff-backup called pybackpack a go too but this howto is so easy anyway why bother?

Thanks for the link BTW (and of course the great howto!)

---

### Post by shane2peru on 2010-11-30
This is old, but I wonder if anyone has used this and restored without problems?  I started looking into rdiff again, and like what it offers, better than the tar method.  Wondered if anyone had successfully restored their system with this.

Shane

---

