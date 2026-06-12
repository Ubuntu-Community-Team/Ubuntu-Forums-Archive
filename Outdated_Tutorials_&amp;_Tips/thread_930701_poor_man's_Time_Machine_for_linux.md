---
title: "poor man's Time Machine for linux"
date: 2008-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by twade on 2008-09-26
This is something that has been covered a few times, but I thought I'd add my solution.  Mac OS X has a neat feature called time machine.  Basically it keeps backups as for everything as long as there is space, so not only do you have a recent backup of file X, you also have versions of it from a few days ago, few weeks ago, etc.  There are front ends that do something similar in Linux, but everything you need is on the command line, and it may give you better control (and at least it makes me feel more confident that the backups were done properly). You would need to make the original backup either with rsync or cp.  Comments on how to improve it are most welcome.

I got most of my ideas from:
[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync)

Basically the idea is to run this script once a day.  It keeps sequential backups by using hardlinking, and the most recent one is made using rsync.  It's a pretty dumb piece of code (i.e. you have to monitor the free space on the external and delete the oldest backups yourself), but it does what I need it to do.

```

!#/bin/sh

# bash script
# In this way all the PREV_BACK folders will contain hardlinks to
# old versions of the files, which are only fully deleted when all 
# links to them disappear. When rsync overwrites a file, the hardlink 
# in the older versions remain pointing to the old version

# the backup destination, an external drive
BACK_DIR=/media/external1/

# the backup source, your home folder
SOURCE_FOLDER=/home/user

# current date
DATESTR=`date +%y%m%d`

# the folder that will contain the new backup, labeled by date
# all backups need to be labeled similarly
CURR_BACK=${BACK_DIR}backup_${DATESTR}/

if [[ -e $BACK_DIR ]]
then
	echo
else
	echo
	echo "External not connected, aborting"
	exit
fi

echo 
echo "Current Backups Detected:"
i10=0
for FILE in ${BACK_DIR}backup*
do
	i10=$(($i10 + 1))
	FILES[i10]=$FILE
	echo $FILE
done
PREV_BACK=${FILE}/
OLD_BACK=${FILES[1]}/

echo
echo "Previous backup is:  $PREV_BACK"
echo "New backup will be:  $CURR_BACK"
echo "Oldest backup is:    $OLD_BACK"
echo "Source of backup is: $SOURCE_FOLDER"

# print the amount of free space
echo
df -h $BACK_DIR

# check to make sure backup not done yet today
if [[ -e $CURR_BACK ]]
then
	echo
	echo "$CURR_BACK exists, aborting"
	exit
fi

# get user to check for free space
echo
echo "Is there enough free space, yes to proceed"
read RESPONSECONTINUE
if [[ $RESPONSECONTINUE == "yes" ]]
then
	echo
	echo "Backup started"
else
	echo
	echo "Backup aborted"
	exit
fi


echo "moving folder"
mv $PREV_BACK $CURR_BACK
echo "hardlinking folder"
cp -al $CURR_BACK $PREV_BACK

# perform the rsync
# the file rsync_exclude contains the folders and files to 
# exclude from the backup, (internet caches, etc)
echo "starting rsync of $SOURCE_FOLDER"
rsync -av --delete $SOURCE_FOLDER $CURR_BACK --exclude-from '/home/user/rsync_exclude'

echo "backup of $SOURCE_FOLDER complete"

```

---

### Post by quattrorally on 2009-01-02
made the script executable and when I run it I get the following error:

malloc: ../bash/dispose_cmd.c:241: assertion botched
free: called with unallocated block argument
Aborting...Aborted

help would be greatly appreciated
thanks

---

