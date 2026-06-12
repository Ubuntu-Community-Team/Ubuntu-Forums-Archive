---
title: "Bash Script using long file names"
date: 2014-02-18
forum: Programming Talk
---

### Post by 0-james on 2014-02-18
Hello, I am writing a bash script to backup some of my home directory and some other directories on my Desktop, however I cant seem to get it find my directories in the Desktop Folder which in my case is "Phone Sync" this is what I have so far and maybe you can see what I've done wrong

```
#!/bin/shclear
echo "#####################################"
echo "#           Backup Script           #"
echo "#####################################"
echo
echo


# What to backup
backup_files="/home/james/Documents /home/james/Desktop/Home\ Sync/ /home/james/Desktop/Phone\ Sync/"


# Where to backup to


dest="/media/Media-Backup/tempbak"


day=$(date +%A)
hostname=$(hostname -s)
archive_file="$hostname-$day.tgz"


# Print status message
echo "Backing up! $backup_files to $dest/$archive_file"
date
echo


tar -czf $dest/$archive_file $backup_files --verbose




ls -lh $dest



```

and this is the output  and the error messages

> ######################################           Backup Script              #
#####################################




Backing up! /home/james/Documents /home/james/Desktop/Home\ Sync/ /home/james/Desktop/Phone\ Sync/ to /media/Media-Backup/tempbak/Obi-Tuesday.tgz
Tue Feb 18 11:22:41 GMT 2014


tar: Removing leading `/' from member names
/home/james/Documents/
/home/james/Documents/IMac Repayments.ods
/home/james/Documents/Collection.tc
/home/james/Documents/Ubuntu Terminal commands.odt
/home/james/Documents/Collection.tc~
/home/james/Documents/2014_02_12_1542_backup.syb
/home/james/Documents/ZHackers_USC_Edition.pdf
tar: /home/james/Desktop/Home\\: Cannot stat: No such file or directory
tar: Sync: Cannot stat: No such file or directory
tar: /home/james/Desktop/Phone\\: Cannot stat: No such file or directory
tar: Sync: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
total 86M
-rw-rw-r-- 1 james james 86M Feb 18 11:22 Obi-Tuesday.tgz
james@Obi:~$ 


Can anyone tell me why it wont read the directories with the long names


Thanks

James

---

### Post by erind on 2014-02-18
> **0-james said:**
> [...]

Can anyone tell me why it wont read the directories with the long names

Thanks

James

These errors have nothing to do with long dir names, the problem lies with the spaces in the directory names and how the shell treats them. The proper solution is using shell arrays that will protect the whitespaces in the array's individual tokens. In older shells where arrays aren't available, ***eval*** can be used, but that's the last option really.

```
#!/bin/bash
# set -x

clear
echo "#####################################"
echo "#           Backup Script           #"
echo "#####################################"
echo
echo

# What to backup

**backup_files=(/home/james/Documents "/home/james/Desktop/Home Sync/" "/home/james/Desktop/Phone Sync/")**
# or
# backup_files=(/home/james/Documents /home/james/Desktop/Home\ Sync/ /home/james/Desktop/Phone\ Sync/)
# or 
# backup_files=(/home/james/Documents /home/james/Desktop/*Sync/)

# Where to backup to

dest="/media/Media-Backup/tempbak"

day=$(date +%A)
hostname=$(hostname -s)
archive_file="$hostname-$day.tgz"
# or simply:   archive_file="$(hostname -s)-$(date +%A).tgz"

# Print status message
echo "Backing up! $backup_files to $dest/$archive_file"
date
echo
[B]
tar -czf "$dest"/"$archive_file" "${backup_files[@]}" --verbose[/B]

ls -lh "$dest"

```
It's recommended to use a modern shell (say **/bin/bash**) instead of **/bin/sh** that is in your script, and always quote your variables:** "$var"**

---

### Post by Lars Noodén on 2014-02-18
As mentioned, wrapping your variables in quotes when you use them will help deal with spaces and other problem characters.  Here is a bit of discussion on the topic:

[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by 0-james on 2014-02-19
Hi Erind that worked a treat, you are a star! :-) I will remember in the future to quote the Variables thanks

---

### Post by 0-james on 2014-02-19
Actually I do have one more question, How do I get the script to do incremental backups only backup files that are new or changed

I am a total noob with Bash Scripting so sorry for my ignorance

---

### Post by ofnuts on 2014-02-19
tar has a "-u/--update" option which is described as: "only append files newer than copy in archive".

But if you want to do a new archive, use "find -cnewer $last_archive_file" to build a list of files **changed** (*) since the archive was done.

(*) and not **modified** which isn't enough (a renamed/moved file will be seen changed but not modified)

---

