---
title: "Performing Backups with Rsync and Cron"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by azurepancake on 2008-04-30
My mother runs a small business with a four computer network and we use a simple, small form factor computer running Ubuntu Hardy to centralize services such as file sharing. 

I've decided to make a backup schedule so that every morning at 2 AM the server automatically backups a folder called "Documents" to a 8GB flash drive called "KINGSTON".

So I loaded up a shell, typed in "crontab -e" and added in the following line:

00 02 * * * rsync -au /home/user/Documents /media/KINGSTON

There are two things I'm not too sure about. First is this the correct way to setup a simple, daily backup? And in the actually backup process will it skip files that haven't been changed and only replace those that have been?

If anyone can give me a little advice or guidance, I would greatly appreciate it.

Thank you!

---

### Post by Monicker on 2008-04-30
Its been a while since I used rsync on a regular basis, but that looks good to me.  The only thing I would add is the -r option, so that it does subdirectories also.

---

### Post by azurepancake on 2008-04-30
Yeah, I have been a bit confused about the difference between the "-a" and the "-r" flag. They both appear to do recursive transfers. 

I'll try -r instead of -a.

Thanks for the reassurance, I'll let you know how it goes. The anticipation is just killing me inside.

Peace.

---

### Post by Monicker on 2008-04-30
> **azurepancake said:**
> Yeah, I have been a bit confused about the difference between the "-a" and the "-r" flag. They both appear to do recursive transfers. 

I'll try -r instead of -a.

Thanks for the reassurance, I'll let you know how it goes. The anticipation is just killing me inside.

Peace.

After reviewing the options for rsync, I think believe you are fine with -a in instead of -r.  It seems that -a includes -r along with several other switches.

My apologies for the misinformation.

---

### Post by azurepancake on 2008-05-01
Hey, it worked perfectly! Thanks so much for the advice.

---

### Post by ego1 on 2008-05-01
I am going to become crazy with a similar problem.
I need get some folder from a windows remote server, and I'd made this file

~/backups/backupSAGE.sh 

#//bin/bash -xv

mount.cifs //10.1.50.201/c$ /home/elder/montaje -o ro,username=administrator,password=password,iocharset=utf8,codepage=cp850sudo
sleep 5 
#ls /home/elder/montaje/backupSAGE/
rsync -avz --bwlimit=50 /home/elder/montaje/backupSAGE/ /home/elder/backups/backupSAGE
sleep 5
umount.cifs /home/elder/montaje

elder@pcelder:~/backups$ ls -la backupSAGE.sh
-rwxr-xr-x 1 elder elder 320 2008-05-01 13:41 backupSAGE.sh
elder@pcelder:~/backups$ 

this file is running from sudo crontab

elder@pcelder:~$ sudo crontab -l
[sudo] password for elder: 
# m h  dom mon dow   command
  0 21  *   *  Mon-Fri sh /home/elder/backups/backupSAGE.sh > /home/elder/backups/backupSAGE.log

I need to run this task as root because the mount command.

If I activate the ls command and deactivate rsync I get the list of files in the log file. If I deactivate the ls command and activate rsync I get a empty log file, and the transfer no happen.

If I make a manual running

elder@pcelder:~$ cd backups/
elder@pcelder:~/backups$ sudo sh ./backupSAGE.sh
[sudo] password for elder: 
building file list ... done
./
Inter, Inc_-031908.ptb
Inter, Inc_-032008.ptb
Inter, Inc_-032108.ptb
Inter, Inc_-032508.ptb
Inter, Inc_-032808.ptb

I don't have /etc/cron.allow neither /etc/cron.deny so I beleive root is the unique personality able to run crontab.

I appreciate some help
Elder

---

### Post by herbster on 2008-05-01
> **azurepancake said:**
> My mother runs a small business with a four computer network and we use a simple, small form factor computer running Ubuntu Hardy to centralize services such as file sharing. 

I've decided to make a backup schedule so that every morning at 2 AM the server automatically backups a folder called "Documents" to a 8GB flash drive called "KINGSTON".

So I loaded up a shell, typed in "crontab -e" and added in the following line:

00 02 * * * rsync -au /home/user/Documents /media/KINGSTON

There are two things I'm not too sure about. First is this the correct way to setup a simple, daily backup? And in the actually backup process will it skip files that haven't been changed and only replace those that have been?

If anyone can give me a little advice or guidance, I would greatly appreciate it.

Thank you!

If you want to synchronize the destination with the source, use the "--delete" option. This will keep the destination an exact copy of the source at each rsync. Depending on your connection, you may also want to use "-z" though that's generally more beneficial for a slower connection.

---

### Post by ego1 on 2008-05-02
> **herbster said:**
> If you want to synchronize the destination with the source, use the "--delete" option. This will keep the destination an exact copy of the source at each rsync. Depending on your connection, you may also want to use "-z" though that's generally more beneficial for a slower connection.

Thank by --delete option, but I haven't gotten the conection jet. I wrote "If I deactivate the ls command and activate rsync I get a empty log file, and the transfer no happen."
Thank again, but I don't get the transfer.
Elder

---

### Post by DanneUK on 2008-05-08
Try putting the .sh file in /root 

I found I got errors when a sudo cron job ran a file that was in my home directory

---

