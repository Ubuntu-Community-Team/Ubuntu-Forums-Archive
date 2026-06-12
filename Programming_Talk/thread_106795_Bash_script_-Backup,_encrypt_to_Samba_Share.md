---
title: "Bash script -Backup, encrypt to Samba Share"
date: 2005-12-21
forum: Programming Talk
---

### Post by anthro398 on 2005-12-21
I wrote this bash script to backup selected files and directories to a remote Samba share at work. Space is at a premium there so it uses tar and bzip2 to archive and compress objects. I also use Gnugpg, ( gpg, pgp) to encrypt the backup file prior to moving it to the shared drive. Bash verifies the existance of files and directories and feeds that to tar. Works pretty well and it's fairly robust. I thought someone might either find it useful for creating and encrypting backups or as a little tutorial to start manipulating files with bash scripting. I'm no expert, so let me know if you see a way to improve it.

You can download it at [www.braggtown.com/projects.html]("http://www.braggtown.com/projects.html")

```


#/bin/bash
#
# remote_backup.sh  
#
# Script to backup system to remote drive
# To decrypt: "gpg --output backup.tar.bz --decrypt backup.tbz"
# To uncompress: "tar -xvjf backup.tar.bz"
# http://www.prairienet.org/~jtuttle/

USER_HOME="/home/bubba"
REMOTEDIR="/mnt/h"
COPY="cp -a"            # Add v flag for verbose copying eg, "cp -av"
ARCHIVE="tar -cjf "        # Use tar and compress with bzip2 (add v flag for verbose operation)
GPGADDRESS="bubba@prairienet.org"
                # Append items to be archived to this list.  Mind the quotation marks
FILES="$USER_HOME/.mozilla/firefox/*.default
$USER_HOME/.mozilla-thunderbird/*.default
$USER_HOME/.gaim
$USER_HOME/.ssh
$USER_HOME/.gnupg
$USER_HOME/.scripts
$USER_HOME/.tomboy
$USER_HOME/.bash_aliases
$USER_HOME/Documents/work
/etc/hosts*
/etc/apache2/httpd.conf.local
/etc/apache2/apache2.conf"

                # If file/directory exists, append to list, else notify user
for file in $FILES
  do
    if [ -e $file ]; then
      FILE_LIST="$file $FILE_LIST"
    else
      echo "$file doesn't exist"
    fi
  done
                # Create tar file and compress with bzip2, which is slower but compresses farther
echo "Creating and compressing tar file"
$ARCHIVE $USER_HOME/backup.tbz $FILE_LIST

                # Use Gnupg to encrypt backup.  Comment out next 3 lines if not using encryption.
gpg -q -r $GPGADDRESS -e $USER_HOME/backup.tbz
echo "Backup encrypted"
                # rename *.tbz.gpg to *.tbz so as to not attract attention to use of encryption
mv $USER_HOME/backup.tbz.gpg $USER_HOME/backup.tbz



                # Mount remote drive to filesystem (will fail if unable to mount)
$USER_HOME/.scripts/mount-common.sh
echo "Mounted remote drive"

                #Check for existance of previous backups    
if [ -e $REMOTEDIR/backup.tbz ]
then    
    echo "Existing backup discovered. Moving backup to backup2..."
    mv $REMOTEDIR/backup.tbz $REMOTEDIR/backup2.tbz
    
else
    echo "No existing backup."
fi

    
                # Copy backup to remote drive
$COPY $USER_HOME/backup.tbz $REMOTEDIR/
                # Compare copy to original to confirm copy was successful
cmp -s $USER_HOME/backup.tbz $REMOTEDIR/backup.tbz
if [ $? -eq 0 ]         # Remove local archive and older copy on remote drive to conserve space
then echo "Move to remote drive successful!"  && rm -rf $USER_HOME/backup.tbz && rm -rf $REMOTEDIR/backup2.tbz
else echo "Move to remote drive unsuccessful!"  && $USER_HOME/.scripts/unmount-common.sh && exit 1
fi

$USER_HOME/.scripts/unmount-common.sh
echo "Unmounted remote drive"
echo "Backup Complete"
exit 0


```

---

