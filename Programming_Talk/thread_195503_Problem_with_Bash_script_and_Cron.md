---
title: "Problem with Bash script and Cron"
date: 2006-06-12
forum: Programming Talk
---

### Post by scrook on 2006-06-12
Hi all,

I've recently discovered the joys of bash and I've been looking to automate certain tasks such as backups that I try to do periodically. I wrote a script to backup my mozilla thunderbird directory so that I have a backup of my email in case I have a hard disc die on me or I hose the OS doing something stupid.

The script works as intended when I run it directly via the terminal, however when I set kcron to run it at a specific time the tar.gz file the script creates is corrupt. The tar file should be about 370MB, however when the script is run through kcron the file size is about 40MB. The specific error that the gui archive program (in gnome) gives is that there is an unexpected EOF. My script is simple and I have included it below. If anyone has an idea where the problem may lie I'd really appreciate a pointer or two.

Code:
> 
#! /bin/bash

#create tar file containing Thunderbird Mail Directory
tar -cvzf /media/hda4/Setup_Files/Mail_backups/$(date +%F).tar.gz /home/scott/.mozilla-thunderbird/;

#check that tar exits without errors before deleting old backups
if [ $? -ne 0 ]; 
then echo 'ERROR!!!';
exit 255;

else

#Delete any backups older than 21 days
find /media/hda4/Setup_Files/Mail_backups/ -ctime +21 -delete;
fi;


---

### Post by nanotube on 2006-06-12
[QUOTE=scrook]Hi all,

I've recently discovered the joys of bash and I've been looking to automate certain tasks such as backups that I try to do periodically. I wrote a script to backup my mozilla thunderbird directory so that I have a backup of my email in case I have a hard disc die on me or I hose the OS doing something stupid.

The script works as intended when I run it directly via the terminal, however when I set kcron to run it at a specific time the tar.gz file the script creates is corrupt. The tar file should be about 370MB, however when the script is run through kcron the file size is about 40MB. The specific error that the gui archive program (in gnome) gives is that there is an unexpected EOF. My script is simple and I have included it below. If anyone has an idea where the problem may lie I'd really appreciate a pointer or two.

Code:[/QUOTE]
hmm, well, your script looks ok to me (except you dont really need the semicolons at the end of the lines ;) )

some things that come to mind: maybe the cron job runs as a different user and does not have permissions to read all the files in the dir? or maybe kcron does something funky, and you should try the regular crontab way, and see if that has better luck?

---

### Post by scrook on 2006-06-13
Thanks for the response nanotube. I took your advice and looked at crontab. What's really wierd is that the script started functioning properly via cron after I had it write the output logs of the job to a file. Here is my crontab:

# Backup Mozilla Thunderbird Mail
0 3 1,15 * *    sh /home/scott/BASH_Scripts/mail_backup.sh >>/home/scott/mail_ba ckup_log.txt
# Backup Weight Graph
0 2 * * *       sh /home/scott/BASH_Scripts/wg_backup.sh


The second script doesn't utilize tar and is working fine even though it doesn't write a log anywhere as far as I can tell. I've looked around for some sort of master log for cron but haven't found it.

---

