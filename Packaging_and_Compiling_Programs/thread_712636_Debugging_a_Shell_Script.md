---
title: "Debugging a Shell Script"
date: 2008-03-01
forum: Packaging and Compiling Programs
---

### Post by nigel_salvador on 2008-03-01
Can anyone provide help debugging the following backup script:

#! /bin/bash
#
OUTPUT=/home/nigelsalvador/Desktop/Backup" "`date +%F`/Videos.tar.gz
#

BUDIR=/home/nigelsalvador/Videos

#

echo "Starting backup of directory $BUDIR to file $OUTPUT at `date`" >> $HOME/backlog2
#
if [ ! -d /home/nigelsalvador/Desktop/Backup" "`date +%F` ]; then
#
mkdir /home/nigelsalvador/Desktop/Backup" "`date +%F`
#
fi
#
tar -cvzf $OUTPUT $BUDIR

#

if [ $? == 0 ]; then

#

echo "The file:" >> $HOME/backlog2

#

echo $OUTPUT >> $HOME/backlog2

#

echo "was created as a backup for:" >> $HOME/backlog2

#

echo $BUDIR "complete `date`" >> $HOME/backlog2

#

else

#

echo "There was a problem creating:" >> $HOME/backlog2

#

echo $OUTPUT >> $HOME/backlog2

#

echo $BUDIR >> $HOME/backlog2

#

fi

This is the error that I'm getting:

nigelsalvador@nigelsalvador-desktop:~/Programs$ ./backupscript.sh
tar: 2008-03-01/Videos.tar.gz: Cannot stat: No such file or directory
tar: Removing leading `/' from member names
tar: /home/nigelsalvador/Videos\r\r: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
./backupscript.sh: line 35: syntax error near unexpected token `fi'
./backupscript.sh: line 35: `fi'

Thanks in advance

---

### Post by kaens on 2008-03-01
Ending slashes needed on OUTPUT and BUDIR perhaps?

Also, what's with the " " in OUTPUT, BUDIR, and the checks? I've never seen that.... (I'm not a BASH guru either....)


Edit - depending on how your directories are setup, maybe 

OUTPUT="home/nigelsalvador/Desktop/Backup-`date +%F`/Videos.tar.gz"

or
OUTPUT="home/nigelsalvador/Desktop/Backup\ `date +%F`/Videos.tar.gz"

Edit2: I'm fairly certain your problem is that unescaped space in the variable. Spaces aren't that great for directory names and need to be preceded by a '\'. I recommend using dashes or underscores instead.

Edit3: An example:

```

$ OUTPUT=/home/nigelsalvador/Desktop/Backup" "`date +%F`/Videos.tar.gz
$ echo $OUTPUT
/home/nigelsalvador/Desktop/Backup 2008-03-01/Videos.tar.gz
$ cd $OUTPUT
bash: cd: /home/nigelsalvador/Desktop/Backup: No such file or directory

```

---

### Post by kaginken on 2008-03-01
Just go here
[HTML]http://bash.cyberciti.biz/backup/wizard-ftp-script.php[/HTML]

It is an auto-generating shell script, prompts for a few tidbits of info and presto magico!

I use it all the time.  You at most will need to install ncftp which I recommend using w/ or w/o this script as it's be defacto bomb of ftp!

Rock on!  :guitar:

---

### Post by kaens on 2008-03-01
You may also want to take a look at [this guide.]("http://tldp.org/LDP/abs/html/") It's extremely good.

---

### Post by stroyan on 2008-03-04
Spaces do happen in file and directory names.
Shell scripts should be written to deal with the whether or not they create them.
You can protect file names with spaces from being broken apart using double quotes.
Change
tar -cvzf $OUTPUT $BUDIR
to
tar -cvzf "$OUTPUT" "$BUDIR"

Any variable that may have spaces in it is a candidate for placing in double quotes.

---

