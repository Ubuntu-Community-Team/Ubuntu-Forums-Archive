---
title: "error in bash script"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by xravexheavenx on 2008-09-17
I am working on a script to check every hour for new files, ftp them to another box, and remove any files older than 72 hours.  I had the script working to copy the files to another directory but now it seems it does not feel like working again.  Anyone see what my issue is.  Her is the error I am getting and the code:

date: extra operand `v1.9.7'
Try `date --help' for more information.
time.sh: 17: arithmetic expression: expecting primary: "1221683960-"
`sh /home/ubuntu/.torrents/timetorrents.sh`
date: option requires an argument -- r
Try `date --help' for more information.
/home/ubuntu/.torrents/timetorrents.sh: 17: arithmetic expression: expecting primary: "1221683960-"




```
#!/usr/local/bin/bash
ls -1 /home/ubuntu/.files | while read FILE
do
tnow=`date +%s`
tfile=`date +%s -r /home/ubuntu/.files/$FILE`
agesecs=$(($tnow-$tfile)) #Age of filename in seconds
ageminutes=$(($agesecs/60)) #Age in minutes
expires=4320
movetime=60
if [ $ageminutes -gt $expires ]; then
`rm -r /home/ubuntu/.files/$FILE`
elif [ $ageminutes -lt $movetime ]; then
`lftp ---FTP LOGIN---`
`mirror -R ".files/$FILE"`
`exit`
fi
done
`sh /home/ubuntu/.torrents/timetorrents.sh`

```

The shell code it executes after this one is just the same thing but with a different directory that needs to be done after this one.

---

### Post by jamesrl on 2008-09-17
Can you run it from command line with?
> bash -vx name_of_script.sh
The prefixes given echo each line of the program, then echo (with a prefix +) each command that runs due to each line of the program.  [Hard to debug as I don't know what files are in your directory.]

---

### Post by xravexheavenx on 2008-09-17
Hmm...  Thanks for the tip.  It seems that when I run that you said...  It looks like the fact that there is a "+" in the file name is causing it.  Any workaround for this?

---

### Post by xravexheavenx on 2008-09-17
I just quoted my variable that retrieves the file names and seems to work but then it gets to a certain point and stops checking the files.

---

### Post by jamesrl on 2008-09-17
Since it works when you run bash from the command line, you probably are using different versions of bash or something.

By default bash is located /bin/bash
so the first line in your program should be:
```

#!/bin/bash

```
unless you want to use a different version.  If you type whereis bash from teh command line you can see which one runs when you use it from the command line (or alternatively you could try 
/usr/local/bin/bash -xv your_script.sh

---

### Post by xravexheavenx on 2008-09-17
Thanks.  Seems I had that set wrong.  

Also, it seems that it is not running commands in order.  For example the ftp command.  Which, doesnt work anyways but even if I put a cp command in there for it to copy to another folder for debugging purposes it seems it is running the command in the middle of everything.  How would I set it to run after all commands above it are finished?

---

### Post by jamesrl on 2008-09-17
I believe by default (unless you end lines in &) every line waits until the line above is executed.  
This is not 100% true as it depends on the behavior of the program.  For example usually when you type a command from the (bash) command line without an &, it waits until the program is finished before giving you another prompt.  However, some programs send signals to bash right after the program just starts up signifying that the command is finished executing or going to run in the background (for example exaile) and immediately gives you a prompt again.  In these circumstances pausing the program is the simplest solution if there is a finite time the command takes.  For example try the sleep command, by adding this line to pause the program 10 seconds:
```
sleep 10
```.

Fancier solutions exist to check if the program above is still running like:
```

exaile_running=`ps aux | grep exaile | grep -v grep | wc| awk '{ print $1 }'`

```
which checks running processes (ps aux), searches for lines containing exaile (while skipping lines containing grep so you ignore the grep exaile process), counts the number of lines (wc= word count) and then gets the first variable from wc (line count).  So $exaile_running is a 1 (or greater if multiple copies are running) if exaile is running and not running is a 0.

I got a version of your script to work (and added some debugging output, and also put paths into string variables based on $HOME location as we have different user names): 
```

#!/bin/bash

FILESPATH="$HOME/.files/"
NEWPATH="$HOME"
ls -1 $FILESPATH/ | while read FILE;
do
echo "FILE: $FILE"
tnow=`date +%s`
tfile=`date +%s -r $FILESPATH/$FILE`
agesecs=$(($tnow-$tfile)) #Age of filename in seconds
ageminutes=$(($agesecs/60)) #Age in minutes
expires=20
movetime=10
echo "tnow: $tnow"
echo "tfile: $tfile"
echo "agesecs: $agesecs"
echo "ageminutes: $ageminutes"
if [ $ageminutes -gt $expires ]; then
`rm -r $FILESPATH/$FILE`
elif [ $ageminutes -lt $movetime ]; then
`cp $FILESPATH/$FILE $NEWPATH/$FILE`
fi
done

```
which will remove the files if older than expires time, and copies the files if newer than movetime.

Happy coding.

---

