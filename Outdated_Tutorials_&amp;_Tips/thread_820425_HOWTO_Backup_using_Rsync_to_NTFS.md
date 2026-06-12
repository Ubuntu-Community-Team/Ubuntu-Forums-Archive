---
title: "HOWTO: Backup using Rsync to NTFS"
date: 2008-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by abhiroopb on 2008-06-06
[SIZE="4"]**[COLOR="Red"]Problem[/COLOR]**[/SIZE]: You have all your data in ubuntu in ext3 file format. Using standard rsync tools do not work effectively because permissions of files/folders cannot be carried over to ntfs systems. Also ntfs systems have various "glitches" that cause backing up an ext3 system a problem. I have managed to find the ideal solution to backup:
a) COMPLETE hard drive to NTFS
b) COMPLETE hard drive (minus massive music folder) to EXT3
c) Essential documents to NTFS (pendrive)

For this tutorial I will show you the essential elements of backing up for a)

Rsync basically can check the destination data and see if any changes have been made in the source data so that ONLY the source data that has been changed is updated. VERY useful.

[B][COLOR="Red"][SIZE="4"]
BackUp all folders to external NTFS Hard Drive.[/SIZE][/COLOR][/B]

For the purposes of this tutorial I assume the following:
1. User name: bob (so home folder is /home/bob/)
2. External hard drive is mounted at: /media/harddrive/

So, first of all its always a good idea to create a folder inside of your external hard drive before backing up:
```

mkdir /media/harddrive/backup

```

So, now we are going to be making the backup bash script. I prefer making a script as the command is quite long. First we need to make a folder to store the script in (so it is easier to access).
```

mkdir bash

```

Then we must create the bash script:
```

cd bash
gedit backupBIG.sh

```
I call it backupBIG.sh so as to differentiate it from another backup for c)

In this text file put the following in:
```

#!/bin/bash

sudo rsync -rltDvu --modify-window=1 --progress --delete --delete-excluded --exclude-from=/home/bob/Bash/BackupBigExclude.txt / /media/harddrive/backup

```
Explanation of commands:
**rsync:**this is the program used to sync the data. Rsync basically can check the destination data and see if any changes have been made in the source data so that ONLY the source data that has been changed is updated. VERY useful.

**-r**: copies directories recursively
**-l**: copies symlinks as symlinks
**-t**: preserves modification times
**-D**: preserves device and special files
**-v**: shows output (verbose)
**-u**: skips files that are newer at the destination
[B]
--modify-window=1[/B]: this is ESSENTIAL. Basically in windows filesystems time is kept in even numbers (or some such problem). This command tells rsync to ignore filechanges that are only 1 second in difference from the original. It is almost impossible that you will create a file, sync it, and in ONE second make a change and want to sync it again. So it is safe to use this option and it means that rsync will not back up everything every time simply because of a one second change.
[B]
--progress[/B]: simply shows the progress
[B]
--delete[/B]: this is important. Basically rsync syncs files that have been changed. But what if you delete a file from the source directory? This command deletes it from your backed up hard drive as well.
[B]
--delete-excluded[/B]: this deletes folder/files that you have specifically excluded.

**--exclude-from=/home/bob/Bash/BackupBigExclude.txt**: this is the other crucial command. This basically tells rsync to exclude the files/folders found in the list BackupBigExlude.txt. To create this list do the following:
```

gedit /home/bob/Bash/BackupBigExclude.txt

```
Now in the text editor it is ENTIRELY upto you what you want to exlcude.

This is my list:
```

/home/bob/MyDownloads
/home/bob/.VirtualBox
/lost+found
/media
/mnt
/proc
/sys
/tmp

```
Since I am backing up from my root directory, I am not backing up the transient or temporary folders (/media, /mnt, /proc, /tmp, /sys, /lost+found). I am not backing up my /MyDownloads directory as I download a lot of files/data some of which I do not want to backup. and I am not backing up my .VirtualbBox directory as its a massive 2gb file that will update every time I log into VB, a waste of time/resources.

Here are some other hints/tips for the exclude command file:
1. To exclude hidden directories (all the directories that start with .) do: /home/bob/.*/
2.  To exclude hidden files (all the files that start with .) do: /home/bob/.*
3. If you are only backing up from your home directory (that is, /home/bob/) and NOT as we are backing up here from the root directory (that is, /), the exclude command files must start from the /home/bob/. So for example to exclude the MyDownloads folder you would simply put this in the exclude file: MyDownloads. (WITHOUT the complete link /home/bob/MyDownloads). This is complicated but if you need further assistance please comment. 

I am no expert with the exclude command but these settings worked to exclude those files for me.
[B]
locations:[/B] finally the / and /media/harddrive/backup tells the script where to backup from (/) and where to backup to.

There are numerous other settings/commands you can use, including compression, etc. My method is simply to have a place where I can access all my data with minimal hassle (I find uncompressing a hassle, especially if I have enough space for full data backup).

Suffice to say these commands are quite technical, but they all work for me. Notice nowhere here do I tell it to preserve permissions as these will not work if you are copying to an ntfs system.
For more information on rsync commands see [http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html).

Save the files.

Now open a terminal and type the following:
```

cd /home/bob/Bash
sh BackupBig.sh

```

This should run the backup, it may take a long time depending on how much data you have.

[B][COLOR="Red"]NB: Make sure you take care when changing any settings. If you are unsure please ask. In fact don't even change the location without first confirming. 
[/COLOR][/B]
For example, You want to backup /home/bob/ to backup /media/harddrive/ and you have lets say data x.txt, y.txt, z.txt on /media/harddrive/. If you do not create a separate folder all data on /media/harddrive will be erased. SO BE CAREFUL!

---

### Post by Sef on 2008-06-06
Moved to Tutorials and Tips.

---

### Post by abhiroopb on 2008-06-06
Thanks, I'm just always in the Absolute Beginner forum and I keep posting there!

---

### Post by sanus|art on 2008-06-06
Just a suggestion:
add 'p' to the flags to preserve permissions.

---

### Post by abhiroopb on 2008-06-06
> **sanus|art said:**
> Just a suggestion:
add 'p' to the flags to preserve permissions.

Thanks for the suggestion, but like I have already mentioned, this is SPECIFICALLY for backing upto NTFS, which will NOT support permissions. When I backup to my EXT3 I simply use -a (which includes most of the useful flags).

---

### Post by sanus|art on 2008-06-06
> **abhiroopb said:**
> Thanks for the suggestion, but like I have already mentioned, this is SPECIFICALLY for backing upto NTFS, which will NOT support permissions. When I backup to my EXT3 I simply use -a (which includes most of the useful flags).
I am not sure, but I am using it with '-a and -z' for archive and compress mode to NTFS (mounted trough smbmount) and I think permissions are preserved as I recovered '/etc/apache2' at Sunday. Here are my comand:
```
sudo rsync --force --log-file=/var/log/rsync-system.log --progress --delete --exclude=/lost+found/ --exclude=/media/ --exclude=/cdrom/ --exclude=/mnt/ --exclude=/proc/ --exclude=/root/.thumbnails/ --exclude=/root/.Trash/ --exclude=/sys/ --exclude=/home/ --exclude=/tmp/ --delete-excluded -avzlp / /media/XP/BACK_SYSTEM
```

---

### Post by abhiroopb on 2008-06-06
> **sanus|art said:**
> I am not sure, but I am using it with '-a and -z' for archive and compress mode to NTFS (mounted trough smbmount) and I think permissions are preserved as I recovered '/etc/apache2' at Sunday. Here are my comand:
```
sudo rsync --force --log-file=/var/log/rsync-system.log --progress --delete --exclude=/lost+found/ --exclude=/media/ --exclude=/cdrom/ --exclude=/mnt/ --exclude=/proc/ --exclude=/root/.thumbnails/ --exclude=/root/.Trash/ --exclude=/sys/ --exclude=/home/ --exclude=/tmp/ --delete-excluded -avzlp / /media/XP/BACK_SYSTEM
```

Ah I see. The thing is if you compress it permissions can be preserved, but then you are stuck with (in my case) a massive 30-50gb file. I'd rather have all the files, as I have an EXT3 backup which preserves all the permissions anyway. Again to reiterate, if you backup with the -a or -p flags (or any other permission related flags) on an NTFS drive you'll be getting errors after while backing up. And permissions will not be preserved.

---

### Post by sanus|art on 2008-06-06
> **abhiroopb said:**
>  ... then you are stuck with (in my case) a massive 30-50gb file  ...
Why is that? The compression is zlib!

---

### Post by abhiroopb on 2008-06-06
Well I backup my 40gb music collection which does not compress at all (mp3 is already a compressed format).

---

### Post by sanus|art on 2008-06-06
I'm not sure what you mean, but my real '/home' is 1..6GB of size, while rsynced '/home' on the backup is 756MB. zlib is 'per-file' compression - so you can't see it visually like tar or zip (at least for my knowledge).

---

### Post by abhiroopb on 2008-06-06
I'm unsure about this but I just tested it out (on the folder /var/log). I added the -z tag and the -a tag, so as to preserve file permissions (right?) and I looked at the permissions and it was drwxrwxrwx which is the same as the permissions I get using my guide. So I can't see any change. Further if I look at my EXT3 backup I see drwxr-xr-x. So, I'm unsure what exactly is happening!

As far as I have read and know, NTFS cannot preserve permissions. But I am no expert!

---

### Post by sanus|art on 2008-06-06
I was checking by the permissions of scripts (user, group, executable etc.) and they was preserved while I copied them from backup to my desktop.

P.S.
I am not expert ether, was posted here to increase stability of peoples backup, so if my comments was somewhat misleading - I am apologize.

---

### Post by abhiroopb on 2008-06-06
And you used ntfs? Thats interesting maybe the problems have been addressed. Hopefully someone who has more experience can comment.

---

### Post by sanus|art on 2008-06-06
> **abhiroopb said:**
> And you used ntfs? Thats interesting maybe the problems have been addressed. Hopefully someone who has more experience can comment.
Yes, I am not using XP for about 6 months - so XP is for backups only and it is NTFS.

---

### Post by mashedbear on 2009-02-27
Thank you for this Howto. I have followed the instructions changing the paths for my system. The source files are copied to the destination ok but files deleted from the source are not deleted from the destination NTFS drive. 

In the terminal (can I send this output to a log file?) I can see an error message saying IO error detected - skippping file deletion. 

Any ideas how I can solve this?

ps. I also get this error at the end of the rsync process rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]

---

### Post by sanus|art on 2009-03-01
pass ```
--log-file=/path/to/log/file/name-of-log-file.log
``` to it.
e.g.
```
rsync --force --log-file=/var/log/rsync-www.log --progress --ignore-errors --delete --delete-excluded -avzlpE /home/user/www /media/backup/www

```

and than see what's wrong.

---

### Post by mashedbear on 2009-03-07
> **sanus|art said:**
> pass ```
--log-file=/path/to/log/file/name-of-log-file.log
``` to it.
e.g.
```
rsync --force --log-file=/var/log/rsync-www.log --progress --ignore-errors --delete --delete-excluded -avzlpE /home/user/www /media/backup/www

```

and than see what's wrong.

Thanks. I used the log file option as you said. This works great. Still not sure what was causing the problem but have now used the --ignore-errors argument and this  seems to be doing the job. So my script is now:

```
#!/bin/bash

sudo rsync -rltDvu --log-file=/var/log/rsync-backupBIG.log --ignore-errors --modify-window=1 --progress --delete --delete-excluded --exclude-from=/home/paul/bash/BackupBigExclude.txt / /media/EXTHD/gandalf_backup
```

Thanks for your help

---

### Post by gluxoid on 2009-03-15
Thanks for your tutorial. Especially the --modify-window=1 option has been useful to me.

---

### Post by krivine on 2009-09-27
Thank you; the --modify-window=1 flag was just what I needed.

---

### Post by Moyamo on 2010-09-03
can windows computers read the compressed files?

---

### Post by kitus_san on 2010-12-08
> **abhiroopb said:**
> 

Suffice to say these commands are quite technical, but they all work for me. Notice nowhere here do I tell it to preserve permissions as these will not work if you are copying to an ntfs system.
For more information on rsync commands see [http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html).



Hello, I just came across this tutorial in a desperate search for a solution or a confirmation of something I'm starting to be afraid of regarding NTFS rsync from EXTx. If the author is still monitoring this thread I would be very grateful for a response.

FWIF, this response links to the thread to be found here [http://forum.qnap.com/viewtopic.php?f=15&t=37728&p=165098#p165098](http://forum.qnap.com/viewtopic.php?f=15&t=37728&p=165098#p165098)

I can't seem to get rsync to set the creation time of the synced files correctly. It sets the current time instead, pretty much like the command "copy" would do.

Can this be done at all? thanks a lot in advance,

---

### Post by Moyamo on 2010-12-08
have you tried adding the -t option to the rsync command
e.g.
```
yaseen@yaseens-desktop:~$ rsync -t ~/Pictures /media/Flashdrive/Pictures
```

---

### Post by kitus_san on 2010-12-09
> **Moyamo said:**
> have you tried adding the -t option to the rsync command
e.g.
```
yaseen@yaseens-desktop:~$ rsync -t ~/Pictures /media/Flashdrive/Pictures
```

Hi there,

thanks for your response.

The command I use is 

rsync -rlptgoD -vh --delete -i --backup --modify-window=1 /share/photos /mnt/MC4G/Backups/photos/

Please, if you can, have a look at the link provided in my previous post. There you can find some outputs that reflect to a large extent what my problem is.

Thanks a lot

---

### Post by Moyamo on 2010-12-09
That is very unusual. I never have that problem. I not sure if this will help but try replace the -rlptgoD with -a it might make a difference and add -u it will cause rysnc to not replace existing files of a later date than the one on the source.  If that doesn't word then there is probably something wrong with the Backup drive

---

### Post by kitus_san on 2010-12-10
> **Moyamo said:**
> That is very unusual. I never have that problem. I not sure if this will help but try replace the -rlptgoD with -a it might make a difference and add -u it will cause rysnc to not replace existing files of a later date than the one on the source.  If that doesn't word then there is probably something wrong with the Backup drive
Hellow there,

thanks for answering. 

rsync.samba.org states

 -u, --update                skip files that are newer on the receiver
The problem here is that for some reason, the files on the ntfs partition does not keep the original creation time but the recent time of sync. This is annoying because I lose part of the information in case I need to restore information from that partition eventually. This option may be a workaround but I would rather prefer rsync to analize all the data and then to decide what to sync based on the date itself. 

Adding -u seems to avoid resyncing, which is good (I had already incorporated that option from what is stated in the first post). But i just don't want to give in so easy. There must be a way of transfering the creation date from the EXT3 partition on to the NTFS partition.

Thanks a lot,

MArc

---

### Post by Moyamo on 2010-12-11
I have no idea what could be the problem. The times are preserved when I rsync my EXT3 drive to my NTFS drive.  I think the only thing left to try is to run the command as root (sudo).

---

### Post by kitus_san on 2010-12-13
> **Moyamo said:**
> I have no idea what could be the problem. The times are preserved when I rsync my EXT3 drive to my NTFS drive.  I think the only thing left to try is to run the command as root (sudo).

I'm running that command as QNAP admin (ie, root): [http://forum.qnap.com/viewtopic.php?f=15&t=37728&p=165957#p165957](http://forum.qnap.com/viewtopic.php?f=15&t=37728&p=165957#p165957)

Can you confirm that the creation time is kept across rsyncs?? Can you post the command you are running? I don't understand how come the creation time is set to the moment I run the command! this doesn't make any sense

---

### Post by Moyamo on 2010-12-13
```
sudo rsync -azvvvu  --modify-window=1 --delete --exclude-from=/home/yaseen/bin/doNotSync.txt --log-file=/home/yaseen/bin/backupflash.log ~/ /media/Yaseen\'s\ backup\ flash\ drive/Ubuntu\ Backup
```

That's the command I run. I run I few identical commands that are exactly the same except for the source and destination.

---

### Post by kitus_san on 2010-12-27
> **Moyamo said:**
> ```
sudo rsync -azvvvu  --modify-window=1 --delete --exclude-from=/home/yaseen/bin/doNotSync.txt --log-file=/home/yaseen/bin/backupflash.log ~/ /media/Yaseen\'s\ backup\ flash\ drive/Ubuntu\ Backup
```That's the command I run. I run I few identical commands that are exactly the same except for the source and destination.

Hi there, 

just deleted all the files in the destination ntfs partition, run a fresh rsync and again all the files did not preserve the creation timestamp :(

At least I have a backup of all of my data by now, but I sort of hate having to give in :(

---

### Post by pquinnet on 2011-03-20
March 20, 2011 and still asking if you can now do RSYNC to an external drive formatted in NTFS ??   ABHIROOPB had a great
writeup in 2006 and I was wondering if anything changed in 5 years.   thanks in advance .... pq

---

### Post by Moyamo on 2011-03-21
It still works for me.

---

### Post by morean51 on 2011-03-21
thank you all for it i am in need these info about taking backup i think this would help me

---

### Post by kitus_san on 2011-03-21
> **pquinnet said:**
> March 20, 2011 and still asking if you can now do RSYNC to an external drive formatted in NTFS ??   ABHIROOPB had a great
writeup in 2006 and I was wondering if anything changed in 5 years.   thanks in advance .... pq
I gave up on this, I never managed to create a proper backup rsync script for backing up my EXT3 partition to a NTFS one... PM if you want to discuss the details.

---

