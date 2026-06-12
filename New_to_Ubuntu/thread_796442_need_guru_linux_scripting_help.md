---
title: "need guru linux scripting help"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-05-16
background: i have a partition for home and have (with help) made a script for homebackup and system backup. the homebackup folder and the sysbackup folder are located in /home
my system backup script works fine but the problem ( and i have been getting advise from people who have linux for 20 years and they cant answer)
i dont want to backup the sysbackup when i run the home backup
here is the script i use:
#!/bin/bash

#-- enter your folders here!
backupfolder="/home/homebackup"
sourcefolder="/home"

cd "$backupfolder"
a=`date +%m-%d-%Y--%H-%M`
tar -czvf homebackup-$a.tgz --exclude=/home/homebackup/$a.tgz/home "$sourcefolder"
echo
echo "-------------------finished backup!-------------------"
echo "--hit ENTER to exit --"
read a
exit 0


even if i add the line --exclude=/home/sysbackup/ in the line that starts
tar and and before "$sourcefolder" the homebackup still backs up the folder sysbackup. and ideas i am sure i am missing the obvious/tks cheesemaker

---

### Post by dstew on 2008-05-16
It seems --exclude=/home/sysbackup/* or --exclude=/home/sysbackup might be better.

Also, --exclude can take only one pattern as an argument. If you want to also exclude both the sysbackup folder, and the older backups, you have to use two different exclude patterns. You can use --exclude twice in the command, or you can use the **--exclude-from *FILE*** to use a file of patterns when you have more than one. FILE is the name of the file that contains the patterns.

---

### Post by rburkartjo on 2008-05-18
tks dstew for the advise but it still backups the system backup folder/cheesemaker

---

### Post by dstew on 2008-05-18
What is /cheesemaker?

---

### Post by rburkartjo on 2008-05-21
dstew,
    just wanted to thank you for your help i already tried what you suggested and didnt work there must be a way to do this but i am lost and cant fiqure it out/cheesemaker

---

### Post by sdennie on 2008-05-21
Though it's fun to write backup scripts, I would actually try using sbackup instead:

```

sudo apt-get install sbackup

```

You'll then find the application in System->Administration->Simple Backup.  It will probably do exactly what you want but without the hassle of having to debug a shell script.

---

