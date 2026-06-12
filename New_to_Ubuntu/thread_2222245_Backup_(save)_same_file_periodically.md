---
title: "Backup (save) same file periodically"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by elang on 2014-05-05
I am saving a stream to my HDD.
I'd like to copy the file periodically into a subfolder **backup** such that the older versions of the the file are not deleted.

Simply put
 1. Assume the original file is **somefolder/data**
 2. The first backup should be **somefolder/backup/data.1**
 3. The second backup should be **somefolder/backup/data.2**
 4. This process should continue in an interval of t minutes/seconds

How do I go about doing this?

---

### Post by pfeiffep on 2014-05-05
@elang, I'm not a superb shell scripter but I think that you can use the date command to add an extension to the file name data.hhmmss
imbed the command into a for or while loop imcremented by whatever time you determine is required.

```
data.`date +"%H%M%S"`
```

possible start with man time

---

### Post by whitesmith on 2014-05-05
There's a Time Machine-ish thingie for Linux called Simple Backup in the repos. It's configurable so as to provide both full and incremental (delta) backups. Unless you have talent and time, this is the way I would go. Custom stuff is unreasonably time consuming to create, even for "simple" projects -- which often turn out not to be.

---

### Post by ajgreeny on 2014-05-05
You could look at rsync for this, and even run it as a cron job at whatever regular interval you set.

See **man rsync** for all details, but here's a copy of the relevant part.
> -b, --backup
              With  this  option,  preexisting  destination files are renamed as each file is transferred or deleted.
              You can control where the  backup  file  goes  and  what  (if  any)  suffix  gets  appended  using  the
              --backup-dir and --suffix options.

              Note  that  if you don&#8217;t specify --backup-dir, (1) the --omit-dir-times option will be implied, and (2)
              if --delete is also in effect (without --delete-excluded), rsync will add a "protect"  filter-rule  for
              the  backup suffix to the end of all your existing excludes (e.g. -f "P *~").  This will prevent previ&#8208;
              ously backed-up files from being deleted.  Note that if you are supplying your own  filter  rules,  you
              may  need  to  manually insert your own exclude/protect rule somewhere higher up in the list so that it
              has a high enough priority to be effective (e.g., if your rules specify a trailing  inclusion/exclusion
              of &#8217;*&#8217;, the auto-added rule would never be reached).

       --backup-dir=DIR
              In  combination with the --backup option, this tells rsync to store all backups in the specified direc&#8208;
              tory on the receiving side.  This can be used for incremental backups.  You can additionally specify  a
              backup  suffix using the --suffix option (otherwise the files backed up in the specified directory will
              keep their original filenames).

              Note that if you specify a relative path, the backup directory will  be  relative  to  the  destination
              directory,  so  you  probably want to specify either an absolute path or a path that starts with "../".
              If an rsync daemon is the receiver, the backup dir cannot go outside the module&#8217;s  path  hierarchy,  so
              take extra care not to delete it or copy into it.

       --suffix=SUFFIX
              This  option  allows  you to override the default backup suffix used with the --backup (-b) option. The
              default suffix is a ~ if no --backup-dir was specified, otherwise it is an empty string.

---

### Post by steeldriver on 2014-05-05
... at its very simplest, you could use cp with the --backup=numbered option

```

$ while : ; do cp -vt ./backup/ --backup=numbered -- file; sleep 5; done
`file' -> `./backup/file'
`file' -> `./backup/file' (backup: `./backup/file.~1~')
`file' -> `./backup/file' (backup: `./backup/file.~2~')
`file' -> `./backup/file' (backup: `./backup/file.~3~')
`file' -> `./backup/file' (backup: `./backup/file.~4~')
`file' -> `./backup/file' (backup: `./backup/file.~5~')
^C

```

The only slight wrinkle is that the newest copy is always called 'file' i.e.
```

$ ls -lt --time-style '+%X' ./backup/
total 24
-rw-rw-r-- 1 user user 24 06:57:05 PM file
-rw-rw-r-- 1 user user 24 06:57:00 PM file.~5~
-rw-rw-r-- 1 user user 24 06:56:55 PM file.~4~
-rw-rw-r-- 1 user user 24 06:56:50 PM file.~3~
-rw-rw-r-- 1 user user 24 06:56:45 PM file.~2~
-rw-rw-r-- 1 user user 24 06:56:40 PM file.~1~

```

---

### Post by vanadium on 2014-05-06
I have a script for incremental backups using rsync that looks like the following. The script makes a snapshot, using hard links to a previous backup for files that were not changed, and copies when the file was changed. Fast and space efficient. Use cron to have such a script automatically executed at regular times.

```

#!/bin/bash

function backupinc {
	if [ -d $1 ] 
	then 
		if [ -d $2 ]
		then
			rsync -av --delete --link-dest="$2" "$1" "$2-new"
			mv "$2" "$2-$date"; mv "$2-new" "$2"
		else 
			echo "Destination $2 not available"
		fi
	else
		echo "Source $1 not available"
	fi
}

date=$(date "+%Y-%m-%dT%H:%M:%S")
backupinc "/home/vanadium/Documents/" "/media/vanadium/Data/bk/Documents"

```

---

