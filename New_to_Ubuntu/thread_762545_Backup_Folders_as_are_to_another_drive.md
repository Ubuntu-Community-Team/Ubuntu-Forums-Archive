---
title: "Backup Folders as are to another drive"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by mrwonx on 2008-04-22
I guess what I'm looking for is a program that will be both easy to install, and will take the contents of a few set folders and back themselves up on another Hard Drive I've set up. What the backup needs to be is an exact copy, not shrunk or compressed, in the folder. Updated nightly, changing the files themselves, instead of just added a new backup folder for that night.

I have a shared folder that I want to back up and share the backed up folder so that people working off the shared folders can go to this folder if they mistakingly deleted or messed up what they were working on.

---

### Post by scorp123 on 2008-04-22
Look at PowerFolder:
[http://www.powerfolder.com/](http://www.powerfolder.com/)

They have a free edition too which I suppose should be what you want?

---

### Post by mister_pink on 2008-04-22
All you need to do is use rsync and a cron job. Do "man rsync" in terminal to find out about it. "crontab -e" allows you to set up a cron job, google for the syntax. Ask here if you want some more help.

---

### Post by mrwonx on 2008-04-22
Ok, I tested the rsync and it's perfect, however when I went to work on the crontab -e, I ran into problems.

I entered what I thought was right, it went to save, and told me that it could save due to an error in the cronfile. Here's what I was telling it:

0 3 * * * rsync -av /dir-to-back /dir-backing-up-to

I have 3 I want to backup, but I tried it with a single entry also.

---

### Post by eldragon on 2008-04-22
there already exists a backup script that does something like with rsync.

it does incremental backups on a ext3 filesystem (relies on hardlinks to do this). its in the repos and its more simple to configure than parsing rsync some options :D

oh.. its called rsnapshot thats what i use, it relies on cronjobs too.

another one which also comes with a gui is unison. which is useful for 2-way folder sync, i use that for my notebook - desktop document sync.

hope i helped ;)

---

### Post by mrwonx on 2008-04-22
Can either of those be set up to automatically do that backup at a certain time? If so, I might just try those.

Easier setup the better since I might not be the only one have to troubleshoot the machine.

---

### Post by mrwonx on 2008-04-22
Installed rsnapshot, and I can't figure out how to open it to set things up.

Installed Unison, which does the job, but only manually. I need to have it do it by itself every night around 3am.

---

### Post by mrwonx on 2008-04-24
So I set it up and went to copy all the items from the other linux box we have over to this one with the shared drive. Copy and paste turned out badly since no one can access the files and save over them. I can use Unison to move them, but would the permissions move with them? Also still need a way to automate a backup copy.

---

### Post by zman58 on 2008-08-28
I have an automated backup solution that I have been using for some time now. It has been fully tested and is working very well. I have a backup script that gets run by root at 3:00 am every morning. A USB hard drive is attached to my system. If the USB drive is powered up, then the backup script will mount and provide backup services targeted to the drive.

So when I want backups to run, I just power up the drive before turning in for the evening. In the morning I power it down. I do this about once per week. It saves wear and tear on the backup drive. It could be left on continuously if desired and backups would occur nightly according to the root cron job. In my case, the backup script is executed at 3:00am each morning. A log file details the progress and results of the backup job. Details can be found here.

[http://home.neo.rr.com/zahorec/downloads/gatekeeper_Ubuntu_8.04_server_config_2008-07-04.tar](http://home.neo.rr.com/zahorec/downloads/gatekeeper_Ubuntu_8.04_server_config_2008-07-04.tar)

Just download the tar file I have above and extract the script called "backup" which is located in the /root/bin directory of the tar file. There are instructions on how to set it up in the script itself. If you are looking for an automated backup solution, then you will really like this. It is part of my home server setup which I have also documented here.

[http://home.neo.rr.com/zahorec/gatekeeper.html](http://home.neo.rr.com/zahorec/gatekeeper.html)

Here is the latest backup script text from the tar file above...
I keep updates available at my website above.

```

#!/bin/bash
#
# backup script for gatekeeper
#
# This shell script provides an automated backup process for backing up a
# system to an external USB hard drive. The script is designed to be run by
# root for the purpose of backing up data in a given directory and below. This
# script will attempt to mount standard /dev points for USB drives. The
# assumption for the backup volume is that it will be the first partition on
# any given drive.  This script mounts the volume (if necessary), backs up
# files to it using rsync, then unmounts the volume (if it mounted it). The
# backup drive must have a special file on it before this script will use it
# for a backup media target (see details below).
#
# Author: Kenneth W. Zahorec
# Website: http://home.neo.rr.com/zahorec/
# License: GPL v2.0 or greater.
# Copyright 2008 - Kenneth W. Zahorec
################
# History:
#
# backup v1.4 - 2008-06-28
#	Cleanup of some additional items and renamed usb mountpoints.
#
# backup v1.3 - 2008-06-24
#	Rewrote significant parts of the script to better handle other possible
#	mount points for /dev on USB.  The script now indexes through a
#	possible list of mount points in the file system.  Also included conditional
#	unmounting to prevent unwanted unmount operations when the volume is already
#	mounted before backup script is executed.
#
# backup v1.2 - 2008-06-15
#	Improve log data at start and end for better
#	readability.
#
# backup v1.1 - 2008-06-06
#	Added timestamp at beginning and end of script
#
# renamed to backup v1.0 - 2008-06-05
#	added information for logrotate
# 
# backup_job version 1.5 - 2008-05-23
#	Corrected iptables config file backups to /etc/arno-iptables-firewall .
#
# backup_job version 1.4 - 2007-01-13
#	- Changed rsync -l option to -L to support new
#	Ubuntu 7.10 server system with symlinked /home/public
# 	- Added /root to backup_dirs
#
# backup_job version 1.3 - 2007-11-26
#	Added new directories to be backed up.
#
# backup_job version 1.2 - 2007-11-21
#	Minor cleanup and allow for multiple source directories
#
# backup_job version 1.1 - 2007-11-18
#	Corrected check for root. Use $LOGNAME instead of $USER
#
# backup_job version 1.0 - initial version 
#
# License: GNU Public Licence version 3. GPL v3
# Licence text can be found at the Free Software Foudation website.
#	http://www.fsf.org/
#
###################################################################
# 
# USAGE:
# A mountpoint in the system must be established for the USB drive before this
# backup script can be used.  As root create a list of possible mountpoints
# in the system and add an entry into /etc/fstab for each as below...
#
#  device     mountpoint         filesystem     options
#
# /dev/sdb1  /media/usb_1  auto          rw,user,noauto 0 0
# /dev/sdc1  /media/usb_2  auto          rw,user,noauto 0 0
# /dev/sdd1  /media/usb_3  auto          rw,user,noauto 0 0
# /dev/sde1  /media/usb_4  auto          rw,user,noauto 0 0
#
# As root, create the mountpoints in the system as listed above. These
# mountpoints will be used by this script to find the backup media. The script
# will sequentially walk through the devices at the respective mountpoints to
# determine which is the backup media and will then perform the backup
# processing with the target set to the proper backup media mountpoint target.
#
# This example assumes that the backup media will be the first partition of an
# external USB hard drive. USB hard drives normally mount into the dev file
# system as /dev/sd* as shown above. In this case /dev/sda1 was not included
# because the system drive is a serial ATA (SATA) drive which resides on the
# /dev/sda* device node(s). In this particular case, we don't want to include
# the system drive as a backup media target candidate. In another situation we
# might actually want to do this--backup data to another partition on the same
# drive that system data is located.

######## Invocation of the backup script ########################
# This script can be invoked directly as root or run at regular intervals
# by entry into the root crontab.
#
# Crontab entry example:
# 0 3 * * * /root/bin/backup_job >>/var/log/backup.log
# 
# This entry will run the backup job at 3:00 AM every day and log
# results to file /var/log/backup.log.

######## Rotation of the backup.log file #########################
# For log rotation you can create a logrotate config file called
# /etc/logrotate.d/backup
#
# In this file place the following entries...
#
# /var/log/backup.log {
#   rotate 6
#   weekly
#   compress
#   missingok
#   notifempty
# }
#
# For details see man page for logrotate.
#
####################################################################
# SCRIPT variables...
#
# BACKUP_DRIVE_ID is a file that must exist in the root of the backup mount
# point to designate it as the backup drive media. We do not want to accidently
# back up to the wrong media or mount point. The backup script only checks for
# existance of this file. 

BACKUP_DRIVE_ID=gatekeeper_backup_drive

# BACKUP_MOUNT_POINT_LIST defines possible mount points in the system for the backup drive.

BACKUP_MOUNT_POINT_BASE="/media/usb_"
INDEX_LIMIT=4

# BACKUP_LIST is the list of items that will be backed up from the system to
# the backup media.  This is a list of directories and/or files that will be
# processed by the backup script. Directories will be recursed. Individual
# files will be directly processed.

BACKUP_LIST="
/home
/root
/etc/arno-iptables-firewall
/etc/fstab
/etc/dhcp3
/etc/bind
/etc/samba
/etc/init.d
/etc/rc2.d
/etc/logrotate.d/backup
"

# BACKUP_TARGET holds the name of the directory that will be the target for the
# backup data on the backup drive.

BACKUP_TARGET=BACKUP_DATA

# Begin script processing here...
echo ""
echo "****** Begin backup script processing. *******"
date
echo "$0: we will attempt to process the following items:"
for item in $BACKUP_LIST
do
	if [ -e $item ]
	then
		ITEM_LIST=$ITEM_LIST" "$item
		echo "    $item"
	else
		echo " INFO: '$item' will be ignored because it does not exist on source drive."
	fi
done
echo "Backup sources will be as follows:"
echo "$ITEM_LIST"

# Make sure we are being run as root
if [ "x$LOGNAME" != "xroot" ]
# if [ "x$LOGNAME" != "x$LOGNAME" ]
then
	echo "ERROR: Script invoked by $LOGNAME. This script should be run by root."
	exit 1
fi

FOUND="false"
DONE="false"
INDEX="0"
SCRIPT_MOUNTED="false"

echo "INFO: Looking for a backup drive volume from the list of possible mount points provided..."
# Find the backup media mount point or give up trying...
until [ "$FOUND" = "true" ] || [ "$DONE" = "true" ]

do
	let "INDEX += 1"
	BACKUP_MOUNT_POINT="$BACKUP_MOUNT_POINT_BASE$INDEX"
	# Warn if backup drive is already mounted. This could be a problem if the
	# wrong drive is mounted. Normal condition at this point is unmounted drive.
	if grep -q $BACKUP_MOUNT_POINT /etc/mtab 
	then
		echo "INFO: $BACKUP_MOUNT_POINT is already mounted."
		MEDIA_MOUNTED="true"
	else
		# attempt to mount backup drive
		if mount $BACKUP_MOUNT_POINT
		then
			echo "INFO: Mounted $BACKUP_MOUNT_POINT"
			MEDIA_MOUNTED="true"
			SCRIPT_MOUNTED="true"
		else
#			echo "INFO: Unable to mount volume at $BACKUP_MOUNT_POINT"
			MEDIA_MOUNTED="false"

		fi
	fi
	
	# If the volume is mounted, then interrogate it.
	# Check to make sure we have identified a valid backup drive volume...

	if [ $MEDIA_MOUNTED == "true" ]
	then
		if [ -f $BACKUP_MOUNT_POINT/$BACKUP_DRIVE_ID ] 
		then
			echo "  Mount point identified with id file at \"$BACKUP_MOUNT_POINT/$BACKUP_DRIVE_ID\""
			FOUND="true"
		else
			echo "WARNING: The mounted volume at $BACKUP_MOUNT_POINT was not identified with id file $BACKUP_DRIVE_ID"
			echo "  If you wish to use this volume as a backup, then you must first write the id file to it."
			# If we are responsible for mounting the invalid volume, then we will attempt to unmount it.
			if [ "$SCRIPT_MOUNTED" = "true" ]
			then
				echo "  unmounting $BACKUP_MOUNT_POINT ..."
				if umount $BACKUP_MOUNT_POINT
				then
					echo "  ...successfully unmounted $BACKUP_MOUNT_POINT"
				else
					echo "WARNING: failed to umount $BACKUP_MOUNT_POINT"
				fi
			fi
		fi
	fi

	if [ $INDEX -ge $INDEX_LIMIT ]
	then
#		echo "WARNING: We have tested all possible backup media volumes."
		DONE="true"
	fi
done

if [ $FOUND == "true" ]
then
	# everything looks good to this point. Invoke rsync to perform the backup operation...
	# r-recursive l-copySymlinks t-preserveTimes --modify-window=1sec(timestamp resolution) --dry-run(optional)
	echo "rsync will now be called..."
	echo "rsync -rLvt --exclude=.* --modify-window=1 $ITEM_LIST $BACKUP_MOUNT_POINT/$BACKUP_TARGET"
	rsync -rLvt --exclude=.* --modify-window=1 $ITEM_LIST $BACKUP_MOUNT_POINT/$BACKUP_TARGET
	# If we are responsible for mounting the backup volume, then we will attempt to unmount it.
	if [ "$SCRIPT_MOUNTED" = "true" ]
	then
		echo "  This script will now attempt to unmount the volume..."
		if umount $BACKUP_MOUNT_POINT
		then
			echo "$BACKUP_MOUNT_POINT successfully unmounted."
		else
			echo "WARNING: $BACKUP_MOUNT_POINT failed to unmount!"
		fi
	fi
else
	echo "ERROR: No backup media found. Check the backup device hardware please!"
	date
	echo "****** End backup script processing. *******"
	exit 1
fi
# we are done...
date
echo "$0: script has completed!"
echo "****** End backup script processing. *******"
exit 0

```

Hope that helps!

---

### Post by fingaz on 2008-09-16
Hi all!

With regards to your post zman58;
I'm pretty up with this Linux stuff after being dumped into it about 6 months ago :)

You're script has saved me alot of thinking (and scripting for that matter, even if the script links aren't up atm =D ), the only thing i was looking at at the moment was an adaptation of this script whereby, the script will backup to say USB drive 1, then afterwards look for a USB Drive 2; until exhausting all mount points- so the same backup location can be copied onto 5-6 external USB destinations, one by one.

Without going into too much as its a touch strange; The reason for this is i have a system at the moment where files are being updated by another application on a regular basis; and this needs to be cloned onto several hard drives fairly regularly (every 20 - 30 mins ideally) in a hot-swappable manner for taking away from site; When one drive is removed, another will be connected. What i'm trying to avoid though is having the script accessing/updating all the USB HDDs at once.

I was wondering if theres an option to simply add detection on the next index number and effectively continue the script from the start ignoring index 1, etc.

The easiest way i presume would be to copy the entire script from beginning to end, replicate this into the same script (or alternate script to be run seperately) and set the index to 2-6, then 3-6, 4-6 etc until cron calls the job again for 1-6. 

Hope this makes sense? :S lol
FingAZ.

---

### Post by zman58 on 2008-12-22
Hello FingAZ,
It seems reasonable that the backup script could be converted to provide this. Instead of finishing the loop on the first identification of backup media, it could continue in a sequential manner searching the other mount points for backup media. At completion of the script, all backup media targets would have full backup data written to them with all drives unmounted and ready for removal. If you need help with this, then please visit my website, email me to discuss and exchange ideas.

---

### Post by fingaz on 2009-01-04
I managed it in the end;

```

for i in sda1 sdb1 sdc1 sdd1 sde1 sdf1
do

echo "Ensuring mount point for $i are present and creating if not."
cd /clone/$i || mkdir /clone/$i
sleep 2
cd /
if mount /dev/$i /clone/$i
then
echo "Hard drive $i mounted successfully."

echo "Copying Files..."
rsync -rtv --progress --modify-window=1 /SOURCE /clone/$i/DESTINATION/
echo

else
echo "Hard drive not detected"
fi
done

```

---

