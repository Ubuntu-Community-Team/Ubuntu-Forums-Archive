---
title: "Rsync Backup --exclude=/home/*/.*"
date: 2009-07-07
forum: Programming Talk
---

### Post by Penguin Guy on 2009-07-07
It should have been [COLOR="Green"]--exclude=/*/.*[/COLOR] rather than [COLOR="Red"]--exclude=/home/*/.*[/COLOR] The finished backup script can be found below, change [COLOR="Green"]WRITE='/media/backup'[/COLOR] to wherever you want to back it up to [COLOR="Red"](warning: if you back up to somewhere inside /home then it will recur one every time you backup, to avoid this add [COLOR="Green"]- /path/to/backup[/COLOR] to the exclude-list)[/COLOR]. Thanks to [[COLOR="Blue"]unutbu[/COLOR]]("http://ubuntuforums.org/member.php?u=518895") and [[COLOR="Blue"]stroyan[/COLOR]]("http://ubuntuforums.org/member.php?u=416360") for correcting me.


/usr/local/bin/backup-home
```
#!/bin/bash

##### CONSTANTS #####
NAME="${0##*/}"
DESCRIPTION=
VERSION=0.1
LOCATION="$(readlink -f $0)"
LOCATION="${LOCATION%$NAME}"
EXCLUDE="${LOCATION}exclude-list"
WRITE='/media/backup'

##### MAIN CODE #####
guest=$(echo $1 | sed 's_[^#]*@\([^#]*\)_\1_')

if [ "$(whoami)" != 'root' ]; then
	echo >&2 "Error: You must have root privileges to run this program."
	exit 1
fi
while [ ! -d "$WRITE" ]; do
	echo >&2 "Please mount backup device at $WRITE and press [ENTER] to continue.
Press [ESC] to postpone backup."
	if [ "$(wait-keypress )" == '' ]; then  # Escape/Enter
		exit 0
	fi
done
echo "The backup may take some time, please be patient..." 
if [ "$1" == '' ]; then
	rsync --delete -act /home/ $WRITE/$HOSTNAME:\ Home\ Backup/ --exclude-from="$EXCLUDE"
else rsync --delete -act $1:/home/ $WRITE/$guest:\ Home\ Backup/ --exclude-from="$EXCLUDE"
fi

if [ "$?" == 0 ]; then
	echo "Backup completed successfully!"
	exit 0
else 
	echo "Backup did not complete successfully."
	exit 1
fi
```



/usr/local/bin/exclude-list
```
+ /*/.alaises
+ /*/.profile
+ /*/.*rc
+ /*/.devilspie/
- /*/.*
- /lost+found
```

---

### Post by unutbu on 2009-07-07
See if this command lists all the files you want (and none that don't want):
```

cd /home
find . -regex "./[^/]+/[^.].*"
```

If that command succeeds, then something like
```

find . -regex "./[^/]+/[^.].*" |  rsync -ac --files-from - /home/ $WRITE/$HOSTNAME:\ Home\ Backup/ --exclude=lost+found 
```

may do what you want. 

I see in your rsync command that you wish to backup files or directories called '.aliases'. For that perhaps use
```

rsync -ac  --include='.aliases' -f 'hide,! */' /home/ $WRITE/$HOSTNAME:\ Home\ Backup/
```

PS: Hmm... A bit of testing seems to suggest using --files-from may obstruct your ability to use the --delete flag...

---

### Post by Penguin Guy on 2009-07-07
Thanks, it seems to work quite well but is there any way to get exact file paths rather than relative ones from the [COLOR="Green"]find[/COLOR] command?

---

### Post by unutbu on 2009-07-07
Yes:
```
sudo find /home -regex "/home/[^/]+/[^.].*"
```

---

### Post by Penguin Guy on 2009-07-08
Thanks! All now works great apart from, as you said, the --delete parameter not working. It may be possible to fix this by adding a / to the end of all directories but **not** to the end of files. This could be done with a another command but I was wondering if find had a built-in function to do this? I have searched but found nothing on the internet or in the man page.

Thanks for all the help.

---

### Post by unutbu on 2009-07-08
How about this:

```
# Copy everything in home that is not a hidden file or directory, or the lost+found directory:
rsync -ac --delete --exclude=lost+found --exclude='.*' /home/ $WRITE/$HOSTNAME:\ Home\ Backup/ 

# Copy the .aliases files or directories:
rsync -ac  --include='.aliases' -f 'hide,! */' /home/ $WRITE/$HOSTNAME:\ Home\ Backup/

# Copy "2nd-level" hidden files:
find /home -regex "/home/[^/]+/[^.].*/\..*" | rsync -ac --files-from - /home/ $WRITE/$HOSTNAME:\ Home\ Backup/ 

```

The first command includes the --delete flag.

---

### Post by stroyan on 2009-07-08
rsync alone can select the files that you want.
Use "/*/.*" to refer to files and directories that start with . and reside one directory level below the root of the transfer in the /home/ directory.
Patterns that don't start with a "/" will be applied to file names in all directories.  That means that your "--exclude=lost+found" will apply to all files and directories at any level.  You may want to use "/" anchors for those other patterns as well.

 rsync --delete -act /home/ $WRITE/$HOSTNAME:\ Home\ Backup/ --exclude=lost+found --include=.aliases --exclude="/*/.*"

---

### Post by unutbu on 2009-07-08
This is a much better solution. Thanks, stroyan!

---

### Post by Penguin Guy on 2009-07-08
> **stroyan said:**
> rsync alone can select the files that you want.
Use "/*/.*" to refer to files and directories that start with . and reside one directory level below the root of the transfer in the /home/ directory.
Patterns that don't start with a "/" will be applied to file names in all directories.  That means that your "--exclude=lost+found" will apply to all files and directories at any level.  You may want to use "/" anchors for those other patterns as well.

 rsync --delete -act /home/ $WRITE/$HOSTNAME:\ Home\ Backup/ --exclude=lost+found --include=.aliases --exclude="/*/.*"
Thanks - that works perfectly! I see where I messed up! :KS

---

### Post by Penguin Guy on 2009-07-25
One small problem: When I backup using the --delete flag it takes ages, I'm guessing it's including files that haven't changed in the backup for some reason. Anyone know why?

---

