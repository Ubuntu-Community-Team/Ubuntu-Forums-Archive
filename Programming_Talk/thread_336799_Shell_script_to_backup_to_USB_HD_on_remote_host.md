---
title: "Shell script to backup to USB HD on remote host"
date: 2007-01-12
forum: Programming Talk
---

### Post by misterpms on 2007-01-12
*Moved from the Absolute Beginners Thread.*

I'm having trouble creating a script to back up my files to a removable USB harddrive attached to a remote machine. I've already made a shell script to backup my files to the remote machine (not the USB HD), I put it into a crontab and it works fine. The code for daily_backup.sh is below:
```

#!/usr/bin/sh
#Author: misterpms
#Date: 08-01-2007
#NOTE: The exclusion of hidden files is very crude. It might
#be more prudent to make a file with exclusion regexps

#Backup Host
HOST='xxx.xxx.xxx.xx'

#Source Folders
SRC="$HOME/ToBackUp/"

#Destination Folders
DEST="$HOME/Backup/"

#Rsync options
#-a, archive mode; -v, increase verbosity; 
#-z, compress file data during the transfer
OPTIONS='-avz'

rsync $OPTIONS -e 'ssh' --exclude='.*' $SRC $HOST:$DEST

```

However problems arose when I tried to modify the file to store my files on the USB HD; Ideally I'd like a script that can be put into a weekly cron. The relevant (remote machine) /etc/fstab of the USB HD is
>  /dev/sda2       /media/usb      ext3     defaults,user,noauto  0  0

I've tried sshfs, but I couldn't mount the USB HD on my local machine (mentioned in the how-to that I was following). I then googled for over an hour, but gave up and decided to try the following:
> 
ssh misterpms@$HOST "mount /dev/sda2" 
sh daily_backup.sh
ssh misterpms@$HOST "umount /dev/sda2"

it's very crude, but it works (with the appropriate modification of the DEST variable). Is there a better way to do what I need ?

Thanks in advance!

NB: I can't change the /etc/fstab on the remote machine (an auto option would make life much simpler!) and a few people will be using the USB HD backup script so using sshfs to mount locally may be out of the question.

---

### Post by kidders on 2007-01-12
Hi there,

I'm not completely sure I have what you'd like to do straight in my head. It sounds like you want to back up stuff onto an external device on a remote machine ... which would be no different than backing up onto an *internal* device, except that you're never going to be quite sure whether someone else is using it locally at the time. Does that sound right?

From your o/p it seems like the actual backing up is easy for you ... the wrinkles are:

[LIST]
[*]You can never be sure whether the remote USB device is mounted.
[*]You can't even be sure it's plugged in.
[*]It might or might not be safe to *un*mount it, given that someone might be using it.
[*]There might not be enough space on it for the backup.
[/LIST]

This might be over-complicating things, but I would seriously think about a two-step backup:

[LIST=1]
[*]Your local cron job copies your data to, say, /tmp/dropbox on the remote box.
[*]A process running remotely monitors /tmp/dropbox for changes.
[*]The remote process waits for the USB device to be both plugged in and idle.
[*]The contents of /tmp/dropbox are moved to /media/usb.
[/LIST]

That way, your local cron job will always succeed (and finish quickly), and you won't annoy anyone using the destination computer locally, by slowing down their I/O, or messing with the free space on the USB disk.

Would something like that be over the top?

---

### Post by misterpms on 2007-01-12
Thanks for the reply! Your interpretation of my situation is correct. 

I hadn't thought about a two-step backup process and it seems prudent to follow a similar scheme. I don't know how willing the user of the remote machine is to let me muck around with it a bit to get the monitoring script running, so I will try to do as much as I can from my side. 

This is what I'm executing now, it works and the logic seems somewhat sound; if the mount is successful then the backup script will run; I'm hoping that this will take care of the first three "wrinkles", I'll look into ironing out the fourth.

```

ssh $USER@$HOST "mount $MNTPOINT" && ./daily_backup.sh $DEST && \
ssh $USER@$HOST "umount $MNTPOINT"

```

Thanks again,
misterpms

---

### Post by kidders on 2007-01-12
Hey again,

> **misterpms said:**
> I don't know how willing the user of the remote machine is to let me muck around with it a bit to get the monitoring script runningYou wouldn't really have to do any messing about ... if you have SSH access (which you seem to), you can run anything as a background process.

> **misterpms said:**
> ```

ssh $USER@$HOST "mount $MNTPOINT" && ./daily_backup.sh $DEST && \
ssh $USER@$HOST "umount $MNTPOINT"

```

The biggest problem with this is that your backup job will fail completely if the USB filesystem is already mounted, which will generally be the case, unless whoever used it last was kind enough to dismount it when they were done ... even if they weren't planning to unplug it. Say you run your backup every second week, for the sake of argument. The most important thing from your point of view will probably be knowing that your files were transferred *somewhere* on the remote machine, even if they're not quite where they're supposed to be. If I were in your shoes, I'd try to ensure that the actual transfer of files was guaranteed to be successful all the time, which is why the two-step approach occurred to me.

Anyhow, putting that aside, how about replacing your mount/unmount commands with something a little "smarter"?

```
DEVICE="/dev/sda2"

if [ -z "`mount | grep "^$DEVICE"`" ]; then
        mount $DEVICE
        UNMOUNT=1
else
        UNMOUNT=0
fi

DEST=`mount | grep "^$DEVICE" | cut -d " " -f 3`

# Prevent the filesystem from being dismounted by someone else
cd $DEST

# ...
# ...
# ...

if [ UNMOUNT -eq 1 ]; then
        umount $DEVICE
fi
```

This would mean your backup would still go ahead if the target device was already mounted, and the "cd" command would prevent whoever mounted it from swiping the filesystem out from under you, because the kernel considers a pwd (working directory) to be an open file. Also, you would only try to unmount something you mounted yourself.

I suppose the amount of trouble you go to with your script depends on how many odd circumstances you want to be able to handle. For instance, what if /dev/sda is missing ... or worse, what if this happens:

[LIST=1]
[*]Someone plugs out the USB hard disk.
[*]Someone plugs in an iPod.
[*]Someone says "Oh heck... the hard disk needs to be there, in case misterpms does a backup", and plugs the USB hard disk back in.
[/LIST]

Now, /dev/sda2 will map to one of the iPod's partitions, while the backup destination moves to /dev/sd**b**2.

Anyhow, I'm happy to help you out ... the big questions, though, are these:

[LIST]
[*]Would you mind if your backup failed from time to time?
[*]How bad would it be if it interfered with local operation of the destination computer?
[*]Is rock-solid reliability of paramount importance?
[/LIST]

---

### Post by misterpms on 2007-01-12
In regards to your suggested mounting method, I understand what is going on but am I to execute it on my machine (after ssh'ing) or do I execute it on the remote machine ? It seems that I have a lot more reading to do before I can write a robust script: ssh, executing a series of commands on a remote host etc. Can you recommend other topics that I should be looking into ?

> 
Anyhow, I'm happy to help you out ... the big questions, though, are these:

[LIST]
[*]Would you mind if your backup failed from time to time?
[*]How bad would it be if it interfered with local operation of the destination computer?
[*]Is rock-solid reliability of paramount importance?
[/LIST]


I would mind if the backup failed as it's being used to store my laboratory's research files. The backup script will be execute once a week at a time when no-one is logged on, so I'm not too concerned about impacting it's operation. The backups should be robust.

Thanks for your help!

---

### Post by kidders on 2007-01-13
> **misterpms said:**
> In regards to your suggested mounting method, I understand what is going on but am I to execute it on my machine (after ssh'ing) or do I execute it on the remote machine ?On the remote machine.

> **misterpms said:**
> It seems that I have a lot more reading to do before I can write a robust script: ssh, executing a series of commands on a remote host etc. Can you recommend other topics that I should be looking into ?There's lots of help with shell scripting on the web. The nice thing about it is that it's *waaaay* more flexible than what your typical windoze user is used to, so chances are, if you can think of something, there's a web page out there that shows you how to do it. :-)

> **misterpms said:**
> I would mind if the backup failed as it's being used to store my laboratory's research files.Oh. For all I knew, you were backing up saved games from Tetris. That changes things a little. :-k

See what you think of the following:

[LIST=1]
[*]Make a gzipped tarball of your data.
[*]SCP it to your home directory on the remote machine.
[*]Check to make sure nothing's funny about the remote USB disk.
[*]Unpack the tarball onto the USB disk.
[/LIST]

If your data are large and infrequently modified, this will be far less efficient that using rsync, but (a) you can be 100% sure you have a complete copy of your data, and (b) it's important that taking the snapshot of your files happens as quickly as possible, to minimise the chances that something could be modified while it's happening.

Anyhow, see what you think of this...

```
#!/bin/bash

ARCHIVE="~/backup_`date +"%Y%m%d%H%M"`.tar.gz"
SOURCE="/path/to/data"
DEST="user@1.2.3.4"
PUBKEY="/path/to/.ssh/id_rsa"
REMOTE_HELPER="~/test"

# Make a complete, self-contained copy of your data.
function make_backup {
	if [ -r "$SOURCE" ]; then
		tar -czf "$ARCHIVE" "$SOURCE"
		return $?
	else
		echo "$SOURCE not readable."
		return 1
	fi
}

# Copy the archive remotely without choking its internet connection.
function copy_backup {
	scp -Bq -l 512 -i "$PUBKEY" "$SOURCE" "$DEST:."
	return $?
}

# Launch remote helper script
function finalise_backup {
	ssh -fN -i "$PUBKEY" $DEST "$REMOTE_HELPER"
	return $?
}

# Stage 1
make_backup
if [ $? -eq 0 ]; then
	# Stage 2
	copy_backup
	if [ $? -eq 0 ]; then
		# Stage 3
		finalise_backup
		if [ $? -eq 0 ]; then
			exit 0
		else
			echo "Couldn't launch remote script"
			exit 3
		fi
	else
		echo "Couldn't back up to $DEST"
		exit 2
	fi
else
	echo "Couldn't create archive of $SOURCE"
	exit 1
fi
```

Now, regardless of any funny business that might be going on with the remote machine (USB devices are, after all, terribly unreliable), you have a complete copy of your data on the remote box, labelled with the backup date. Non-zero exit codes help things like cron realise something's gone wrong.

On the remote box, you could execute something like this:

```
#!/bin/bash

UUID="f191663b-7fec-4092-bede-caeb08a03844"

# Find (and maybe mount) the target device
function find_device {
	NODE="`find /dev/disk/by-uuid/ -type l -name $UUID -printf "%l"`"
	if [ -n "$NODE" ]; then
		NODE="/dev/`basename $NODE`"
		if [ -z "`mount | grep "^$NODE"`" ]; then
			mount $NODE
			EC=$?
			eval "$2=1"
		else
			# If the USB filesystem is FAT, we should abort here!
			EC=0
			eval "$2=0"
		fi
		eval "$1=`mount | grep "^$NODE" | cut -d " " -f 3`"
	else
		echo "Target device (UUID=$UUID) not connected."
		EC=1
	fi
	return $EC
}


find_device MOUNT_POINT SHOULD_UNMOUNT
if [ $? -eq 0 ]; then

	# Ready to unpack
	echo $MOUNT_POINT
	echo $SHOULD_UNMOUNT

else
	echo "Couldn't find target device or target device failed to mount."
fi
```

By the time this script gets to the "Ready to unpack" comment, you know where the USB disk is at, in a way that is immune to variation in remote system configuration, and you know whether to unmount it when you're done. Now, you can choose whether you want to keep multiple complete backups, or replace the last backup with the new one. You could then finish with a "sendmail" command, to have the remote box mail you a reassuring message.

Given that tarballing your data has the potential to be so inefficient, it might be worth explaining why I'm suggesting it:

**Scenario 1**
The internet connection between you and the remote box is uncharacteristically slow, and the rsync takes 3 hours, rather than 3 minutes. This dramatically increases the probability that the source data will be modified during the course of the backup, leading to inconsistencies.

**Scenario 2**
There is limited space available on the remote USB disk. Tarballing your data first makes deciding whether it will fit far more straightforward.

**Scenario 3**
You do something silly and accidentally erase something vitally important this Friday night ... only you don't notice until Monday morning. Over the weekend, the backup script syncs the remote copy of your data with the local one, erasing both copies. By keeping all your tarballs (or even just the last 5), rather than just syncing a single copy, you can protect against accidental deletions.

**Edit:** I hope I haven't made any mistakes with this code ... *please* check!! With luck, these scripts will be a helpful starting point ... I've tried to take account of the limited administrative control you have over the remote box, and make the code reasonably robust.

---

### Post by misterpms on 2007-01-14
Thank you so much for your help with this. I've learnt quite a bit from just thinking about your recommendations and design.

> **kidders said:**
> On the remote machine.
There's lots of help with shell scripting on the web. The nice thing about it is that it's *waaaay* more flexible than what your typical windoze user is used to, so chances are, if you can think of something, there's a web page out there that shows you how to do it. :-)


It's the flexibility that I'm finding a bit daunting; I've been using linux for over 5 years as a student programmer, but never as someone who needs to do admin tasks, so things like the filesystem, mounting, cron, user groups etc. were never my concern; All I did was compile programs and write the odd shell script to coordinate things.

> 
See what you think of the following:

[LIST=1]
[*]Make a gzipped tarball of your data.
[*]SCP it to your home directory on the remote machine.
[*]Check to make sure nothing's funny about the remote USB disk.
[*]Unpack the tarball onto the USB disk.
[/LIST]

If your data are large and infrequently modified, this will be far less efficient that using rsync, but (a) you can be 100% sure you have a complete copy of your data, and (b) it's important that taking the snapshot of your files happens as quickly as possible, to minimise the chances that something could be modified while it's happening.


The first script is straight-forward, however I don't fully understand what is going on in the 
second script; I haven't come across UUID before. Can't I just look at the output of the mount command on the remote machine to determine whether the HD is mounted or not ? 

> 
Given that tarballing your data has the potential to be so inefficient, it might be worth explaining why I'm suggesting it:

**Scenario 3**
You do something silly and accidentally erase something vitally important this Friday night ... only you don't notice until Monday morning. Over the weekend, the backup script syncs the remote copy of your data with the local one, erasing both copies. By keeping all your tarballs (or even just the last 5), rather than just syncing a single copy, you can protect against accidental deletions.


I've been meaning to implement one for my backup scheme.

Thanks for your help! :-D

---

### Post by kidders on 2007-01-14
> **misterpms said:**
> Thank you so much for your help with this. I've learnt quite a bit from just thinking about your recommendations and design.:-)

> **misterpms said:**
> It's the flexibility that I'm finding a bit daunting; I've been using linux for over 5 years as a student programmer, but never as someone who needs to do admin tasks, so things like the filesystem, mounting, cron, user groups etc. were never my concern; All I did was compile programs and write the odd shell script to coordinate things.Yeah, I can understand that. It takes a while to get used to some of the admin-related stuff.

> **misterpms said:**
> I haven't come across UUID before.UUIDs (Universally Unique IDs) are a way of referring to things based on information they're storing about *themselves*. For example, just because a filesystem is mounted at /dev/sda2 today, doesn't mean that's where it'll be tomorrow. By referring only to the filesystem's UUID (and using it to extrapolate any other information you need), you avoid a very common gripe people have with Linux's devfs, namely that /dev entries for removable devices tend not to be static. If the owner of your backup target machine uses more than one USB device (camera, flash disk, iPod, etc.), /dev/sda2 may or may not point to what you think it does ... so it is often useful to take that into account.

> **misterpms said:**
> Can't I just look at the output of the mount command on the remote machine to determine whether the HD is mounted or not ?Yep :-) You can. It might be nice to make that automatic, but the choice is yours.

A more heavily commented version of the second script:

```
#!/bin/bash

# This should be the UUID of the remote USB filesystem.
UUID="f191663b-7fec-4092-bede-caeb08a03844"

# Find (and maybe mount) the target device
function find_device {
	
	# Find a /dev alias matching the remote UUID
	NODE="`find /dev/disk/by-uuid/ -type l -name $UUID -printf "%l"`"

	if [ -n "$NODE" ]; then
		
		# The search was successful - rewrite the alias a bit.
		NODE="/dev/`basename $NODE`"

		# Try to figure out if the USB disk is already mounted.
		if [ -z "`mount | grep "^$NODE"`" ]; then

			# Mount the USB disk now and store the "mount" command's exit code.
			mount $NODE
			EC=$?

			# Tell the function caller to unmount the disk when we're done.
			eval "$2=1"
		else
			
			# If the USB filesystem is FAT, we should abort here, because
			# we probably won't be able to write to it ... and the /etc/fstab
			# line provided forbids us to remount it ourselves.

			EC=0
			eval "$2=0"

		fi

		# Tell the function caller where the USB filesystem has been mounted.
		eval "$1=`mount | grep "^$NODE" | cut -d " " -f 3`"
	else
		echo "Target device (UUID=$UUID) not connected."
		EC=1
	fi
	return $EC
}


find_device MOUNT_POINT SHOULD_UNMOUNT
if [ $? -eq 0 ]; then

	# Ready to unpack
	
	# Here, you can either do a "tar -xzf...." or a simple "mv"
	# to put your backup where it's supposed to be. Your choice. :-)
	
	echo $MOUNT_POINT
	echo $SHOULD_UNMOUNT

else
	echo "Couldn't find target device or target device failed to mount."
fi
```

The only advantage all this code has over a simple "mount" instruction is that it is impervious to a wide range of system configuration changes on the remote machine. The only place it might fall down is that the mount command itself requires a corresponding entry in /etc/fstab.

---

