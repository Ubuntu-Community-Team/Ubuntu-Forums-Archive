---
title: "HOWTO: Backup multimedia with rsync"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by djgrandmarquis on 2006-06-03
The Ubuntu forums contain several great posts about fully backing up a Linux system. I use this one regularly: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

But this method doesn't work very well for large, numerous multimedia files. The above process yields a single tarball, which is not ideal for accessing music or movies. As a digital DJ, I need to carry around all my music on an external hard drive even though my collection is stored on my desktop.

My woes began with Windoze, where trying to backup a large number of files was painful at best. My needs were pretty straightforward: I wanted a one-way mirror of all my multimedia, with the ability to not only copy files from Kubuntu to the external disk, but also with the ability to remove files that I deleted on my desktop machine. I also needed incremental backup capability, since I don't want to copy the same gigabytes of data over and over.

Linux offers several tools for backing up/mirroring files. Some include Unison ([http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)), fullSync([http://fullsync.sourceforge.net/](http://fullsync.sourceforge.net/)), and rsync([http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)). (Unison is available from the Ubuntu repositories, fullSync is a downloadable Java app, and rsync is a command-line tool that comes with Linux.) This howto documents my success with rsync.

At first I formatted my external hard drive with FAT32([http://en.wikipedia.org/wiki/Fat32](http://en.wikipedia.org/wiki/Fat32)), so that my XP laptop and my Kubuntu desktop could read and write to it. However, FAT32 lacks several keys features that make it difficult to use with synchronization tools:
-case-insensitive file names
-no user permissions
-goofy time stamps (they vary by significant amounts)
-it's slow (it's a very old file system)

The result is that automated backups of files are nearly impossible with FAT32. So my solution was to reformat the drive as ext3([http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)). I found a nice driver to read and write ext3 in Windows, ext2IFS([http://www.fs-driver.org/](http://www.fs-driver.org/)). (related Ubuntu forum: [http://ubuntuforums.org/showthread.php?t=115717](http://ubuntuforums.org/showthread.php?t=115717))

With everything in place, it was time to start backing up! Unison is designed for two-way synchronization, which I'm not interested in; if I accidentally delete a file on my external drive, I surely don't want it to get deleted on my desktop. FullSync never installed properly (it didn't like my pango settings, I assume because of 64-bit incompatibilities), so rsync emerged as my tool of choice.

Here's my backup script, to automate the process:

```
#!/bin/sh

# rsync.sh
#
# - this script will back up my 4 dirs that need to be synchronized with 
# (mirrored to) my external ext3 usb disk:
# 
# /home/<username>/docs (small)
# /home/<username>/pics (small)
# /home/<username>/thor (large)
# /home/<username>/music (very large)
# 
# - can be executed by user (no need for sudo/root access)
# - other dirs (video, tgz, etc.) must be updated by hand
# 

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(1) Backing up docs..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/docs
rsync -vurt --progress --delete /home/<username>/docs/ /mnt/usbdevice/docs/

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(2) Backing up pics..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/pics
rsync -vurt --progress --delete /home/<username>/pics/ /mnt/usbdevice/pics/

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(3) Backing up thor..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/thor
rsync -vurt --progress --delete /home/<username>/thor/ /mnt/usbdevice/thor/

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(4) Backing up music..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/music
rsync -vurt --progress --delete /home/<username>/music/ /mnt/usbdevice/music/

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "All done!"

```

I run this script from ~/ but you can run it from wherever you like. Make sure the script is executable:
```
chmod 755 rsync.sh
```

Simply run, and everything will be mirrored to the USB drive.
```
./rsync.sh

```

Some explanation of the various rsync flags (info from rsync's man page):

-v: verbose - this flag makes rsync tell you what files it's moving and gives a summary at the end
-u: update - this forces rsync to skip any files for which the destination file already exists and has a date later than the source file 
-r: recursive - rsync will mirror the directories you specified and all the directories inside them.
-t: times - rsync will copy al the timestamps of the source files, so that the files on the external drive are exact replicas.
--progress: rsync will tell you how many files need to be copied before it's finished. this is useful if you want to see what's going on.
--delete: this tells rsync to delete any files on the receiving side that aren't on the sending side.

Remember, backup often! Linux makes it incredibly easy to do, unlike Microsoft products. And don't worry about files being 'in use,' that's a Windows ailment. rsync is a very powerful tool, and it's also useful for synchronizing to a network drive. It can exclude files if you choose, and the '-n' flag will let you preview changes before they are actually made. Read about rsync in the man page:
```
man rsync
```

---

### Post by Lunar_Lamp on 2006-08-14
Thanks for this.  I see nobody else has responded, but this is pretty much what I was looking for.  I too needed a simple backup solution, that was NOT automated (i.e. I just did it when I wanted to).  I knew rsync was what I needed to use, but this script has meant that I barelyhave to use any effort in reading the rsync man-pages to write my own!

---

### Post by senorJ on 2006-08-22
Thanks that's really useful and just what I needed right now.

As a linux noobie that was my first attempt at using a bash script and I can feel myself swelling with pride and self satisfaction ;)

Cheers
Jay

---

### Post by xander848 on 2006-08-23
You mentioned that the external drive had to be formatted at ext3. Could the partition that I am backing up from be FAT32 though?

---

### Post by djgrandmarquis on 2006-08-23
> **xander848 said:**
> You mentioned that the external drive had to be formatted at ext3. Could the partition that I am backing up from be FAT32 though?

Unfortunately, no. rsync does not play well with FAT32. I think there were issues with case sensitivity and time stamping. I couldn't get rsync to properly update the files incrementally; it just copied all the files. I've never tried it with FAT32 as the source drive, but I imagine the problems would be the same.

---

### Post by kefkakiller on 2006-08-29
Great guide, I think this is exactly what I need to sync my music on my laptop and my media server. I have one question on the -u flag, though. Am I correct in assuming that it will only update files with changed timestamps ie it will backup an mp3 whose ID3 tag has been changed, even though the filename is the same?

---

### Post by guymauve on 2006-08-29
Hi,

Any body get that problem... I am keeping lost connection with unison...

I reset ssh conf and keys, remove firewall (firestarter) set nat translating between both computer TCP UDP on, reset unison conf...

Nothing

Keep lost connection

The gui gtk interface ask for passwd and everything and when the authentification start, it pop lost connection...

Where could it coming from?

---

### Post by guymauve on 2006-08-29
I get by using unison in command line the error from bash :

bash: unison : commande introuvable

That mean that that it steel has some correction to do to the package since the package and invoking command change for :

unison-2.13.16

There should be a remaining unison command straigh somewhere that conflict with the ssh protocol...

After the answering of the user identification by openssh-server code somewhere....

???

Thanks for the correction if possible...

And sorry for the post in the midle of nowhere, I was no able to publish a new thread cause I just join the forum...

Guy

---

### Post by djgrandmarquis on 2006-08-29
> **kefkakiller said:**
> Great guide, I think this is exactly what I need to sync my music on my laptop and my media server. I have one question on the -u flag, though. Am I correct in assuming that it will only update files with changed timestamps ie it will backup an mp3 whose ID3 tag has been changed, even though the filename is the same?

Yes, I think you are correct. If you change an ID3 tag on your media server, the -u flag will overwrite the file on your laptop to reflect the changes. rsync compares the timestamps of files and updates them if the server's time stamp is newer than the client's. The -u flag ignores client files that have matching names and newer (or same) timestamps.

---

### Post by guymauve on 2006-08-29
Bug report here : [https://launchpad.net/distros/ubuntu/+source/unison/+bug/58134](https://launchpad.net/distros/ubuntu/+source/unison/+bug/58134)

Sorry for the missleading of this one...

Guy

---

### Post by hopstah on 2006-08-31
thanks so much for this.  i have been planning to purchase what will essentially become my backup server, but didn't know how to go about doing this.  this is great, and can also be made into a cron job.

---

### Post by pgmario on 2006-09-06
Nice how-to!
Do you have any suggestions on how to restore my system from a backup made with rsync? I would like it to be not incremental, since I want to have the exact system I backed up. Would a simple "cp -R * /targetdir" do the job? would all permissions be preserved that way? What about hidden files? Thank you!

EDIT: It's obviously "cp -Rp" to preserve the permissions etc, but can anyone confirm that this is everything I need to make sure everything is copied correctly?

---

### Post by djgrandmarquis on 2006-09-10
> **pgmario said:**
> Nice how-to!
Do you have any suggestions on how to restore my system from a backup made with rsync? I would like it to be not incremental, since I want to have the exact system I backed up. Would a simple "cp -R * /targetdir" do the job? would all permissions be preserved that way? What about hidden files? Thank you!

EDIT: It's obviously "cp -Rp" to preserve the permissions etc, but can anyone confirm that this is everything I need to make sure everything is copied correctly?

I think cp -Rp will do the trick, hidden files included. I'd also consult cp's man pages. You'll probably want begin with rm -R on  /targetdir to start with a clean slate.

---

### Post by pgmario on 2006-09-20
Thanks, I'll try it on occasion and tell you how it worked.

---

### Post by hopstah on 2006-09-21
you could just do a reverse rsync, but remove the 'u' flag on the end, and it should copy over everything.  But remember, neither cp nor rsync will remove files that have been created on your computer since the backup was made, so in order to get your computer 'exactly' as you had it, you would need to first remove all files from the target directory and then perform the cp or rsync.

---

### Post by firecat53 on 2006-09-21
Here's another way to skin the proverbial cat:

1. The rsync -a option covers the all of the "-rlptgoD" options.
2. I've read that keeping your backup partition or disk unmounted until you need it is good practice. However, using rsync, you MUST (learned the hard way :mad: ) make sure the partition is mounted first, otherwise you can delete an entire backup disk by accident.
3. Use rsync --modify-window=10 when dealing with vfat partitions.
4. You also have to check if a partition is currently mounted before trying to mount it again.

Here's one of my backup scripts run from cron (server in my house copying pix via Samba from our Windows desktop):

```
# Backup My Pictures to 30 G partition (just do every two weeks)
if [ ! -d /mnt/windows/My\ Pictures ]; then
   mount /mnt/windows
   if [ $? != "0" ]; then
        echo "Could not mount share"
        exit
   fi
fi

#mount the 30g partition to backup the pictures only
if [ `mount | grep /backup1 | wc -l` = 0 ]; then
  mount /backup1
  if [ $? != "0" ]; then
        echo "Could not mount share"
        umount /mnt/windows
        exit
  fi
fi

rsync -aq --delete --modify-window=10 /mnt/windows/My\ Pictures /backup1 >> /dev/null

umount /mnt/windows
umount /backup1

```

Good luck !
Scott

---

### Post by pgmario on 2006-09-22
> **hopstah said:**
> you could just do a reverse rsync, but remove the 'u' flag on the end, and it should copy over everything.Thanks!  > **hopstah said:**
> But remember, neither cp nor rsync will remove files that have been created on your computer since the backup was made.Isn't that what the "--delete" option is for?

> **firecat53 said:**
> 
1. The rsync -a option covers the all of the "-rlptgoD" options.
2. I've read that keeping your backup partition or disk unmounted until you need it is good practice. However, using rsync, you MUST (learned the hard way :mad: ) make sure the partition is mounted first, otherwise you can delete an entire backup disk by accident.
3. Use rsync --modify-window=10 when dealing with vfat partitions.
4. You also have to check if a partition is currently mounted before trying to mount it again.

Here's one of my backup scripts run from cron (server in my house copying pix via Samba from our Windows desktop):
Thanks for the advice and the script, looks exactly like what I was looking for.

---

### Post by HAARP on 2006-09-23
Here's my rsync backup script. Heavily modified from something I've found on the net. Feel free to post any improvements.

```
#!/bin/sh

if [ `id -u` != "0" ]; then
	echo "Not running as root!"
	exit 2
fi

# Separate with a space. Exclude trailing slash!
SOURCES="/"
TARGET="/media/hda2"

# dirs and files to be excluded, one per line.
# /proc/
# *.bak
EXCLUDE_FILE="/usr/local/sbin/backup-exclude.txt"

TARGETMOUNTED=0

echo "Verifying target..." 
if [ ! -x $TARGET ]; then
	echo "Backup target does not exist!"
	echo "Exiting..."
	exit 2
fi
if [ ! -d $TARGET/lost+found ]; then
	mount $TARGET
	echo "Backup target is not mounted. Mounting..."
	if [ ! -d $TARGET/lost+found ]; then
		echo "Backup target is not mountable!"
		echo "Exiting..."
		exit 2
	else export TARGETMOUNTED=1
	fi
else export TARGETMOUNTED=2
fi
echo "Target verified."

echo "Verifying sources..." 
for source in $SOURCES; do
	echo "Checking $source..."
	if [ ! -x $source ]; then
	echo "Backup source does not exist!"
	echo "Exiting..."
	exit 2
fi
done

if [ -f $EXCLUDE_FILE ]; then
EXCLUDE="--exclude-from=$EXCLUDE_FILE"
fi

echo "Sources verified."

for source in $SOURCES; do
		if [ ! -d $TARGET/$source ]; then
			echo "Mimicking sources directory hierarchy..."
			mkdir -p $TARGET/$source
		fi
	echo "Running rsync..."
	rsync --progress --exclude=$TARGET/ $EXCLUDE -a --delete $source/ $TARGET/$source/ "$@"
done
if [ $TARGETMOUNTED = 1 ]; then
	sleep 2
	umount $TARGET
	if [ -d $TARGET/lost+found ]; then
		echo "Backup target still mounted!"
		echo "Exiting..."
		exit 1
	fi
	echo "Backup target unmounted."
fi
if [ $TARGETMOUNTED = 2 ]; then
	echo "Backup target was mounted and will remain mounted."
fi

exit 0

```

---

### Post by happyisland on 2006-10-08
Thanks for the how-to! I was trying to figure this out using the manual and was having a hard time.

---

### Post by theseeker on 2007-02-11
If you prefer GUIs over terminal, you should try:

```
sudo aptitude install grsync
``` :D

---

### Post by jms830 on 2007-02-20
what could I add to the original script to backup my /home/<username> folder but exclude the Desktop folder? ie; What would I change in the following line?

```
ls /home/<username>
rsync -vurt --progress --delete /home/<username>/ /media/usbdisk/home/<username>/
```

---

### Post by Vil on 2007-02-25
Since I am backing up to a remote machine via ssh, I needed to change some things from the OP's script to get it to work.

Note: This isn't my actual script. I changed the OP's script in such a way as to illustrate how to make the appropriate modifications yourself.

Note 2: All changes are marked in bold print.

```
#!/bin/sh

# rsync.sh
#
# - this script will back up my 4 dirs that need to be synchronized with 
# (mirrored to) my external ext3 usb disk:
# 
# /home/<username>/docs (small)
# /home/<username>/pics (small)
# /home/<username>/thor (large)
# /home/<username>/music (very large)
# 
# - can be executed by user (no need for sudo/root access)
# - other dirs (video, tgz, etc.) must be updated by hand
# 

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(1) Backing up docs..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/docs
rsync -vurt --progress --delete /home/<username>/docs/ **<username>@<server-ip>:docs/**

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(2) Backing up pics..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/pics
rsync -vurt --progress --delete /home/<username>/pics/ **<username>@<server-ip>:pics/**

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(3) Backing up thor..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/thor
rsync -vurt --progress --delete /home/<username>/thor/ **<username>@<server-ip>:thor/**

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(4) Backing up music..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/music
rsync -vurt --progress --delete /home/<username>/music/ **<username>@<server-ip>:music/**

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "All done!"
```

If you are like me and have several GBs of stuff to back up for each operation and you are doing it via ssh, you may want to have festival "announce" that the operation is complete so that you know when to enter your password again if you are doing something else (assuming you have ssh set up to enter a password and not just use keys).

```
#!/bin/sh

# rsync.sh
#
# - this script will back up my 4 dirs that need to be synchronized with 
# (mirrored to) my external ext3 usb disk:
# 
# /home/<username>/docs (small)
# /home/<username>/pics (small)
# /home/<username>/thor (large)
# /home/<username>/music (very large)
# 
# - can be executed by user (no need for sudo/root access)
# - other dirs (video, tgz, etc.) must be updated by hand
# 

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(1) Backing up docs..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/docs
rsync -vurt --progress --delete /home/<username>/docs/ <username>@<server-ip>:docs/

**echo "Operation one complete." | festival --tts**
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(2) Backing up pics..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/pics
rsync -vurt --progress --delete /home/<username>/pics/ <username>@<server-ip>:pics/

**echo "Operation two complete." | festival --tts**
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(3) Backing up thor..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/thor
rsync -vurt --progress --delete /home/<username>/thor/ <username>@<server-ip>:thor/

**echo "Operation three complete." | festival --tts**
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(4) Backing up music..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/<username>/music
rsync -vurt --progress --delete /home/<username>/music/ <username>@<server-ip>:music/

**echo "Operation four complete." | festival --tts**
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "All done!"
```

---

### Post by djgrandmarquis on 2007-02-25
> **jms830 said:**
> what could I add to the original script to backup my /home/<username> folder but exclude the Desktop folder? ie; What would I change in the following line?

```
ls /home/<username>
rsync -vurt --progress --delete /home/<username>/ /media/usbdisk/home/<username>/
```

I'd probably use the flag --exclude=PATTERN or --exclude-from=FILE
Just create a text file called FILE (or whatever you like) and put the full path to your Desktop directory in it. rsync will then ignore all the directories in that file.

---

### Post by megamaced on 2007-03-03
Awesome! Thanks for the script

---

### Post by cotcot on 2008-04-09
Great, thanks for sharing your knowledge. I was searching for this to incremental backup photos.

---

### Post by vanadium on 2008-04-09
Why not simply use the -a switch? That switch is made for mirrorring a directory tree. All it takes is

rsync -a <source> <destination>

If you want some verbosity and want to delete files at the destination that do not exist anymore in the source, include the -v and --delete switches:

rsync -av --delete <source> <destination>

---

### Post by senor_smile on 2008-11-23
Having a problem with Rsync.  I have just used wubi to install Ubuntu 8.10 on my machine.  I used to use robocopy in windows to mirror one external usb 500 GB harddrive to another identical external drive.  For some reason, when I run rsync doing: 

```

rsync -vurt --delete --progress /media/SHAUN500 /media/HD-HSIU2
```

my second harddrive (the one mounted as HD-HSIU2) is running out of room.  I have browsed around and don't see any extra files.  I should have 174 GB free, but I now have only 23!  I actually escaped the rsync job as it doesn't seem to stop copying files.  

The other thing is, since I already had both drives in sync, I wouldn't expect that this job would take very long.  I started it last night and it was still running this afternoon.  

Any help would be greatly appreciated.  

Thanks, 

--shaun

---

### Post by djgrandmarquis on 2008-12-04
You already had them synced with rsync in the past?

What file system is on the drives?

---

### Post by senor_smile on 2008-12-04
I forgot I had posted here trying to solve that issue! 

The filesystems are fat32.  I had them in sync via robocopy, a similar program for windows systems.  I found out what my problem was though.  It was actually copying every file into a folder on the destination with the name of the root.  so, I have two drives mounted as:

/media/shaun500   &   /media/shaun500bak

I originally tried: 
```

rsync -av --delete /media/SHAUN500 /media/SHAUN500BAK
```

which was copying the contents of /media/shaun500 into /media/shaun500bak/shaun500.  I left out the forward slash!  Once I fixed it as:

```
rsync -av --delete /media/SHAUN500/ /media/SHAUN500BAK/
```

it works flawlessly.  


I also set up a cron job with:

```
crontab -e
```

and entered 
```
00 03 * * * rsync -av --delete /media/SHAUN500/ /media/SHAUN500BAK/
```

to have it sync at 3:00 AM every morning.

---

### Post by Ecclesia on 2008-12-07
Thanks for the script, that was perfect since you use the same arguments I would have eventually had to come up with.

I've run into a problem with rsync, however, I get a hard crash reliably a couple of minutes (sometimes less) into the transfer when trying to sync with a laptop running Debian (Etch) from my desktop (Intrepid).  Anyone have an idea why this would happen?  I've searched the forum and haven't seen anyone with similar issues.  I'm going to try to sync with a different machine and see if that makes a difference.

---

### Post by Ecclesia on 2008-12-07
Just to update from my last post.  I tried syncing from the same desktop to a machine running Intrepid and get the same hard crash.

---

### Post by Clochard on 2009-01-08
Sorry, no advice for crashes - I'm just learning too.

My question is about performance.  I'm seeing if I can use an rsync script that would be triggered when my media device is plugged in.  This script would sync my media device and library.

My library (~40GB) is in a CIFS share over a 100MB network connection that is used for very little else.

The first run of rsync took many hours (I gave up and went to bed).  Will subsequent runs be quicker?  I've just launched a second one after adding a single text file to one of the folders.  We'll see how quick this happens.  So far it is still indexing at 10 minutes and has only hit the "d" folders, so unless this is abnormal behavior, I don't think rsync will work very well.

Oh, another thing, gtkrsync is a nice way to have a GUI progress bar pop up when rsync is scripted.

So is this kind of performance expected for rsyncing 40GB of data?

---

### Post by any.linux12 on 2009-01-08
Hi!

I want to know if is possible to check the diference between 2 folders and save the file that have been modified to a third one.

Like if I have a Monday folder (with a full backup of my system) and on tuesday night I want a script that compare the content of my data souce (for ex. /fyle-server/*) and save (just the diferences) on the folder Tuesday.


Should be very nice to do this. Please comment this idea!

---

### Post by djgrandmarquis on 2009-01-08
> **Clochard said:**
> 
My question is about performance.  I'm seeing if I can use an rsync script that would be triggered when my media device is plugged in.  This script would sync my media device and library.

My library (~40GB) is in a CIFS share over a 100MB network connection that is used for very little else.

The first run of rsync took many hours (I gave up and went to bed).  Will subsequent runs be quicker?  I've just launched a second one after adding a single text file to one of the folders.  We'll see how quick this happens.  So far it is still indexing at 10 minutes and has only hit the "d" folders, so unless this is abnormal behavior, I don't think rsync will work very well.

Oh, another thing, gtkrsync is a nice way to have a GUI progress bar pop up when rsync is scripted.

So is this kind of performance expected for rsyncing 40GB of data?

No, I would expect an incremental rsync backup like this to finish very quickly.

However, I have had trouble with Windows file systems in the past. Somehow the timestamps are incorrect and rsync thinks everything needs to be updated. Therefore, I switched all my disks to ext3.

---

### Post by djgrandmarquis on 2009-01-08
> **any.linux12 said:**
> 
I want to know if is possible to check the diference between 2 folders and save the file that have been modified to a third one.

Like if I have a Monday folder (with a full backup of my system) and on tuesday night I want a script that compare the content of my data souce (for ex. /fyle-server/*) and save (just the diferences) on the folder Tuesday.


```

diff monday/ tuesday/ > tuesday/diff.txt

```

That will spit out the differences between the two directories, then redirect the output into a text file. I would recommend checking out the man page for diff, it has a lot of nice options.

---

### Post by any.linux12 on 2009-01-08
> 
Code:

diff monday/ tuesday/ > tuesday/diff.txt

That will spit out the differences between the two directories, then redirect the output into a text file. I would recommend checking out the man page for diff, it has a lot of nice options.

It's not quite what I was thinking but it could help
I will try then I tell you something 
Thanks

---

