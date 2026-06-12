---
title: "Webmin Backup errors"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by James1984 on 2012-11-29
Hello,

I've been asked by my boss to backup our Ubuntu Webserver to a NASbox on site via FTP and i just can't get it to work, not even on my Office PC which i have also tried.

I installed Filezilla Server on my office PC and set everything right, username, password, added read and write permissions to the shared folder which is on my desktop.

And i get this error;

[B]Performing backup of /home/website/site/sqlbackup to 127.0.0.1:/ ..

FTP login failed : PASS ********* failed : Login incorrect.

tar (child): admin@127.0.0.1\:/: Cannot open: Operation not permitted
tar (child): Error is not recoverable: exiting now [/B]

The password is write i just get it :confused:

I want to backup to the NAS box really but i wanted to see if i could get it to backup to my PC first thinking if it was something on the NAS box.

The error i get on the NASbox is;

[B]Performing backup of /home/website/site/sqlbackup to 10.xxx.xxx.xxx:/backup/SiteBackup/ ..

FTP write failed : STOR /backup/SiteBackup/ failed : /backup/SiteBackup/: No such file or directory

tar (child): [email]admin@10.xxx.xxx.xxx[/email]\:/backup/SiteBackup/: Cannot write: Operation not permitted
tar (child): Error is not recoverable: exiting now
.. backup failed![/B]

Thanks
James

---

### Post by James1984 on 2012-11-29
Also the Operating system version is Linux 12.04.1 and the webmin is version 1.600

Thanks
James

---

### Post by James1984 on 2012-11-30
Does anyone have any ideas??

I cant even backup to the local server :(, i get this error trying to do it locally;

[B]Performing backup of /home/website/site/sqlbackup to /home/hwebsite/backup ..

tar: Removing leading `/' from member names
tar (child): /home/website/backup: Cannot open: Is a directory
tar (child): Error is not recoverable: exiting now
.. backup failed![/B]

James

---

### Post by James1984 on 2012-12-04
Can anyone at least tell home to map a drive of the server files on  a windows Operating system so i can make a schedule backup of the files using our backup software. 

So i don't have to copy and paste from Filezilla FTP Client to the backup NASbox manually.

James

---

### Post by James1984 on 2013-01-07
Anyone at all?????

---

### Post by James1984 on 2013-01-16
Heeellllooooo ):P,

Can anyone help me at all with this, i would like to be able to use this backup feature without having to do copy and paste it manually every time through Filezilla Client

Thanks
James

---

### Post by d4m1r on 2013-01-16
Ok, this thread is kinda convoluted...Can you clearly explain what exactly you are trying to accomplish?

---

### Post by James1984 on 2013-01-17
I want to use the webmin backup schedule to backup our ubuntu server website to a network storage drive but it won't do it and won't even do it locally.

Errors are shown above

---

### Post by CharlesA on 2013-01-17
Sounds like you are using tar incorrectly.

If you want to backup the whole directory, you'd need to run tar like this:

```
tar /path/to/file.tar.gz --directory=/var/www somefolder
```

[http://unixhelp.ed.ac.uk/CGI/man-cgi?tar](http://unixhelp.ed.ac.uk/CGI/man-cgi?tar)

---

### Post by James1984 on 2013-01-22
Where do i run this code please.

Do i put this in the Extra Command line Parameters in the file system Backup feature?

Thanks
James

---

### Post by CharlesA on 2013-01-22
Try running it in a terminal.

I don't use Webmin, so I do not know how to run a specific command from there.

---

### Post by James1984 on 2013-01-23
> **CharlesA said:**
> Sounds like you are using tar incorrectly.

If you want to backup the whole directory, you'd need to run tar like this:

```
tar /path/to/file.tar.gz --directory=/var/www somefolder
```

[http://unixhelp.ed.ac.uk/CGI/man-cgi?tar](http://unixhelp.ed.ac.uk/CGI/man-cgi?tar)

Doesn't matter I've sorted it now but just to double check.

1) The file.tar.gz triggered something that i didn't put in the location for backing up to :-), I've selected **"tar"** for the format i want it to be.

2) Does it need to be **"file.tar.gz"** or can it be **"file.tar"**?

3) I've got a backup i'm doing for the sql 3 times a week that is labelled **"file.sql.gz"**, can it be **"file_SQL.tar"** or should it be the first one?

Thanks
James

---

### Post by CharlesA on 2013-01-23
The only difference between tar and tar.gz is tar.gz is compressed using gzip. If you desire, you can not bother with compression by just using .tar instead of .tar.gz.

---

### Post by James1984 on 2013-01-23
ahhh i see, well i set it on the backup to use gzip for compression so we'll soon see.

Thanks you for your help

---

### Post by James1984 on 2013-01-24
one more question :-)

It says backup scheduled?... NO

But i've set to run for example every Sunday at 00:00 am

Have i set it wrong?

Thanks
James

---

