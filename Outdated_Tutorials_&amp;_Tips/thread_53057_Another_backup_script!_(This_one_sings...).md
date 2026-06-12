---
title: "Another backup script! (This one sings...)"
date: 2005-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Nequeo on 2005-07-30
Hi people...

I recently wrote a very simple backup script designed for use on an Ubuntu based file server. I present it here so that any others in similar circumstances can use it without needing to peruse the countless backup-scripts in the repositories, fretting over which one will do what they want. 

It is designed to be run by a crontab, automatically backuping up certain directories to a specified location on a hard-drive (such as an external USB drive), and notifying you by e-mail of the result. In my case, /home and /data. 

It is NOT designed to backup to removeable media, such as CD-R, DVD-R, tape drives.... It is NOT designed to create a working backup of an entire system (though it could concievably do so).

I am operating under the assumption you know how to schedule a program to run with cron. If so, you can download the script [here](http://members.optusnet.com.au/~sger/backup.py), edit the settings (conviniently located at the start of the file), and crontab away. If you don't know about cron, I'm happy to help you get the script running. But for now , here's the meat:

Here is what it does - 

* Recursively backs up the directories of your choice as .tar.bz2 files, to the destination of your choice. In my case an external hard-drive. 

* Files are automatically named according to the root directory you are backing up. E.g. '/home' will backup as 'home0.tar.gz2'. '/data/bill' will backup as 'bill0.tar.bz2', and '/' will back up as 'root0.tar.gz2'

* You can specify a number of old backups to keep. E.g. When the backup is run, 'home0' will be renamed as 'home1', etc. and a new 'home0' will be created. When the maximum number of backups is reached, old files are automatically deleted. 

* Optionally, a rudimentry disk-check can be performed. The script totals up the size of your most recent set of backups and compares that to the amount of free space left on the destination drive. If it doesn't look like there will be enough space to complete the backup, the script aborts. 

* Optionally, the output of the actual backup commands, and notificaton of a failed free space check, can be e-mailed to any number of e-mail addresses. Two separate variables control warning notification and output notification, so you can choose to recieve none, one or both, as you please. 

Hope this is of use to someone,

Cheers!

---

### Post by Sam on 2005-07-30
Nice script! I haven't tested it yet, I'll do it when I'll reinstall my server, it could be useful.

---

### Post by Nequeo on 2005-07-30
Thanks.

If you do try it out, let me know how it goes. 

Cheers,

---

