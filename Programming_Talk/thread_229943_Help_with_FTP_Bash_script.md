---
title: "Help with FTP Bash script"
date: 2006-08-05
forum: Programming Talk
---

### Post by chrisfay on 2006-08-05
I am trying to find a simple BASH script that would essentially tar.gz a file locally and then FTP that file to a remote location. I want to transfer some automated backups from my linux box to my windows machine using this script. 

I have found a couple but they won't log onto my ftp server without me entering my password.

---

### Post by cwaldbieser on 2006-08-05
> **chrisfay said:**
> I am trying to find a simple BASH script that would essentially tar.gz a file locally and then FTP that file to a remote location. I want to transfer some automated backups from my linux box to my windows machine using this script. 

I have found a couple but they won't log onto my ftp server without me entering my password.

If you don't want to have the script enter a password, you have to set your FTP server to allow anonymous write access.  What kind of FTP server are you using?  IIS or something else?

---

### Post by chrisfay on 2006-08-06
I did some more Googling and found that it's pretty tough to write a SIMPLE bash script for ftp that includes usrname and passwd as the ftp server won't except the input correctly. I think I have to have an external passwd file which is called by the script otherwise the ftp server will reject it. 

Instead of using ftp, which is pretty insecure anyways, I just wrote a quick backup script and dropped it in cron.daily. I mounted my Windows Samba share folder to my Ubuntu machine and just used that as my backup destination. Did what I needed and probably a bit more secure. Includes a nice transcript email to my mail server to boot...:D

---

### Post by ssam on 2006-08-06
you could try using wput

>  Wput is a free utility that is able to upload files to a ftp-server.

Wput  is non-interactive and background-capable. It can upload files or whole directories and is meant to be a robust client even for unstable connections and will therefore retry to upload a file, if the connection broke.
from man wput.

---

### Post by moma on 2006-08-06
This can be a beginning:
```
#!/bin/bash

ftp_site=ftp://yoursite.com
username=roger
passwd=abc123
backupdir=$HOME
filename="backup-$(date '+%F-%H%M').tar.gz"

echo "Creating a backup file $filename of $backupdir."

# Make a tar gzipped backup file
tar -cvzf  "$filename" "$backupdir"

ftp -in <<EOF
open $ftp_site
user $username $passwd
bin
put $filename 
close 
bye
EOF
```
Study also wput (ref. ssam)

---

### Post by nelskurian on 2009-03-17
thanks..

---

### Post by xMoDx on 2009-06-23
> **moma said:**
> This can be a beginning:
```
#!/bin/bash

ftp_site=ftp://yoursite.com
username=roger
passwd=abc123
backupdir=$HOME
filename="backup-$(date '+%F-%H%M').tar.gz"

echo "Creating a backup file $filename of $backupdir."

# Make a tar gzipped backup file
tar -cvzf  "$filename" "$backupdir"

ftp -in <<EOF
open $ftp_site
user $username $passwd
bin
put $filename 
close 
bye
EOF
```
Study also wput (ref. ssam)

could it be possible to extract the files on ftp site? and how about if you have 2-4 folder same ftp server :confused:

---

### Post by gbkabitz on 2011-07-17
> **moma said:**
> This can be a beginning:
```
#!/bin/bash

ftp_site=ftp://yoursite.com
username=roger
passwd=abc123
backupdir=$HOME
filename="backup-$(date '+%F-%H%M').tar.gz"

echo "Creating a backup file $filename of $backupdir."

# Make a tar gzipped backup file
tar -cvzf  "$filename" "$backupdir"

ftp -in <<EOF
open $ftp_site
user $username $passwd
bin
put $filename 
close 
bye
EOF
```
Study also wput (ref. ssam)



This works perfectly!  Thanks...

---

