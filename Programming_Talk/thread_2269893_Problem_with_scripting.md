---
title: "Problem with scripting"
date: 2015-03-18
forum: Programming Talk
---

### Post by VitiDaniele on 2015-03-18
Hi all, i don't know if it's the right section, but i'm new t this forum...
I only wanted to ask why my script works only in my Ubuntu at home (14.10 minimal - MATE - ubuntu-desktop minimal) and not in my dedicated server at OVH (ubuntu 14.04 server)

Here's the script:

```
 #!/bin/bash
 # /etc/init.d/minecraft
 # versione 1.2 | 12-03-2015
 
BACKUPPATH='/root/Desktop/BACKUPS'
BKPATH='/root/Desktop'
NAME='NECROLANDS'
NOW=`date "+%Y-%m-%d_%Hh%M"`
BACKUP_FILE=''$BACKUPPATH'/'$NAME'_'$NOW'.tar'
SERVERS='folder1 folder2 folder3'


echo "Back up $NAME? (Y/n)"
read CHOICE


if [ $CHOICE = "n" ]; then 
	echo "Closing $NAME backup utility..."
	exit
else [ $CHOICE = "Y" ];
	echo "Backing up $NAME..."
	tar -C $BKPATH -cf $BACKUP_FILE $SERVERS
	echo "Compressing backup..."
	gzip -f $BACKUP_FILE
	echo "Backup completed! Exiting..."
	exit
fi

```

At home it works perfectly, no errors.

On my server returns theese things...

```

./backup: line 4: $'\r': command not found
./backup: line 11: $'\r': command not found
? (Y/n) NECROLANDS
': not a valid identifier`CHOICE
./backup: line 14: $'\r': command not found
./backup: line 26: syntax error: unexpected end of file

```


Why? This script is very important to me cause makes a backup of the entire minecraft server...

---

### Post by sisco311 on 2015-03-18
Thread moved to **Programming Talk**.

Check out BashFAQ 052 (link in my signature).

The error message indicates that the script file is in MS-DOS/Windows format. ;)

---

### Post by VitiDaniele on 2015-03-19
But on my ubuntu at home that script runs perfectly, i've not wrote it in windows...

---

### Post by ofnuts on 2015-03-19
It could have been converted to Windows format during the transfer (FTP or else). On the OVH server you can [remove the CRs](http://superuser.com/questions/52044/convert-crlfs-to-line-feeds-on-linux).

---

