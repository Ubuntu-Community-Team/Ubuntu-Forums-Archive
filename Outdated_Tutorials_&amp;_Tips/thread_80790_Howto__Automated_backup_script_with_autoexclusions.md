---
title: "Howto:  Automated backup script with autoexclusions based on filesize"
date: 2005-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by zigford on 2005-10-23
Hey,  I have been looking for a good way to backup my Ubuntu system for ages.  There seem to be no good programs in our repositories or I am blind.

So I decided to write a beauifull little script.  It started out as a simple task and just kept getting bigger and better.  It was based off of various scripts I found on the Google.

Features:

[LIST]
[*]Will scan home directorys and exclude files larger than 10meg (You can change this variable)
[*]Reads ".exclude" files from home directories for manual exclusions.
[*]Reads ".exclude" files from any of the other specified inclusions for exclusion.
[*]Creates archives with date tags
[*]Easily editable variables
[*]Verifies backup integrity
[/LIST]

```
#!/bin/bash
# Backup Script by Jesse Harris
# Create backups of /etc, /home, /usr/local, and...
PATH=/bin:/usr/bin

#######################################################################
# Please edit these variables to match your system                    #
#                                                                     #
# backupdirs - This specifies seperate archives you wish to create    #
#            - You can put a .exclude file into these directories     #
#            - for manual exclusions (Specify the full path)          #
# dir        - This is where you backups will be stored, if it is     #
#            - within your inclusion path, make sure to put it into   #
#            - its relevant .exclude file.                            #
# homes      - This is a temp file created whenever the script is run #
# sizecheck  - This specifies that home directories are to be scanned #
#            - for file sizes, do not change this variable            #
# maxsize    - This specifies that anything exceeding this size within#
#            - anyones home directory will be automatically excluded  #
#-----------------------------Good Luck-------------------------------#
#######################################################################

backupdirs="/etc /root /home /boot /var /bin /initrd /lib /sbin /usr"
dm=`date +%d%b`
dir="/home/harrisj/backup/"
homes="/tmp/homes"
sizecheck="/home"
maxsize="+10M"

# Check if root
if [ "$(whoami)" != "root" ]; then
        echo "Not running as root. Exiting..."
        exit 0
else
        echo "Running as root. Good"
fi

mkdir -p $dir$dm

for path in $backupdirs
        do
        if [ "$path" = "$sizecheck" ]; then
                ls $path > $homes
                for home in $(cat $homes)
                        do
                        if [ "$home" != "$sizecheck" ]; then
                                echo "Checking $home Filesizes..."
                                find $path/$home/ -size $maxsize -type f -print > $path/$home/auto-exclude
                                echo "System backup on $path/$home"
                                tar --exclude-from=$path/$home/auto-exclude --exclude-from=$path/$home/.exclude -czf $dir$dm/$home.tar.gz $path/$home 2>/dev/null
                        fi
                        done
        else
                if [ -e $path/.exclude ]; then
                        echo "Reading exclude file.. for $path"
                        echo "System backup on $path"
                        tar --exclude-from=$path/.exclude -czf $dir$dm/$path.tar.gz $path 2>>/dev/null
                        else
                        echo "System backup on $path"
                        tar czf $dir$dm/$path.tar.gz $path 2>>/dev/null
                fi
        fi
        sleep 2
        done

echo "System backups complete, status: $?"
echo "Now verifying system backups"

for path in $backupdirs
        do
        echo "Verifying $path...."
        if [ "$path" = "/home" ]; then
        for home in $(cat $homes)
                do
                        zcat $dir$dm/$home.tar.gz | tar t 2>/dev/null && \
                if [ $? -eq 0 ]
                        then echo "$path: verified"
                        else echo "$path: error(s) in verify" | wall
                fi
                done
        else
                zcat $dir$dm/$path.tar.gz | tar t 2>/dev/null && \
                if [ $? -eq 0 ]
                        then echo "$path: verified"
                        else echo "$path: error(s) in verify" | wall
                fi
        fi
        done


echo "Please remove backup tape" | wall

```

Example .exclude file from /home/harrisj/.exclude
Always specify the full path in your .exclude files
```
/home/harrisj/backup/*
/home/harrisj/c/*
/home/harrisj/dvdrip/*
/home/harrisj/Qemu/*
/home/harrisj/iso/*
/home/harrisj/Games/*
/home/harrisj/Temp/*
/home/harrisj/Video/*
/home/harrisj/vcr/*
/home/harrisj/.Trash
/home/harrisj/.transgaming/*
~/music
~/roms
~/winetools

```

Also, its handy to have a nautilus script to easily add directories to your home  .exclude file

vi ~/.gnome2/nautilus-scripts/Add\ To\ Backup\ Exclude
```
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi
echo $dir >> ~/.exclude

```
chmod ug+x ~/.gnome2/nautilus-scripts/Add\ To\ Backup\ Exclude

Now just right click on the directory-->Scripts-->Add to backup exclude.

Good bye

Edit: Bugfix
Edit: Script update
Edit: missed a slash in there.
Edit: Changed a line of code that was wrong.

---

### Post by Gandalf on 2005-10-23
WOW that's a nice HOWTO Thanks

Just change
```

vi ~/.gnome2/nautilus-scripts/Add\ To\ Backup Exclude

```

to

```

vi ~/.gnome2/nautilus-scripts/Add\ To\ Backup\ Exclude

```


P.S: nautilus script does not work i always get
```

/

```
as an exclude

---

### Post by zigford on 2005-10-23
[QUOTE=Gandalf]
P.S: nautilus script does not work i always get
/
as an exclude[/QUOTE]

Hmmm, wierd... Can't say I know why that would happen.  Anybody else get the same problem?

---

### Post by BLTicklemonster on 2005-10-25
Missing a dot org? No wait, don't let them know about this! :D 

Thanks for the nice howto.

---

### Post by UbuWu on 2005-10-25
[QUOTE=zigford]Hey,  I have been looking for a good way to backup my Ubuntu system for ages.  There seem to be no good programs in our repositories or I am blind.[/QUOTE]

Not in the repositories, but there was something very similair to your script with a nice gui developed for Ubuntu during the Google summer of code. You can find it here:

[http://sourceforge.net/projects/sbackup](http://sourceforge.net/projects/sbackup)

> 
SBackup is a simple backup solution intended for desktop use. * backup any files and directories * define exclusions by regex * maximum filesize limit * to local & remote dirs The software is created within Google Summer of Code 2005 for Ubuntu 

---

### Post by zigford on 2005-10-25
[QUOTE=UbuWu]Not in the repositories, but there was something very similair to your script with a nice gui developed for Ubuntu during the Google summer of code. You can find it here:

[http://sourceforge.net/projects/sbackup](http://sourceforge.net/projects/sbackup)[/QUOTE]

Thanks UbuWu, maybe I should have posted before writing the script :)

---

### Post by Pallazzio on 2006-12-20
I'm very new to Linux.  Could someone please tell me how to run this script?

---

### Post by un_dave on 2007-09-26
Ingenious! 

This is just what i was looking for. I did have a look at sbackup, but i much prefer this simple script, as i can tell exactly what's happening.

I've just tested it, and it seemed to work perfectly, however seeing as this is a little out of date now, is there anything that should be changed for backing up feisty 7.04?

Thanks zigford!

---

### Post by Jasper84 on 2007-12-14
Great job! I was wondering why the fact that the method of those two other threads copy everything didnt turn up :/. I doubt any ,ogg file will crash your system in a way someone would want to back up that way for :).
I guess all system files are <10MB, to, so great :).
Edit: Perhaps you should add the files in attachments for convenience.

---

### Post by karldiechmann on 2007-12-15
There were some tweaks I wanted to make to Zigford's backup script, to better fit my personal preferences.  Some of my alterations (I won't call them enhancements--that'd be an undeniable misnomer):
[LIST]
[*]Configuration settings are read from a user-specified file.  Script-coded settings are available only as fallback.
[*]Instead of doing a size check on the /home directory, user specifies which folders to do a size check on.
[*]Within the configuration file, user can specify which compression method they wish to use.  Currently: gzip, bzip2, and tar (uncompressed).
[*]The .exclude and auto-exclude files have been moved to .$scriptName.exclude and .$scriptName.auto-exclude.  I did this just in case I did an ls -a and couldn't remember what exclude was for.  Because I titled the script zigford on my machine, those files are called .zigford.exclude and .zigford.auto-exclude.
[/LIST]

I have attached my altered code and the .zigford.conf file I use.  (If a settings file is not specified, the script checks for a .zigford.conf file to use before defaulting to normal.)

---

### Post by marf88 on 2008-01-03
Zigford I had a 600MB iso in my /home/myuser/Desktop  and for some reason it was adding this file to the backup zip file even though it is over the +10MB file size limit. Any Ideas?

---

### Post by RobinetDeTrie on 2008-03-21
Hello Hello !
This is really a nice script. Just one thing : I would like to implement a split argument, because I would like to backup my data to a F32 partition. What are the changes to do to your script ? Thank you.

---

### Post by bluetoothgoose on 2009-02-02
For some reason, this backed-up everything except my home directory.  

Any ideas as to why?

---

