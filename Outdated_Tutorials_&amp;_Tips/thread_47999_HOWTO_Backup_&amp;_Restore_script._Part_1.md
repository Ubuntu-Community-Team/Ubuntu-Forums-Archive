---
title: "HOWTO: Backup &amp; Restore script. Part 1"
date: 2005-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Lunde on 2005-07-10
**[SIZE=4]HOWTO create menu based backup and restore scripts[/SIZE]**

This guide is based on **Heliode**'s 
**Howto: Backup and restore your system**   
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

I suggest you read his guide first, then return here to create the scripts to perform his commands.

**Part 1.** Will explain how to create a shell script to perform the commands Heliode are explaining. 

A following **Part 2** (Not yet published) will consist of a more advanced and secure backup / restore system that will function over several partitions / disks, this will be published as soon as I'm finished testing it.

[B]
[SIZE=3]READ FIRST[/SIZE][/B]

I have successfully tested Heliod's system and have used it to restore my own system after I messed it up trying to fix the errors of the new Nvidia drivers :-) However if you configure this wrong, or your system is set up wrong, please don't blame me. There may  also may be “typos” here.. I have set up my system over several disks and therefor cannot use these scripts myself exactly how I wrote them here. I use the script which is going to be published in Part 2. I have also tested these script on other directories then “**/**” 

First thing to do after you run the backup script the first time is to open the backup.tgz and check that all files and directories are as they should, so then you know you have a backup.

If this did'nt scare you off.. lets start looking at the scripts:



[B][SIZE=3]THE BACKUP SCRIPT[/SIZE]
[/B]
This is how it looks on screen:
```

|-------------------------------------------------------------
|  IT'S RECOMMENDED TO RUN THIS SCRIPT BEFORE GNOME LOGIN
|-------------------- Press CTRL+ALT+F1 at the GDM login
|-------------------------------------------------------------
|  BACKUP YOUR SYSTEM:
1) Backup
2) Exit
#?

```
You simply just type: **sudo backup** and choose with your number keys the wanted action and press **Enter** on the keyboard.

OK, lets start.
Open a terminal window and type:
**$ gedit backup** 

Copy the following code into your empty text file:
```

#!/bin/bash
#
# A very simple backup script created by: 
# Fredrik Lunde
# http://www.wine-bank.com/profile
#
# This script is related to the article:
# Howto: Backup & Restore script. Part 1
# Published at: http://ubuntuforums.org/showthread.php?p=249408
#
# Instructions: 
# Change the values of "STORAGE_MEDIA" and "ROOT_EXCLUDE_DIRS"
# Name this file "restore", make it "executable" and put it in "/bin"
# Invoke by: "sudo backup"
#
# Feel free to modify however you want. If you make something better, 
# please post it at the ubuntuforum.org thread above :-)
#
#------------------------------------------------------------------------------------
#    CHANGE THE VALUES BELOW TO SUIT YOUR CONFIGURATION 
#------------------------------------------------------------------------------------

ROOT="/*"
ROOT_EXCLUDE_DIRS="--exclude=/lost+found --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/backup.tgz"

#------------------------------------------------------------------------------------
#             DO NOT CHANGE ANYTHING BELOW THIS LINE           
#------------------------------------------------------------------------------------
if [ "$USER" != "root" ]; then 
    echo "You are not root user, use: sudo backup"
    exit
fi
clear
echo "|-------------------------------------------------------------" 
echo "|  IT'S RECOMMENDED TO RUN THIS SCRIPT BEFORE GNOME LOGIN  "
echo "|-------------------- Press CTRL+ALT+F1 at the GDM login"
echo "|-------------------------------------------------------------"
echo "|  BACKUP YOUR SYSTEM: "
OPTIONS="Backup Exit"
LIST="1) Backup 2) Exit" 

select opt in $OPTIONS; do
if [ "$opt" = "Exit" ]; then
    clear
    exit

elif [ "$opt" = "Backup" ]; then
    tar cvpfz /backup.tgz $ROOT $ROOT_EXCLUDE_DIRS
    echo "BACKUP COMPLETE"
    exit
else
    clear
    echo "| BAD OPTION! Select 1 or 2"
    echo "|--------------------------------------------------------------"
    echo "|  BACKUP YOUR SYSTEM: "
    echo $LIST
fi
done

``` 

Now lets modify the script (If you have to...). By default, it makes a backup of everything in “**/**” so you probably don't have to change the “**ROOT**” configuration. Also the “**ROOT_EXCLUDE_DIRS**” may be left alone, but double check that it is like you want it to be according to Heliodes guide.

Save the file, exit the text editor and type in the terminal:
[B]$ sudo chmod 775 backup 
$ sudo mv backup /bin/
[/B]
Now all you have todo to start the script is to type:
**$ sudo backup** 
You can now try to open it, but exit with the option “**2**” and press **Enter**. 



**[SIZE=3]THE RESTORE SCRIPT[/SIZE]**

This is how it looks on screen:
```

|-------------------------------------------------------------
|  IT'S RECOMMENDED TO RUN THIS SCRIPT BEFORE GNOME LOGIN
|-------------------- Press CTRL+ALT+F1 at the GDM login
|-------------------------------------------------------------
|  RESTORE YOUR SYSTEM:
1) Restore
2) Exit
#?

```
Again open a terminal window and type:
**$ gedit restore**

Copy the following code into your empty text file:
```

#!/bin/bash
#
# A very simple backup restore script created by: 
# Fredrik Lunde
# http://www.wine-bank.com/profile
#
# This script is related to the article:
# Howto: Backup & Restore script. Part 1
# Published at: http://ubuntuforums.org/showthread.php?p=249408
#
# Instructions: 
# Change the values of "BACKUP_FILE" and "CREATE_DIRS"
# Name this file "restore", make it "executable" and put it in "/bin"
# Invoke by: "sudo restore"
#
# Feel free to modify however you want. If you make something better, 
# please post it at the ubuntuforum.org thread above :-)
#
#---------------------------------------------------------------------------------
# CHANGE THE VALUES BELOW TO SUIT YOUR CONFIGURATION 
#---------------------------------------------------------------------------------

BACKUP_FILE="backup.tgz"
CREATE_DIRS="/proc /sys /mnt /mnt/mounted_drive"

#---------------------------------------------------------------------------------
#           DO NOT CHANGE ANYTHING BELOW THIS LINE              
#---------------------------------------------------------------------------------
if [ "$USER" != "root" ]; then
    echo "You are not root user, use: sudo restore"
    exit
fi
clear
echo "|-------------------------------------------------------------"
echo "|  IT'S RECOMMENDED TO RUN THIS SCRIPT BEFORE GNOME LOGIN  "
echo "|-------------------- Press CTRL+ALT+F1 at the GDM login"
echo "|-------------------------------------------------------------"
echo "|  RESTORE YOUR SYSTEM:"
tput sgr0
OPTIONS="Restore Exit"
LIST="1) Restore 2) Exit"

select opt in $OPTIONS; do
if [ "$opt" = "Exit" ]; then
    clear
    exit
elif [ "$opt" = "Restore" ]; then
    tar xvpfz $BACKUP_FILE -C /
    echo "|  RESTORE COMPLETE "
    if [[ -e "/proc" ]]; then
        echo "$CREATE_DIRS allready exists! "
    else
        mkdir $CREATE_DIRS
        echo "$CREATE_DIRS are created! "
    fi
    exit
else
    clear
    echo "| BAD OPTION! Select 1 or 2"
    echo "|--------------------------------------------------------------"
    echo "|  RESTORE YOUR SYSTEM:"
    echo $LIST
fi
done

```

Also this may need to be modified a bit. Change the value of “**CREATE_DIRS**” to fit your system. All you **/mnt/XXX** have to be put here etc.

Save the file, exit the text editor and type in the terminal:
**$ sudo chmod 775 backup **
[B]$ sudo mv backup /bin/
[/B]
Now all you have todo to start the script is to type:
**$ sudo backup** 
You can now try to open it, but exit with the option “**2**” and press **Enter**. 


[B][SIZE=3]
CREATING YOUR FIRST BACKUP[/SIZE][/B]

Now you are ready to run your first backup. **Remember to log out of gnome first**.
First thing you have to do is to **open the backup.tgz in the Archive Manager** and check that everything is in order and that you have backed up all the files you want.

Note: If you crash your system so bad that you can't start even start console, you have to use a liveCD and use the **chroot** command then wake the script by **sudo /bin/restore**

---

### Post by Heliode on 2005-07-11
Good idea! Your script looks good... I'll give it a try soon!

---

### Post by LinuxWiz83 on 2005-11-22
How come it does not exclude anything that i have excluded? I have it the exact same way you do in your sample accept a few different directories.

---

### Post by Gweilo on 2006-06-13
those --exclude's didn't really work for me, also I didn't manage to make it only exclude those folders in the root directory (subfolders with the same name as an excluded folder where also excluded, although they shouldn't be...)

here's a little script I wrote
```
#! /bin/sh
#
# very simple backup script. don't forget to run as root, 
# since otherwise not all needed files will be backed up
############################################################

######## user settings ######################################

# folders in the root directory to exclude
exclude=("proc" "lost+found" "mnt" "sys" "media" "tmp")
# directory where the backup file should be placed
backupdir="/media/usbdisk/backup/x40 13.06.06"

#############################################################

cd /

# folders/files in root directory to be saved
BACK=""
for i in `ls`
do
	contains=0
	for e in "${exclude[@]}"; do
		if [ "$i" == "$e" ] 
		then 
			contains=1 
		fi
	done

	if [ "$contains" == 0 ] 
	then
		BACK=$BACK" "$i
	fi
done

timestamp=`date +%Y%m%d_%H%M%S`
file="backup"${timestamp}".tar.gz"

# generate tar
tar -cvpzf "$backupdir/$file" --exclude=$file $BACK
```

---

### Post by Rambie on 2007-01-24
I couldn't get either one to work.  So I made a basic one using a mix of Heliode's guide and this guide:   

```

# generate backup filename with timestamp
timestamp=`date +%Y%m%d_%H%M%S`
file="backup"${timestamp}".tar.gz"

# generate backup tarball
tar -cvpzf "/PATH-GOES-HERE/$file" --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/tmp /

```

Change: PATH-GOES-HERE to the path you'd like to save your backups.
Also edit the exclude paths to your needs.

---

### Post by mrgamer on 2008-03-08
ehe... also i've made a little modification to Lunde's script

my version manages a different path other than / and excludes that path from the tar; it also add to exclude list the default apt archives directory, that's usually very big and very useless if you have a fast internet connection!
That's very useful if you want your backup on a samba partition mount, or a big volume mounted somewhere that contains a lot more data than only your Ubuntu install

The script tough misses the functionality to exclude all the mounted devices from the tar, but at the state of things my bash-scripting knownledge is just not enough for it :confused:

```

#!/bin/bash
#
# A very simple backup script created by: 
# Fredrik Lunde
# http://www.wine-bank.com/profile
#
# This script is related to the article:
# Howto: Backup & Restore script. Part 1
# Published at: http://ubuntuforums.org/showthread.php?p=249408
#
# Instructions: 
# Change the values of "STORAGE_MEDIA" and "ROOT_EXCLUDE_DIRS"
# Name this file "restore", make it "executable" and put it in "/bin"
# Invoke by: "sudo backup"
#
# Feel free to modify however you want. If you make something better, 
# please post it at the ubuntuforum.org thread above :-)
#
#------------------------------------------------------------------------------------
#    CHANGE THE VALUES BELOW TO SUIT YOUR CONFIGURATION 
#------------------------------------------------------------------------------------

ROOT="/*"
ROOT_EXCLUDE_DIRS="--exclude=/lost+found --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/backup*.tgz --exclude=/var/cache/apt/archives"
DEST_DIR=""

#------------------------------------------------------------------------------------
#             DO NOT CHANGE ANYTHING BELOW THIS LINE           
#------------------------------------------------------------------------------------
if [ "$USER" != "root" ]; then 
    echo "You are not root user, use: sudo backup"
    exit
fi
:PRINTMSG
clear
echo "|-------------------------------------------------------------" 
echo "|  IT'S RECOMMENDED TO RUN THIS SCRIPT BEFORE GNOME LOGIN  "
echo "|-------------------- Press CTRL+ALT+F1 at the GDM login"
echo "|-------------------------------------------------------------"
echo "|  BACKUP YOUR SYSTEM: "
OPTIONS="Backup Destination Exit"
LIST="1) Backup 2) Specify Destination 3) Exit" 

select opt in $OPTIONS; do
if [ "$opt" = "Exit" ]; then
    clear
    exit

elif [ "$opt" = "Backup" ]; then
    if [ ${#DEST_DIR} -gt 0 ]; then
        ROOT_EXCLUDE_DIRS=${ROOT_EXCLUDE_DIRS///backup*.tgz/$DEST_DIR}
    fi
    tar cvpfz $DEST_DIR/backup.`date +%d%m%y_%k%M`.tgz $ROOT $ROOT_EXCLUDE_DIRS
    echo "| BACKUP COMPLETE!"
    exit
elif [ "$opt" = "Destination" ]; then
    echo "| Actual Destination: $DEST_DIR/backup.`date +%d%m%y_%k%M`.tgz "
    echo "| For change it, just input some ABSOLUTE path "
    echo "| For leave it as it is, just input nothing an push Return"
    read NEW_DEST

    # if the NEW_DEST length is > 0 then we assign it
    if [ ${#NEW_DEST} -gt 0 ]; then
        DEST_DIR="$NEW_DEST"
    fi
    clear

    if [ ! -d $DEST_DIR ]; then
        echo "| WARNING: Specified Destination Dir: $DEST_DIR/ does not exist, yet"
    fi
    echo "|--------------------------------------------------------------"
    echo "|  BACKUP YOUR SYSTEM: "
    echo $LIST
else
    clear
    echo "| BAD OPTION! Select 1 or 2"
    echo "|--------------------------------------------------------------"
    echo "|  BACKUP YOUR SYSTEM: "
    echo $LIST
fi
done

```

---

### Post by Dieseler on 2008-07-30
Bump from a newbie.
Any updates to this Lunde or Heliode?
I need a back up script badly for Hardy Heron 8.04 but I'm scared to try it.

---

### Post by mastergunner on 2008-07-31
subscribe

---

### Post by Dieseler on 2008-08-09
I removed my script because it went through many changes.
Added menu and other functions.
May resubmit later once I get it tested completely in its new form.

---

