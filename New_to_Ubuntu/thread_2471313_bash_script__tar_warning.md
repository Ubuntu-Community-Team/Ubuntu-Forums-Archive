---
title: "bash script / tar warning"
date: 2022-01-26
forum: New to Ubuntu
---

### Post by nginmu on 2022-01-26
I cobbled together the script from some google searches:

```

#!/bin/sh

# place in /etc/cron.daily & make executable
# terminal test command: run-parts /etc/cron.daily

# This Command will read the time, day and date.
# Careful - FAT32 does not like colons in filenames
TIME=`date +%H%M-%a-%b-%d-%Y`

#------------------------------------------------
# 1. backup firefox profile               
FILENAME=firefoxprofile$TIME.tar.gz
# Source backup folder.
SRCDIR=/home/me/.mozilla/firefox/profile.default
# Destination of backup file.
DESDIR=/media/me/USBBACKUP/000-AUTOBACKUPS
tar -cpzf $DESDIR/$FILENAME $SRCDIR
#------------------------------------------------
# 2. backup thunderbird profile               
FILENAME=thunderbirdprofile$TIME.tar.gz
# Source backup folder.
SRCDIR=/home/me/.thunderbird/profile.default-release
# Destination of backup file.
DESDIR=/media/me/USBBACKUP/000-AUTOBACKUPS
tar -cpzf $DESDIR/$FILENAME $SRCDIR
#------------------------------------------------

exit 0

```

It goes in /etc/cron.daily and backs up my thunderbird and firefox profiles to a USB drive once a day, it seems to work fine.

When I do 

```

run-parts /etc/cron.daily

```

in terminal to test it, terminal reports

```

me@skully:~$ run-parts /etc/cron.daily
tar: Removing leading `/' from member names
tar: Removing leading `/' from member names

```

Should I be concerned, have I got my syntax wrong somewhere?

---

### Post by Holger_Gehrke on 2022-01-26
No, it's just a warning. 'tar' removes leading '/' from file names while putting files in an archive (and the message tells you it's doing so). This makes restoring in a different location easier. If you really want absolute paths in your archive you can force 'tar' to do so with the option '-P' or '--absolute-names'.

Holger

---

### Post by nginmu on 2022-01-26
Thanks. I don't really understand what these leading '/' characters are.. when I open up the archives in LXQt File Archiver, I just see the folders and files I'd normally expect to see.

No, I wouldn't need absolute paths.. good chance I'd (re)install either FF or TB differently, dependant on updates, OS change etc, so an archive I can restore to a different location makes sense

I think I'm just having trouble understanding what it's trying to tell me about what it's stripping. My thought process is, / is a folder separator, not part of the filename, so why does tar have to strip anything?

---

### Post by The Cog on 2022-01-26
It is indeed a file separator. Except that a leading / has a special meaning, 'from the top' or similar. The very top of the filesystem tree, the root folder is just '/'. A file path that starts with '/' means start at the very top of the tree. Without the leading / it is a **relative** path instead, and starts at wherever in the tree you happen to be at the time. So for instance, when you log in, you are normally placed in your home directory. As such from where you are, you can refer to a file in your Pictures directory as Pictures/my-pic.jpg. This is a **relative** path , relative to your current working directory. For a different user in a different home folder, Pictures/my-pic would refer to a different file in *their* Pictures folder. The full, absolute path for your picture would be /home/nginmu/Pictures/my-pic.jpg. The absolute path is unambiguous. 

When restoring from the tar file where the leading / has been removed, the path is just home/nginmu/Pictures/my-pic.jpg, and if you are still in your home directory it will restore to a folder there, called home, inside your home folder. That full path would then be /home/nginmu/home/nginmu/Pictures/my-pic.jpg.

---

### Post by nginmu on 2022-01-26
I get it now, thanks, that's a great explanation :-)

---

