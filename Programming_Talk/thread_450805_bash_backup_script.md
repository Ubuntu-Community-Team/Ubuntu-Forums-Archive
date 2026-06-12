---
title: "bash backup script"
date: 2007-05-21
forum: Programming Talk
---

### Post by dwanders on 2007-05-21
Do any of you guru's see anything potentially bad/harmful with the following script I have been working on to use as a backup script (any and all suggestions/comments greatly appreciated):

I am sure it could be written much more efficiently, but my main concerns are with things that could whack up my system or leave me with an unreliable backup script. 

#!/bin/bash
# This is a simple bash script to backup files on 
# the home computer. The backup system uses a spare
# HDD for the backup media rather than tape. 
#
# It is intended to be run from cron like:
#	(30 11 * * * backup.sh 2>log.file)
# The 2 above will only send stderr to the log
#
# The idea is to:
#	1) Mount a backup media drive (exit if fail)
#	2) Verify target file exists (exit if fail)
#	3) parse through target file
#	4) if new target
#		a) tar the target files up
#		b) gzip the new target
#	5) if not new, update the current tar file by
#		a) gunzip the archive
#		b) run tar update
#		c) gzip the file 
#	6) Unmount the backup file system
# 	7) verify un-mount
#	8) exit script
# echo date for start of log file
/bin/date

# Static global variables
backup_path=/mnt/backup/

#Begin Backup Functions
function check_target {
	if [ -f bu_targets.txt ]; 
	then
		echo "Target file exists."
		echo "... continuing ..."
	else
		echo "Cannot find target file."
		echo "... exiting ..."
		exit 0
	fi
}

function mount_drive {
	# Mount the data hard drive
	mount /dev/sdb1 /mnt/backup
}

function check_mount {
	# Check that the mount succeded
	if [ -a /mnt/backup/mount_test ]; 
	then
    	echo "Mount seemed to work."
    	echo "... continuing ..."
	else
    	echo "Mount failed."
    	echo "... exiting ..."
    	exit 0
	fi
}

function archive_targets {
	# Begin archiving/updateing targets 
	while read line;
	do
		PATH=${line%;*};
		ARCH_NAME=${line#*;};
		if [ -f "$backup_path$ARCH_NAME.tar.gz" ]; 
		then
			echo "The file $backup_path$ARCH_NAME.tar.gz exists"
			echo "start update process of: gunzip then tar update then gzip"
			/bin/gunzip $backup_path$ARCH_NAME.tar.gz && /bin/tar uvf $backup_path$ARCH_NAME.tar $PATH/* && /bin/gzip $backup_path$ARCH_NAME.tar
		else
			echo "The file does not seem to exist"
			echo "start process to create new tar file, gzip file"
			/bin/tar cvf $backup_path$ARCH_NAME.tar $PATH/* && /bin/gzip $backup_path$ARCH_NAME.tar
		fi
	done <bu_targets.txt
}

function unmount_drive {
	#Un-mount & verify un-mount of the spare file system
	echo "Un-Mounting"
	/bin/umount /mnt/backup
	
	# Verify unmount success
	while [ -a /mnt/backup/mount_test ]
	do
		echo "Un-Mount must have failed";
		echo "... sleeping for 30 seconds, then trying again ...";
		/bin/sleep 30;
		echo "... trying again ...";
		/bin/umount /mnt/backup;
	done
	
	echo "BackUp drive unmounted.";
	echo "... continuing ...";
}

function exit_script {
	#echo end date for log file & status
	/bin/date
	exit 1	
}

# Start Main program Execution
check_target
mount_drive
check_mount
archive_targets
unmount_drive
exit_script

The above uses another file for the targets, that is like:
/etc;system_etc
/root;system_root

Again, any suggestions or input is greatly appreciated.

---

### Post by Ramses de Norre on 2007-05-21
In your exit function, I think you mean **exit 0** instead of **exit 1**, 1 is an erroneous exit and 0 is a correct/normal exit.

---

### Post by dwanders on 2007-05-22
I changed my 1's to 0's and 0's to 1's - thanks. 

I also found out that for some reason the gzipped files in the end had bad crc's and would not open. So I added another 30 second sleep and it seemed to clear up. Also changed my tar command to:

/bin/gunzip $backup_path$ARCH_NAME.tar.gz 
&& /bin/tar uvf $backup_path$ARCH_NAME.tar -P --totals $PATH/* 
&& /bin/gzip $backup_path$ARCH_NAME.tar
else
echo "The file does not seem to exist"
echo "start process to create new tar file, gzip file"
/bin/tar cvf $backup_path$ARCH_NAME.tar -P --totals $PATH/* 
&& /bin/gzip $backup_path$ARCH_NAME.tar

And it now seems to be working fine. Any other suggestions/comments still greatly appreciated.

---

### Post by dwanders on 2007-05-22
I think I have determined that I had way too many ;'s in that script - so I removed the excess. Now I am wondering, is there a way I can check each step to ensure that it completes without problems e.g. after the tar, and each gunzip?

---

