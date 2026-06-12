---
title: "problem with IF, THEN, ELSE statements in BASH program. help!"
date: 2007-07-20
forum: Programming Talk
---

### Post by syxbit on 2007-07-20
I'm writing a backup bash script (it's for a mac, but it should be mostly the same)
I'm having to actually edit an old script a guy wrote a while ago (who's left)
I'm having to add features.

right now, it's pretty complicated, as it does a "daily" backup that just backs up the home folder (but doesn't delete if the user deletes), then a "semesterly" backup that will (once a semester) sync the daily backup with what's currently on the hard drive

I'm having to make a manual backup, and I want it to just to a one way sync (if user deletes a file, I want it to delete it from the backup) - I haven't implemented this yet, because I can't seem to get that part of the code recognized at all

I added the last paragraph (#new code starts here)

could someone help me with my if, then, else statements, as it currently doesn't see "manual" as an option.


```

# First, check to see if it is a daily backup, or a semester backup
if [ $backup_type = "daily" ]; then
    # Now check to see if the destination for the backup is there
    if [[ -d /Volumes/$drive_name ]]; then
	# Print out some log junk
	echo "DailyBackup********************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Run the backup
	rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
    else
	echo "DailyBackup/wMount*************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Since destination is not mounted, make a directory in the /Volumes/ for the destination to be mounted to.
	mkdir /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Attempt to mount the destination for the backup
	/sbin/mount -t hfs -o local,nodev,nosuid,journaled /dev/`/usr/sbin/diskutil list | grep $drive_name | awk {' print $NF '}` /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Now check to see if it actually mounted or not
	if [[ `/sbin/mount | grep $drive_name | awk {' print $3 '}` = "/Volumes/$drive_name" ]]; then
	    # It mounted, so run the backup
	    rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Now that the backup is done, unmount the destination.  Remove the created directory only if the unmount was sucessful.
	    /sbin/umount -f /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	else
	    # The destination didn't mount, so print out some log junk again
	    echo "$drive_name didn't mount" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Remove the directory that was made to mount to.
	    rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	fi
    fi
# Do the same stuff as above, but for the semester backup.
elif [ $backup_type = "semester" ]; then
    if [[ -d /Volumes/$drive_name ]]; then
	echo "SemesterBackup*****************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	rsync -a $dry_run --delete --stats /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ /Volumes/$drive_name/Semester\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rsync -a --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
    else
	echo "SemesterBackup/wMount**********************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	mkdir /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	/sbin/mount -t hfs -o local,nodev,nosuid,journaled /dev/`/usr/sbin/diskutil list | grep $drive_name | awk {' print $NF '}` /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	if [[ `/sbin/mount | grep $drive_name | awk {' print $3 '}` = "/Volumes/$drive_name" ]]; then
	    rsync -a $dry_run --delete --stats /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ /Volumes/$drive_name/Semester\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    /sbin/umount -f /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	else
	    echo "$drive_name didn't mount" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Applications/Utilities/HTRSC\ Backup/Volumes/$drive_name/backup_log$number.txt
	fi
    fi
else
    print_help
fi


# new code starts here
# right now, the "manual" is the same as the "daily". I'll have to change the rsync to do what I want
# but for now, I need to fix the if,then,else stuff

elif [ $backup_type = "manual" ]; then
    # Now check to see if the destination for the backup is there
    if [[ -d /Volumes/$drive_name ]]; then
	# Print out some log junk
	echo "DailyBackup********************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Run the backup
	rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
    else
	echo "DailyBackup/wMount*************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Since destination is not mounted, make a directory in the /Volumes/ for the destination to be mounted to.
	mkdir /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Attempt to mount the destination for the backup
	/sbin/mount -t hfs -o local,nodev,nosuid,journaled /dev/`/usr/sbin/diskutil list | grep $drive_name | awk {' print $NF '}` /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Now check to see if it actually mounted or not
	if [[ `/sbin/mount | grep $drive_name | awk {' print $3 '}` = "/Volumes/$drive_name" ]]; then
	    # It mounted, so run the backup
	    rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Now that the backup is done, unmount the destination.  Remove the created directory only if the unmount was sucessful.
	    /sbin/umount -f /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	else
	    # The destination didn't mount, so print out some log junk again
	    echo "$drive_name didn't mount" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Remove the directory that was made to mount to.
	    rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	fi
    fi

```

---

### Post by syxbit on 2007-07-20
I think it's fixed now
here's my code (i did the if,else with some guessing till it worked)

```


# First, check to see if it is a daily backup, or a semester backup
if [ $backup_type = "daily" ]; then
    # Now check to see if the destination for the backup is there
    if [[ -d /Volumes/$drive_name ]]; then
	# Print out some log junk
	echo "DailyBackup********************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Run the backup
	rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
    else
	echo "DailyBackup/wMount*************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Since destination is not mounted, make a directory in the /Volumes/ for the destination to be mounted to.
	mkdir /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Attempt to mount the destination for the backup
	/sbin/mount -t hfs -o local,nodev,nosuid,journaled /dev/`/usr/sbin/diskutil list | grep $drive_name | awk {' print $NF '}` /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Now check to see if it actually mounted or not
	if [[ `/sbin/mount | grep $drive_name | awk {' print $3 '}` = "/Volumes/$drive_name" ]]; then
	    # It mounted, so run the backup
	    rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Now that the backup is done, unmount the destination.  Remove the created directory only if the unmount was sucessful.
	    /sbin/umount -f /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	else
	    # The destination didn't mount, so print out some log junk again
	    echo "$drive_name didn't mount" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Remove the directory that was made to mount to.
	    rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	fi
    fi
# Do the same stuff as above, but for the semester backup.
elif [ $backup_type = "semester" ]; then
    if [[ -d /Volumes/$drive_name ]]; then
	echo "SemesterBackup*****************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	rsync -a $dry_run --delete --stats /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ /Volumes/$drive_name/Semester\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rsync -a --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
    else
	echo "SemesterBackup/wMount**********************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	mkdir /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	/sbin/mount -t hfs -o local,nodev,nosuid,journaled /dev/`/usr/sbin/diskutil list | grep $drive_name | awk {' print $NF '}` /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	if [[ `/sbin/mount | grep $drive_name | awk {' print $3 '}` = "/Volumes/$drive_name" ]]; then
	    rsync -a $dry_run --delete --stats /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ /Volumes/$drive_name/Semester\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    /sbin/umount -f /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	else
	    echo "$drive_name didn't mount" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Applications/Utilities/HTRSC\ Backup/Volumes/$drive_name/backup_log$number.txt
	fi
    fi


elif [ $backup_type = "manual" ]; then
    # Now check to see if the destination for the backup is there
    if [[ -d /Volumes/$drive_name ]]; then
	# Print out some log junk
	echo "DailyBackup********************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Run the backup
	rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
    else
	echo "DailyBackup/wMount*************************************************************" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	date 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Since destination is not mounted, make a directory in the /Volumes/ for the destination to be mounted to.
	mkdir /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Attempt to mount the destination for the backup
	/sbin/mount -t hfs -o local,nodev,nosuid,journaled /dev/`/usr/sbin/diskutil list | grep $drive_name | awk {' print $NF '}` /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	# Now check to see if it actually mounted or not
	if [[ `/sbin/mount | grep $drive_name | awk {' print $3 '}` = "/Volumes/$drive_name" ]]; then
	    # It mounted, so run the backup
	    rsync -a $dry_run --stats /Users/$shortname /Volumes/$drive_name/Daily\ Backup\ \(DO\ NOT\ EDIT\)/ 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Now that the backup is done, unmount the destination.  Remove the created directory only if the unmount was sucessful.
	    /sbin/umount -f /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt && rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	else
	    # The destination didn't mount, so print out some log junk again
	    echo "$drive_name didn't mount" 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	    # Remove the directory that was made to mount to.
	    rm -fr /Volumes/$drive_name 1>>/Volumes/$drive_name/backup_log$number.txt 2>>/Volumes/$drive_name/backup_log$number.txt
	fi
    fi
else
    print_help
fi

```

---

### Post by phansiizwe on 2007-07-20
The problem was that

```

else
    print_help
fi
```

closed off your "if" main statement

Basically, the correct order is:

```
if [ ]; then

elif [ ]; then     (there can be several of these)

else

fi
```

---

### Post by Mr. C. on 2007-07-20
You have a lot of common code in your if/then/else clauses.  See if you can parameterize the code and place the common code in a function.  Eg:

```
function dobackup (...) {
   backuptype=$1
   
   ...
}


dobackup ('semester', ...);
```

MrC

---

### Post by syxbit on 2007-07-20
does anyone know what the "1>>log.txt 2>>log.txt" does?
i know what ">" and ">>" mean, but not with the 1 and 2 in front.
they're paramaters I have to enter when running the script (with getopts)

---

### Post by Mr. C. on 2007-07-20
These are redirections of STDIN and STDERR, respectively, in append mode as you are already aware.  See **Redirecting Output** in man bash.

MrC

---

