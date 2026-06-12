---
title: "HOWTO: Automatic, incremental, encrypted and online stored backup"
date: 2007-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by TakeshiKovacs on 2007-08-26
For quite a while now I was looking for a solution, to store a backup of my boot partition (ubuntu server) online, since it took me about half a year to get the system configured the way I wanted it. Loosing it would definitely cause an attempted genocide. But I had two major concerns: 
1: The costs. Why would I have to pay for something, that is already available in different forms. Yeah, services like S3 from amazon are affordable, but, why pay when you don't have to, right?
2: Security. I'm aware of the fact that there is no such thing as total security when you're somehow connected to the interwebs, but I don't wanna trust some firm, where I can't hunt down the sysadmin with a baseball bat, because he got into my backup files. I think you get the point.

So here is what I did.

Create a backup with tar, split it into 94MB files, encrypt them with my gpg key and upload them to rapidshare. Rapidshare will delete the files after 3 month, if you haven't accessed them, which sould be quite enough.

Let's have a look at the full backup script:

```
#!/bin/bash
#create directory for this month full back in /home/saylar/backup/
mkdir /home/saylar/backup/`date '+%Y-%m'`
mkdir /home/saylar/backup/`date '+%Y-%m'`/full_backup/
#create a full backup for this month and split it into 94MB Files
tar cvj --listed-incremental /home/saylar/backup/`date '+%Y-%m'`/fullbackup.snar --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys  --exclude=/home/saylar/backup / | split -d -b 90m - /home/saylar/backup/`date '+%Y-%m'`/full_backup/full_backup.tar.bz2.split
#encrypt the files with gpg
gpg --encrypt-files --batch --no-tty -r dummy@email.address /home/saylar/backup/`date '+%Y-%m'`/full_backup/*split*
#upload the files via rsupload script
for gpg in /home/saylar/backup/`date '+%Y-%m'`/full_backup/*gpg;
        do /home/saylar/backup/rsupload.pl "$gpg";
done
#now move the file with Rapidsharelinks into corresponding directory
mv /home/saylar/backup/rsulres.txt /home/saylar/backup/`date '+%Y-%m'`/full_backup/
#delete gpg files after they were succesfully uploaded
rm -r /home/saylar/backup/`date '+%Y-%m'`/full_backup/*gpg
```

As you can see, it first creates a directory in /home/saylar/backup for this month and a full_backup directory. Then we tar the whole filesystem and pipe that into the split command which will split the files into 94MB files. Then we encrypt the split files with gpg. Note the --batch --tty option. This is neccessary because the script is started by cron, otherwise it won't run. Then we take upload script provided by [rapidshare]("http://rapidshare.com/en/news.html")(Look for the news from 22. Dec. 2006) and upload the gpg files. Since the script does a MD5 check, there is no need to worry about corrupted files. Now we just have to move the file with the download links into the corresponding backup directory and remove the gpg files again. The scripts are running at 6am each day and at 11:30 pm each day we'll move the logfiles of what was done into the corresponding directory. Just to be sure, that the fullbackup is really finished.

So, if you wanna do that, you have to do the following things:
```
mkdir ~/backup
```
```
mkdir ~/backup/log
```

Put the attached files into the backup directory and replace saylar in every script with you username, replace [email]dummy@email.addr[/email]ess with the email address you create the gpg keys for and make them executable with:
```
chmod a+x scriptname
```
Also look into rsupload.pl, there is one entry at the end of the file. Afterwards edit the crontab for root
```
sudo crontab -e
```

and put the following there:
```
0 6 1 * * /home/saylar/backup/backup_full >> /home/saylar/backup/log/backup_full.log 2>&1
0 6 8,15,23,30 * * /home/saylar/backup/backup_incr_weekly >> /home/saylar/backup/log/backup_incr_weekly.log 2>&1
0 6 2,3,4,5,6,7,9,10,11,12,13,14,16,17,18,19,20,21,22,24,25,26,27,28,29,31 * * /home/saylar/backup/backup_incr_daily >> /home/saylar/backup/log/backup_incr_daily.log 2>&1
30 23 * * * /home/saylar/backup/mvlog > /dev/null
```

Again, make sure you change the username and you are set for a secure backup stored online. 

PS: I'm no programmer at all, so I know that some things could be done much nicer, but it works very well for me. If you have any suggestions, let me you know and I'll be happy to change it.

Sources: 
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=35087")
[Rapidshare Upload Script]("http://images.rapidshare.com/software/rsapi.pl")
[GPG Tutorial]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto")

---

### Post by KubuntuKilledMe on 2007-08-27
Don't you exclude /dev from your backup?

And what is the recovery procedure from a total loss?

Thanks!

---

### Post by TakeshiKovacs on 2007-08-27
Well, both things are mentioned also in this [thread]("http://ubuntuforums.org/showthread.php?t=35087"). I couldn't find any evidence that clearly said i had to exclude /dev from the backup. Well, to be honest, right now I just don't have a second hdd or en empty partition to test the restoring procedure mentioned in the thread I posted above. But I really don't see exceptions to that procedure.

The main purpose of this thread was to show a way that the files are stored online and encrypted.

---

### Post by talon314 on 2007-12-11
Awesome scripts/idea! Just set it up.

Might want to exclude /media in the backups, though.

---

