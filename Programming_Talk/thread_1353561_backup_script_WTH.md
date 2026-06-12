---
title: "backup script WTH???"
date: 2009-12-12
forum: Programming Talk
---

### Post by Barriehie on 2009-12-12
So I finally got a USB thumbdrive and after my backup is completed the script is supposed to erase the old files from the thumbdrive and copy the new ones to it.  It's copying the new ones but not rm'ing the old ones!  I'm the owner of the drive and the script is being run as root.  If I go to a terminal I can *rm /media/disk/bup** and the files are removed.  What am I missing here?????

TIA,
Barrie

```

#!/bin/bash
#

#
#  Find and remove  emacs backup files.
#
find / -iname *~ -user barrie -exec rm {} \;

#
#  Remove the thumbnails.
#
find /home/barrie -name .thumbnails -exec rm -rf {} \;

#
#  Nuke the Nautilus sessions
#  Leave 1 session files
#
# Specify the target directory and file names to operate on.
target_files=~/.nautilus/saved-session-*

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
target_files=~/.metacity/*

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
#  Do the Backup
#
BUPFILENAME=bup$(date +%m%d%y).tgz
INSTALLEDFILEZ="/home/barrie/Documents/"$(date +%m%d%y)-Installed_Packages.txt
dpkg --get-selections > $INSTALLEDFILEZ

mkdir /home/barrie/Desktop/Backup.log

tar cvpzf /home/barrie/disk/backup-files/$BUPFILENAME --exclude=/home/barrie/Desktop/backup.log --exclude=/home/barrie/disk /home/barrie 1>/home/barrie/Desktop/Backup.log/b1.log 2>/home/barrie/Desktop/Backup.log/b2.log

tar cvpzf /home/barrie/disk/backup-files/$BUPFILENAME-etc /etc 1>>/home/barrie/Desktop/Backup.log/b1.log 2>>/home/barrie/Desktop/Backup.log/b2.log

tar cvpzf /home/barrie/disk/backup-files/$BUPFILENAME-www /var/www/ 1>>/home/barrie/Desktop/Backup.log/b1.log 2>>/home/barrie/Desktop/Backup.log/b2.log

**rm /media/disk/bup***
cp /home/barrie/disk/backup-files/bup* /media/disk/

chown barrie:barrie /home/barrie/Desktop/Backup.log/b1.log
chgrp barrie /home/barrie/Desktop/Backup.log/b1.log

chown barrie:barrie /home/barrie/Desktop/Backup.log/b2.log
chgrp barrie /home/barrie/Desktop/Backup.log/b2.log

chown barrie:barrie /home/barrie/Desktop/Backup.log
chgrp barrie /home/barrie/Desktop/Backup.log

chown barrie:barrie /home/barrie/disk/backup-files/$BUPFILENAME
chgrp barrie /home/barrie/disk/backup-files/$BUPFILENAME

chown barrie:barrie /home/barrie/disk/backup-files/$BUPFILENAME-etc
chgrp barrie /home/barrie/disk/backup-files/$BUPFILENAME-etc

chown barrie:barrie /home/barrie/disk/backup-files/$BUPFILENAME-www
chgrp barrie /home/barrie/disk/backup-files/$BUPFILENAME-www

chown barrie:barrie /media/disk/bup*
chgrp barrie /media/disk/bup*

chown barrie:barrie $INSTALLEDFILEZ
chgrp barrie $INSTALLEDFILEZ

exit 0

```

Barrie

---

### Post by Barriehie on 2009-12-13
NM, this was my bad!  I wasn't removing the old files from ~/disk/backup-files... :(

Barrie

---

### Post by falconindy on 2009-12-13
You can use '-delete' instead of '-exec rm {}'. Better yet, 'man tar' and look at the exclude flag. You don't need to delete anything before archiving.

---

### Post by Barriehie on 2009-12-14
> **falconindy said:**
> You can use '-delete' instead of '-exec rm {}'. Better yet, 'man tar' and look at the exclude flag. You don't need to delete anything before archiving.

:)  I'm deleting the ones that are just taking up space!


Barrie

---

