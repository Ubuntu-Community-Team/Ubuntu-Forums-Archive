---
title: "BASH mount point / dir testing ?"
date: 2010-03-14
forum: Programming Talk
---

### Post by Barriehie on 2010-03-14
Edit: NM!  I've just discovered the **mountpoint** command.

Hey All,
So I've got this backup script and went through it to make it portable but can't for the life of me resolve whether or not the $USBTHING exists!  I've tried:

```

if[ -d $USBTHING ]      with and w/out quotes around $USBTHING
if[ -f $USBTHING ]    as above
if[ $USBTHING != "" ]    as above
if[ $USBTHING ]    as above

```What am I missing???

TIA,
Barrie

**[COLOR=green]Corrected Script:[/COLOR]**
```

 #!/bin/bash
#
# BASH script to backup /home/barrie and /etc and get a list
# of installed files.  Files generated are saved on a seperate partition
# and also copied out to a USB drive.  Script is run as root so also
# CHOWN the /home/barrie files and the package list.
#


#
# Variable Setup   >> Edit to suit your locations <<
#
MYHOMEDIR=/home/barrie
BACKUPPLACE=/media/backup/backup-files
USBTHING=/media/disk
MYEMAIL=barrie@localhost
DT=$(date +%m%d%y)
mountpoint -q $USBTHING
ISUSB=$?


#
#  Find and remove emacs backup files, (system-wide).
#
find / -iname *~ -user barrie -exec rm {} \;


#
#  Remove ~/.electricsheep/*.xxx files
#  Comment out if not using electricsheep screensaver.
#
find $MYHOMEDIR/.electricsheep -name *.xxx -exec rm {} \;


#
#  Remove Thunar sessions
#
rm $MYHOMEDIR/.cache/sessions/Thunar*


#
#  Nuke the Nautilus sessions
#  Leave 1 session files
#
# Specify the target directory and file names to operate on.
target_files=$MYHOMEDIR/.nautilus/saved-session-*

# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=1

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi


#
#  Nuke the Metacity sessions
#  Leave 1 session
#
# Specify the target directory and file names to operate on.
target_files=$MYHOMEDIR/.metacity/sessions/*

# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)

# Specify the number of files to retain.
retained_files=1

# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi


#
# Remove all the 'normal' thumbnails
#
rm $MYHOMEDIR/.thumbnails/normal/*

#
# Uncomment the next two lines if not using --delete with rsync
# (rsync is next in /etc/crontab)
#
#rm -rf /media/backup/backup-files/barrie
#rm -rf /media/backup/backup-files/etc


#
# Empty the trash
#
rm $MYHOMEDIR/.local/share/Trash/files/*
rm $MYHOMEDIR/.local/share/Trash/info/*


#
#  Do the Backup
#
BUPFILENAME=bup$DT.tgz

dpkg --get-selections | gawk '{ print $1 }' > $BACKUPPLACE/Packages-$DT 2>$MYHOMEDIR/Desktop/backupErrors.log

tar cvpzf $BACKUPPLACE/home-$BUPFILENAME --exclude=$MYHOMEDIR/Desktop/backupErrors.log $MYHOMEDIR 2>>$MYHOMEDIR/Desktop/backupErros.log

tar cvpzf $BACKUPPLACE/etc-$BUPFILENAME /etc 2>>$MYHOMEDIR/Desktop/backupErrors.log


#
# Delete last backup files from USB device.
#
if [ "$ISUSB" -eq 0 ] ; then
    rm $USBTHING/*.tgz
    rm $USBTHING/Package*

#
# Copy to USB device
#
    cp $BACKUPPLACE/etc-$BUPFILENAME $USBTHING/
    cp $BACKUPPLACE/home-$BUPFILENAME $USBTHING/
    cp $BACKUPPLACE/Packages-$DT $USBTHING/
fi


#
# Since run as root, CHOWN
#
chown barrie:barrie $BACKUPPLACE/"home-"$BUPFILENAME
chown barrie:barrie $BACKUPPLACE/"etc-"$BUPFILENAME

if [ "$ISUSB" -eq 0 ] ; then
    chown barrie:barrie $USBTHING/*.tgz
    chown barrie:barrie $USBTHING/Packages*
fi

chown barrie:barrie $BACKUPPLACE/*.tgz
chown barrie:barrie $BACKUPPLACE/Packages*

chown barrie:barrie $MYHOMEDIR/Desktop/backupErros.log

#
# Empty the trash on USB device.
#
if [ "$ISUSB" -eq 0 ] ; then
    rm -rf $USBTHING/.Trash-0
fi


#
# Send me an email
#
echo ""|\mutt -s "backup completed ${DT}" $MYEMAIL

exit 0

```

---

