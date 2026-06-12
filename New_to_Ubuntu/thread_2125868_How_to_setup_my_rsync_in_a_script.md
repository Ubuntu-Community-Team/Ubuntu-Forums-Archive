---
title: "How to setup my rsync in a script"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by roberto99 on 2013-03-15
Hi all

I do use rsync on the commandline at the moment. But I would like to execute all my 5 rsync's with one click, and then possibly automatically shutdown the computer. How can I do this?


my commands are doing the following (the last two go to a nfs-share on a NAS)

rsync -r -t -p -o -g -v --progress --delete --exclude=.* --log-file=/home/roberto/i3vmssd.txt --log-file-format= -l -H -s /media/i3vmssd/i3vmmint /media/vmandimages/vmandimages/vm

rsync -r -t -p -o -g -v --progress --delete --exclude=.* --log-file=/home/roberto/homei3host.txt --log-file-format= -l -H -s /media/homei3host/roberto /media/homei3hostbk

sudo rsync -r -t -p -o -g -v --progress --delete --exclude=.* --log-file=/home/roberto/vmandimages.txt --log-file-format= -l -H -s /media/vmandimages/vmandimages /media/vmandimagesbk

rsync -r -t -p -o -g -v --progress --delete --exclude=.* --log-file=/home/roberto/homei3hostdatanas.txt --log-file-format= -l -H -s -b --backup-dir=`date +%Y-%m-%d` /media/homei3host/roberto /media/datanas

rsync -r -t -p -o -g -v --progress --delete --exclude=.* --log-file=/home/roberto/vmandimagesdatanas.txt --log-sudo file-format= -l -H -s -b --backup-dir=`date +%Y-%m-%d` /media/vmandimages/vmandimages /media/datanas

so can I just put all in a file starting "#!/bin/bash" and just ending with the last command?

thanks
Roberto

---

### Post by r-senior on 2013-03-15
That would be a reasonable starting point for a script.

If you want to shut down at the end, something like:

```
sudo poweroff
```

You might also want to define some variables to refer to the directories and common options so that it's easier to maintain, for example:

```

RSYNC_OPTIONS="-r -t -p -o -g -v --progress --delete"
VM_IMAGES="/media/i3vmssd/i3vmmint /media/vmandimages/vmandimages/vm"

rsync $RSYNC_OPTIONS --exclude=.* --log-file=/home/roberto/i3vmssd.txt --log-file-format= -l -H -s "$VM_IMAGES"
...

```

---

### Post by mckenna1977 on 2013-03-15
To make the script executable you may also want to do chmod +x <script_name>

---

### Post by oldfred on 2013-03-15
You will not need nor should have sudo in the file.

A simple example.
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

      
 Some folders to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      
 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

   Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

   rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by roberto99 on 2013-03-18
thanks for all the information!

cheers
Roberto

---

