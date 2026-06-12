---
title: "Backup script question"
date: 2008-10-03
forum: Programming Talk
---

### Post by tc101 on 2008-10-03
The following line of script backs up everything in /home/tom/D and puts it in a compressed file in /home/tom/backup:


sudo tar -czf /home/tom/backup/D_Compressedbackup$(date +"%Y%m%d").tar.gz /home/tom/D

How could I change this so it only backs up files in /home/tom/D that have been changed in the last 10 days?

---

### Post by shantzg001 on 2008-10-03
@tc101: You can look at the --newer option of tar to do that. You can specify a date with this option to archive only files that changed after that date.

---

### Post by shantzg001 on 2008-10-03
btw, why are u using "sudo" with ur command. I think its not needed since ur operations are limited within  ur home directory, or are u doing this for some other user on a system where u r admin?

Btw, I wrote a series of articles about backingup up stuff efficiently (especially websites), you can find them here, if u wish: [http://tech.shantanugoel.com/2008/02/17/tip-automating-website-backups.html](http://tech.shantanugoel.com/2008/02/17/tip-automating-website-backups.html)

---

### Post by tc101 on 2008-10-03
> btw, why are u using "sudo" with ur command. I think its not needed 


You are correct.  I don't need it.

I read about the --newer option for tar.  I tried the following but it backed up everything, including things that had not been changed in years:

tar --newer "2008-01-01" -czf /home/tom/backup/D_Compressedbackup3$(date +"%Y%m%d").tar.gz /home/tom/D

I tried a date format "01/01/2008" and got the same result.

I looked at your articles about backing up stuff.  Thanks for doing that.  I see that you use two lines to write newer file names to a file and then back up from that:

find ~ -type f -newer ~/backups/backup_x.tgz > files.txt
tar cvzpGf ~/backups/backup_$date.tgz -T files.txt

I don't understand why it needs to be done that way.  Why doesn't my single line work?

---

### Post by mssever on 2008-10-03
> **tc101 said:**
> I read about the --newer option for tar.  I tried the following but it backed up everything, including things that had not been changed in years:

tar --newer "2008-01-01" -czf /home/tom/backup/D_Compressedbackup3$(date +"%Y%m%d").tar.gz /home/tom/D

I tried a date format "01/01/2008" and got the same result.
Unfortunately, tar --help doesn't explain the format it expects for dates. However, you can specify a filename, in which case it will only store files newer then the mentioned file. So, you could pass in the name of your most recent backup.

---

### Post by tc101 on 2008-10-03
I tried this but again it backed up everything:

tar --newer /home/tom/D/Work/dykes.txt -czf /home/tom/backup/D_Compressedbackup_part4$(date +"%Y%m%d").tar.gz /home/tom/D

the file /home/tom/D/Work/dykes.txt is only a few months old.

---

### Post by tc101 on 2008-10-04
I found the problem.  I just needed to use the mtime option with newer.  This worked:
 

tar --newer-mtime="2008-09-01" -czf /home/tom/backup/D_backup.tar.gz /home/tom/D

---

