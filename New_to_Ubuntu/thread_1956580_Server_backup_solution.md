---
title: "Server backup solution?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by lht2685 on 2012-04-11
Hi,
 
We have a mixed linux server base, but trying to stick with ubuntu server LTS 
 
we have 40+ servers many running my-sql and I need to back them all up.
 
what is a good backup program to use for this and it would be a bonus if it had some central console I could monitor it all from. 
 
Target for the backup's would be our NAS device (that replicate to our DR site).
 
I would like to be able to restore a full server as well as single files.

---

### Post by audiomick on 2012-04-11
Hi. Way out of my range of experience, actually, but I see a lot of reference to rsync.
Have a look here:
[http://askubuntu.com/questions/35353/recommended-method-to-backup-ubuntu-server]("http://askubuntu.com/questions/35353/recommended-method-to-backup-ubuntu-server")

[https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities]("https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities")

Hope that helps a bit.

---

### Post by SeijiSensei on 2012-04-11
The best backup solution for MySQL is to use mysqldump to create plain-text files that can be restored using the mysql client at the command prompt.

For a centralized solution, I'd write a script that runs on the backup server, cycles over the list of database hostnames, and executes mysqldump on each one.  Something like:

```

#!/bin/bash

SERVERS='happy sneezy dopey doc'

cd /path/to/backup/directory

# create a directory for today's backups
TODAY=$(date +%Y%m%d)
mkdir -p $TODAY
cd $TODAY

for s in $SERVERS
do
    mysqldump -h $s -A -u root -p root_password > $s.sql
done

# delete old backup directory
cd ..
rm -rf $(date +%Y%m%d --date='30 days ago')


```

Something like that.  That would create subdirectories with names like "20120411" each night and put the backups into separate files named "hostname.sql".

If the list of servers is long, create a file with the server names, one per line, and use

```
SERVERS=$(cat /path/to/server_list)
```

instead.

If they all have different root passwords, then you'll need some additional massaging.  Perhaps put the servernames and passwords in the server_list file with a delimiter like space or colon between them, and use awk to split the entry.  Make sure the file has root ownership and 600 permissions to protect the passwords.  If you have a common root password, and it appears in the script as it does above, make sure the script has 700 permissions.

All of the servers will need to allow 'root'@'backup_server' to connect.

If you want to create entire images of the servers, use rsync as has been suggested already.  Personally I think that's overkill as you're unlikely to restore a server this way in practice.  You might want to rsync certain specified directories like /etc and maybe /var.  If a server fails you're more likely to end up installing Linux on it again, perhaps even a newer version.  In that case you'll find it easier to restore specific files and rebuild the MySQL databases from the dumps.

---

### Post by SeijiSensei on 2012-04-12
Wow, lht2685, I even spend the time to write you a lengthy script, and we never see your face in this thread again?  I, for one, won't be replying to any future requests for help that you make.

---

### Post by lht2685 on 2012-04-12
> **SeijiSensei said:**
> Wow, lht2685, I even spend the time to write you a lengthy script, and we never see your face in this thread again? I, for one, won't be replying to any future requests for help that you make.
 
Dear SeijiSensei,
 
Your script modified somewhat for my needs are running right now (well been running for a few hours actualy...)
 
So very sorry I did not reply stait away, been very busy all day trying out things using your script as my stating point.
 
In short I'm very greatful for your help, so I hope you will forgive my late reply.

---

### Post by SeijiSensei on 2012-04-12
Thanks for the reply!  I'm sorry if I seemed harsh, but too often I've had the [experience]("http://ubuntuforums.org/showthread.php?t=1927042") of writing extensive replies to questions only to see the person asking the question disappear into the sunset.

I'm glad I could help!  Good luck!

---

