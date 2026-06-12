---
title: "Ubuntu backup equivalent to this XP application."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by kuproverto on 2008-11-11
On my XP box I used [this]("http://rdcomp.net/ezbackitup/") application which did exactly what I wanted.

I've looked at various Linux backup applications but can't find one that would be the equivalent of this one. I'm looking for a solution that has all of the following features. Does one exist?

Does not compress data.
Copies data from one internal HD to another preserving directory/file structure and permissions.
Automatically deletes directories/files from the destination that are not in the source.
Has a scheduler and a Back-Up Now option
Writes back up details to a log file.
Has a GUI (optional but preferred)

I thought rsnapshot might be the closest but (being a linux newbie) I have no idea how to make it work.

Currently, I'm using Simple Backup Config/Restore but that compresses data so I don't like it. I'm also running Time Vault which seems to just reference the directory/file location rather than actually making a copy. I tried Flyback but it didn't work at all, for some reason.

---

### Post by torgrot on 2008-11-11
Did you try rsync?

torgrot

---

### Post by DGortze380 on 2008-11-11
> **kuproverto said:**
> On my XP box I used [this]("http://rdcomp.net/ezbackitup/") application which did exactly what I wanted.

I've looked at various Linux backup applications but can't find one that would be the equivalent of this one. I'm looking for a solution that has all of the following features. Does one exist?

Does not compress data.
Copies data from one internal HD to another preserving directory/file structure and permissions.
Automatically deletes directories/files from the destination that are not in the source.
Has a scheduler and a Back-Up Now option
Writes back up details to a log file.
Has a GUI (optional but preferred)

I thought rsnapshot might be the closest but (being a linux newbie) I have no idea how to make it work.

Currently, I'm using Simple Backup Config/Restore but that compresses data so I don't like it. I'm also running Time Vault which seems to just reference the directory/file location rather than actually making a copy. I tried Flyback but it didn't work at all, for some reason.

You can do all of this with an rsync script. (but no GUI)

---

### Post by mapes12 on 2008-11-11
Grysync does the same but with GUI.

In backing up a Linux OS there are 2 primary things you may need to consider:

1. System files i.e. your OS
2. Your data files i.e personal settings, files, bookmarks and the like

For both sets of data it is best practice to keep them on separate partitions.

Partimage will create exact images of you partitions and is a popular choice. If you can cut and paste command line instructions then this is an excellent and quick way of protecting you OS system files: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

There are many backup options in Linux and I'm sure you will have many posts to alternatives. 

As with most things Linux, try a few out then stick with one that you're comfortable with. 

BTW take a look at the link in my sig file for more info on this and other Linux best practices.

---

### Post by waffen on 2008-11-11
> **kuproverto said:**
> On my XP box I used [this]("http://rdcomp.net/ezbackitup/") application which did exactly what I wanted.

I've looked at various Linux backup applications but can't find one that would be the equivalent of this one. I'm looking for a solution that has all of the following features. Does one exist?

Does not compress data.
Copies data from one internal HD to another preserving directory/file structure and permissions.
Automatically deletes directories/files from the destination that are not in the source.
Has a scheduler and a Back-Up Now option
Writes back up details to a log file.
Has a GUI (optional but preferred)

I thought rsnapshot might be the closest but (being a linux newbie) I have no idea how to make it work.

Currently, I'm using Simple Backup Config/Restore but that compresses data so I don't like it. I'm also running Time Vault which seems to just reference the directory/file location rather than actually making a copy. I tried Flyback but it didn't work at all, for some reason.


Are you try SBackup? You found it in repos.

---

### Post by ugm6hr on 2008-11-11
Most people advise cron & rsync scripts for this kind of thing.  That would achieve everything you are after (except GUI).

I use grsync, which is a GUI frontend for rsync.  It does exactly what you want, except for the scheduled backup option.

---

### Post by waffen on 2008-11-11
> **ugm6hr said:**
> Most people advise cron & rsync scripts for this kind of thing.  That would achieve everything you are after (except GUI).

I use grsync, which is a GUI frontend for rsync.  It does exactly what you want, except for the scheduled backup option.

Yes, is for that reason I prefer SBackup...:)

---

### Post by kuproverto on 2008-11-12
Thanks for the replies.

Grsync seems to be the best option but I can't find a way to backup more than one directory per execution. Is there a way to add a few directories to a list and have them all backed up at the same time? Is that what Sessions are for?

Also, I get a lot of permissions errors and certain files are not copied even after having set the backup directory and file permissions to read and write for owner, group and others. Would it work better if I ran the backups as root? If so, how do I do that?

I only get errors when the backup destination directory is located on my second internal HD.

---

### Post by beercz on 2008-11-12
[rsnapshot.org]("http://rsnapshot.org")?

It will do everything you need, automatically if you want, once you have configured it.

I rely on it very heavily for all my personal and company's data.  Never let me down.

---

### Post by kuproverto on 2008-11-12
I looked at rsnapshop but don't know how to configure it.

---

### Post by j.smith on 2008-11-12
Thanks ^.^

---

### Post by Paqman on 2008-11-12
> **kuproverto said:**
> I can't find a way to backup more than one directory per execution.

Sbackup will back up as many directories as you tell it to. You can either do backups on command or schedule them.

---

### Post by kuproverto on 2008-11-12
Is there a way to have Sbackup not compress the data?

---

### Post by Paqman on 2008-11-12
> **kuproverto said:**
> Is there a way to have Sbackup not compress the data?

Er, don't think so. Why wouldn't you want it compressed though?

---

### Post by DGortze380 on 2008-11-12
here's some sudo code for a script that'll likely be easier and more efficient than the GUIs you're currently messing with.

```

#!/bin/bash

echo "Start $DATE" >> someLogFile.log
rsync -az /source/path /dest/path
rsync -az /other/source /other/dest
rsync -az /you/get /the/idea
echo "End $DATE" >> someLogFile.log

# Now add me to root's cron


```

EDIT: Please note this is pseudo code. The script will not run as is.

---

### Post by kuproverto on 2008-11-12
Compression - I just prefer to have my backups uncompressed and since I have two huge HDs, I don't need to compress it.

rsync script - Thanks, I'll give that a try.

I'm also testing [this]("http://www.conduit-project.org/") application which, so far, works very well.

---

### Post by stinger30au on 2008-11-12
> **kuproverto said:**
> On my XP box I used [this]("http://rdcomp.net/ezbackitup/") application which did exactly what I wanted.

i bet it will run in wine 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

for hdd backup stuff i use wine and syncback freeware, works a treat

[http://www.2brightsparks.com/downloads.html](http://www.2brightsparks.com/downloads.html)

---

### Post by kuproverto on 2008-11-12
It runs in Wine but not well so I downloaded the app you use which works great. How can I automate it though as, obviously, the Windows Task Scheduler is unavailable?

I presume I use a cron job but how?

---

### Post by kuproverto on 2008-11-12
After much testing I've decided to use the rsync code provided by DGortze380. I saved the bash script in the etc/cron.daily directory. 

Two questions:

Is there a way I can specify when during the day the script runs?

The "Start $DATE" & "End $DATE" just return the words Start and End but not the date. How can I rectify this and how can I add the time as well?

---

### Post by DGortze380 on 2008-11-13
> **kuproverto said:**
> After much testing I've decided to use the rsync code provided by DGortze380. I saved the bash script in the etc/cron.daily directory. 

Two questions:

Is there a way I can specify when during the day the script runs?

The "Start $DATE" & "End $DATE" just return the words Start and End but not the date. How can I rectify this and how can I add the time as well?

The script wasn't complete. It's just pseudo code (some logic that needs to be completed). Give me 10 minutes and I'll write something more complete. What are the directories you want to back up, and (more important) what is the destination directory?

---

### Post by DGortze380 on 2008-11-13
```

# PROGRAMMER: DANIEL GORTZE
# DATE: 13 NOV 2008 - 00:26

##########
# This script will sync a source and backup every time it is
# run. I suggest adding the script to root's cron. I also suggest
# modifying the script to keep incremental backups rather than
# syncing every time.
##########
# You are free to modify and redistribute this script as you see 
# fit. Any modifications from the original code require that my
# name be removed, and a Modification Date be added under the
# creation date above. All other statements in this file must
# remain complete an intact if the file is redistributed.
##########
# I take no responsibility for the results of running this script.
# It is not maintained in any manner, and no warranty is given or
# implied.
##########

#!/bin/bash

# Check for log
touch /var/log/backup.log

# Print start date and time in log
        echo "Start" >> /var/log/backup.log
        date >> /var/log/backup.log

# Run backups. man rsync for more information and other options.
# WARNING: This script will SYNC the backup and source EVERY TIME it is run.
        # EXAMPLES
        # To Sync Backup Every Time
        # rsync -ax /home /media/backupDrive/folder

        # To Add To Backup Every Time
        # rsync -axq /home /media/backupDrive/folder

        # To Create Incremental Backup Every Time
        # rsync -ax /home /media/backupDrive/$(date +"%b-%d-%y")

        # Add your rsync commands below.

# Print end date and time in log
        echo "End" >> /var/log/backup.log
        date >> /var/log/backup.log

```

Put the above script (after you modify it to suite your needs), in your path. The easiest way is the copy is /usr/bin. Check your permissions! Should be 770 or similar.

To run an immediate backup, just type "sudo nameOfScript" (without quotes).

Add to root's cron for daily backups.

```

sudo crontab -e

```

To run every day at 00:01:00

1 0 * * * /usr/bin/nameOfScript

crontab format is

minute of hour / hour of day / day of month / mon of year / day of week / command
an asterisk basically means 'every'. 

So the above crontab entry runs namOfScript at 00:01 of every day of every month each day of the week.

---

### Post by kuproverto on 2008-11-13
> What are the directories you want to back up, and (more important) what is the destination directory?

Here's a couple of lines from my current rsync code:

```
rsync -av --times --delete /home/user1/Documents /backup/home/user1/
rsync -av --times --delete /home/user2/Documents /backup/home/user2/
```

I want the script to only back up items that have changed on the source and delete anything from the destination that no longer exists on the source. /backup is my second internal HD.

The script works when run from a directory in /home/user1 but I wanted to try your method below.

> The easiest way is the copy is /usr/bin. Check your permissions! Should be 770 or similar.

My script is named backup.sh

I did the following:

sudo chmod 770 /usr/bin

and got Permission Denied

so I tried

sudo chmod 770 /usr/bin/backup.sh

and got the same error.

---

### Post by DGortze380 on 2008-11-13
> **kuproverto said:**
> 
I did the following:

sudo chmod 770 /usr/bin


YIKES! NO, Definitely DON'T do that!
I appologize, my original post was unclear.

Never chmod an entire directory, especially a system directory.

Assuming the script is called backup.sh and is currently in your home directory. Do the following.

```


cd ~

sudo chmod 700 backup.sh

sudo cp backup.sh /usr/bin/backup


```

If all of those complete correctly, you should be able to run your backup script by opening a terminal and typing
```

sudo backup

```



These are fine:
rsync -av --times --delete /home/user1/Documents /backup/home/user1/
rsync -av --times --delete /home/user2/Documents /backup/home/user2/

But I would suggest removing the -v flag; using the flag will increase the time it takes for you backup to run exponentially.

Using the -a flag will achieve the following:
Backup new items on the source to the destination.
Update changed items on the source on the destination.

Using the --delete flag will achieve the following:
Delete any files on the destination that no longer exist on the source

Be aware. If you schedule this script to run daily with those flags, all of the above will occur daily. Thus, your backups provide very little protection from accidentally deleted files. You backup of the accidentally deleted file will also be deleted the next time your back-up script runs.


Is your second internal drive mounted via fstab? If not, you may want to consider adding mount and unmount commands to the script, to ensure the drive is accessible.

---

### Post by kuproverto on 2008-11-13
> YIKES! NO, Definitely DON'T do that!
I appologize, my original post was unclear.

Never chmod an entire directory, especially a system directory.

Yes, bad things happened when I did this. I could no longer access the Home folder. What should I chmod the /usr/bin directory back to? Currently, I can access the Home folder etc but I might have made the permissions too relaxed.

I got the backup.sh file copied to the /usr/bin directory and checked to see if the chmod had worked. The owner is root with Read and Write permissions. Group and Others have no permissions so I guess it worked.

The problem is typing sudo backup in Terminal returns the following error:

```
sudo: backup.sh: command not found
```

I navigated into the /usr/bin/backup directory then ran the sudo backup command but still received the same error:

```
/usr/bin/backup$ sudo backup
sudo: backup: command not found
```

I also tried backup.sh. Didn't work.

Obviously I'm doing something wrong here!


> But I would suggest removing the -v flag; using the flag will increase the time it takes for you backup to run exponentially.

I will. It was useful when testing to see what worked and what didn't.



> Is your second internal drive mounted via fstab? If not, you may want to consider adding mount and unmount commands to the script, to ensure the drive is accessible.

Yes it is.

---

### Post by DGortze380 on 2008-11-13
back tonight with a solution (hopefully). class right now.

---

### Post by DGortze380 on 2008-11-13
> **DGortze380 said:**
> back tonight with a solution (hopefully). class right now.

can you post the output of the following commands?
I'm trying to get an idea of what your permissions currently are, and if any of them have been changed.

ls -al /usr

ls -al /usr/bin | grep backup

ls -al /


does the following command work?

sudo touch /test

if it does, let me know and then run the next command.
if it doesn't, don't run the next command.

sudo rm /test




note to self on default permissions:
drwxr-xr-x root root /usr
drwxr-xr-x root root /usr/bin
drwxr-xr-x root root /usr/bin/backup

---

### Post by mdpalow on 2008-11-13
QuickStart might be what you're looking for. See my signature below.

mdpalow

---

### Post by kuproverto on 2008-11-13
> can you post the output of the following commands?
I'm trying to get an idea of what your permissions currently are, and if any of them have been changed.

> ls -al /usr

```
drwxr-xr-x  14 root root  4096 2008-11-11 10:36 .
drwxr-xr-x  22 root root  4096 2008-10-15 10:20 ..
drwxr-xr-x   3 root root 36864 2008-11-13 15:53 bin
drwxr-xr-x   3 root root  4096 2008-10-09 02:33 etc
drwxr-xr-x   2 root root  4096 2008-07-31 13:42 games
drwxr-xr-x  50 root root  4096 2008-11-11 10:36 include
drwxr-xr-x 200 root root 69632 2008-11-12 15:49 lib
drwxr-xr-x   3 root root  4096 2008-05-30 21:37 lib32
drwxr-xr-x   2 root root  4096 2008-11-11 10:36 lib64
drwxr-xr-x  10 root root  4096 2008-04-22 12:48 local
drwxr-xr-x   2 root root 12288 2008-11-12 15:49 sbin
drwxr-xr-x 341 root root 12288 2008-11-12 15:49 share
drwxrwsr-x  13 root src   4096 2008-10-16 15:47 src
drwxr-xr-x   2 root root  4096 2008-04-22 12:51 X11R6
```


> ls -al /usr/bin | grep backup

```
drwxr-xr-x  2 root   root        4096 2008-11-13 18:06 backup
-rw-rw-r--  1 root   root           0 2008-11-13 08:32 backup.sh~
```


> ls -al /

```
drwxr-xr-x  22 root root  4096 2008-10-15 10:20 .
drwxr-xr-x  22 root root  4096 2008-10-15 10:20 ..
drwxrwxrwx   7 root root  4096 2008-11-13 20:42 backup
drwxr-xr-x   2 root root  4096 2008-11-12 08:45 bin
drwxr-xr-x   3 root root  4096 2008-11-09 21:44 boot
lrwxrwxrwx   1 root root    11 2008-05-31 04:02 cdrom -> media/cdrom
drwxr-xr-x  12 root root 14480 2008-11-12 19:08 dev
drwxr-xr-x 144 root root 12288 2008-11-13 20:24 etc
drwxr-xr-x   4 root root  4096 2008-11-13 09:24 home
drwxr-xr-x   2 root root  4096 2008-04-22 12:48 initrd
lrwxrwxrwx   1 root root    33 2008-10-15 10:20 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root root    33 2008-06-19 18:21 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root 12288 2008-11-12 15:49 lib
drwx------   2 root root 16384 2008-05-31 04:02 lost+found
drwxr-xr-x   4 root root  4096 2008-11-12 18:17 media
drwxr-xr-x   2 root root  4096 2008-04-15 00:53 mnt
drwxr-xr-x   4 root root  4096 2008-10-30 13:06 opt
dr-xr-xr-x 166 root root     0 2008-11-12 15:43 proc
drwxr-xr-x  20 root root  4096 2008-11-13 20:42 root
drwxr-xr-x   2 root root  4096 2008-11-12 08:45 sbin
drwxr-xr-x   2 root root  4096 2008-04-22 12:48 srv
drwxr-xr-x  12 root root     0 2008-11-12 15:43 sys
drwxrwxrwt  24 root root  4096 2008-11-13 20:44 tmp
drwxr-xr-x  14 root root  4096 2008-11-11 10:36 usr
drwxr-xr-x  16 root root  4096 2008-06-03 22:07 var
lrwxrwxrwx   1 root root    30 2008-10-15 10:20 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root root    30 2008-06-19 18:21 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic
```

> does the following command work?

sudo touch /test

What's it supposed to do? All that happens is another prompt line appears in the Terminal directly beneath the one I just ran the command on. As I didn't know if it worked or not, I didn't do this:

> sudo rm /test


I've been experimenting a little and have copied the backup.sh script to the usr/local/bin directory then run sudo /usr/local/bin/backup.sh and it works fine. I already have a copy in the /usr/bin/backup directory so I tried again to get the command you wrote, sudo backup, to work. Still get the command not found error. So I tried sudo backup.sh and it works!

I then deleted the backup.sh file from the /usr/bin/backup directory and ran the sudo backup.sh command again. It still works.

My conclusion is the file has to be in the /usr/local/bin directory to run. What is the intended purpose of the /usr/local/bin directory?

---

### Post by kuproverto on 2008-11-13
> QuickStart might be what you're looking for. See my signature below.

Thanks, I'll take a look at that.

---

### Post by DGortze380 on 2008-11-13
> **kuproverto said:**
> ```
drwxr-xr-x  14 root root  4096 2008-11-11 10:36 .
drwxr-xr-x  22 root root  4096 2008-10-15 10:20 ..
drwxr-xr-x   3 root root 36864 2008-11-13 15:53 bin
drwxr-xr-x   3 root root  4096 2008-10-09 02:33 etc
drwxr-xr-x   2 root root  4096 2008-07-31 13:42 games
drwxr-xr-x  50 root root  4096 2008-11-11 10:36 include
drwxr-xr-x 200 root root 69632 2008-11-12 15:49 lib
drwxr-xr-x   3 root root  4096 2008-05-30 21:37 lib32
drwxr-xr-x   2 root root  4096 2008-11-11 10:36 lib64
drwxr-xr-x  10 root root  4096 2008-04-22 12:48 local
drwxr-xr-x   2 root root 12288 2008-11-12 15:49 sbin
drwxr-xr-x 341 root root 12288 2008-11-12 15:49 share
drwxrwsr-x  13 root src   4096 2008-10-16 15:47 src
drwxr-xr-x   2 root root  4096 2008-04-22 12:51 X11R6
```




```
drwxr-xr-x  2 root   root        4096 2008-11-13 18:06 backup
-rw-rw-r--  1 root   root           0 2008-11-13 08:32 backup.sh~
```




```
drwxr-xr-x  22 root root  4096 2008-10-15 10:20 .
drwxr-xr-x  22 root root  4096 2008-10-15 10:20 ..
drwxrwxrwx   7 root root  4096 2008-11-13 20:42 backup
drwxr-xr-x   2 root root  4096 2008-11-12 08:45 bin
drwxr-xr-x   3 root root  4096 2008-11-09 21:44 boot
lrwxrwxrwx   1 root root    11 2008-05-31 04:02 cdrom -> media/cdrom
drwxr-xr-x  12 root root 14480 2008-11-12 19:08 dev
drwxr-xr-x 144 root root 12288 2008-11-13 20:24 etc
drwxr-xr-x   4 root root  4096 2008-11-13 09:24 home
drwxr-xr-x   2 root root  4096 2008-04-22 12:48 initrd
lrwxrwxrwx   1 root root    33 2008-10-15 10:20 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root root    33 2008-06-19 18:21 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root 12288 2008-11-12 15:49 lib
drwx------   2 root root 16384 2008-05-31 04:02 lost+found
drwxr-xr-x   4 root root  4096 2008-11-12 18:17 media
drwxr-xr-x   2 root root  4096 2008-04-15 00:53 mnt
drwxr-xr-x   4 root root  4096 2008-10-30 13:06 opt
dr-xr-xr-x 166 root root     0 2008-11-12 15:43 proc
drwxr-xr-x  20 root root  4096 2008-11-13 20:42 root
drwxr-xr-x   2 root root  4096 2008-11-12 08:45 sbin
drwxr-xr-x   2 root root  4096 2008-04-22 12:48 srv
drwxr-xr-x  12 root root     0 2008-11-12 15:43 sys
drwxrwxrwt  24 root root  4096 2008-11-13 20:44 tmp
drwxr-xr-x  14 root root  4096 2008-11-11 10:36 usr
drwxr-xr-x  16 root root  4096 2008-06-03 22:07 var
lrwxrwxrwx   1 root root    30 2008-10-15 10:20 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root root    30 2008-06-19 18:21 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic
```



What's it supposed to do? All that happens is another prompt line appears in the Terminal directly beneath the one I just ran the command on. As I didn't know if it worked or not, I didn't do this:




I've been experimenting a little and have copied the backup.sh script to the usr/local/bin directory then run sudo /usr/local/bin/backup.sh and it works fine. I already have a copy in the /usr/bin/backup directory so I tried again to get the command you wrote, sudo backup, to work. Still get the command not found error. So I tried sudo backup.sh and it works!

I then deleted the backup.sh file from the /usr/bin/backup directory and ran the sudo backup.sh command again. It still works.

My conclusion is the file has to be in the /usr/local/bin directory to run. What is the intended purpose of the /usr/local/bin directory?

ok..
the touch command should have just put an empty text file in / named test.
If that got created, you're fine. just delete it.


sounds like /usr/bin is not in your path. if /usr/local/bin works, then that's fine, you can use it from there too.

If it all works as intended, just go ahead and add the job to roots crontab as I said in a previous post. If it works when you run it at the command line, it will work in crontab.


As for the output I had you post, it all looks normal. Your permissions are fine, don't chmod anything else.

---

### Post by kuproverto on 2008-11-14
touch command worked.

cron worked.

Thank you for all your help!

---

### Post by DGortze380 on 2008-11-14
> **kuproverto said:**
> touch command worked.

cron worked.

Thank you for all your help!

Anytime.

---

