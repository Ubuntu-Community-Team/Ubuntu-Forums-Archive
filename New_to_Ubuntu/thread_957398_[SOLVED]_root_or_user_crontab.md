---
title: "[SOLVED] root or user crontab"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by batfastad on 2008-10-24
Hi guys

I'm looking to write a shell script and have it run on a schedule using crontab.

But I'm not sure if this should all be done in root's crontab, or my user account's crontab (administrator)

My shell script will use mysqldump to dump databases from 2 different mysql servers.
Then it will use p7zip to compress both files into a 7z archive.
Then it will FTP that file to a remote server.

Should something like this be done as root?
Or should I write all custom shell scripts and cron jobs as my local user?

I'll also be looking to add a cron job to run weex on a schedule at some point as well.

Thanks, B

---

### Post by kpkeerthi on 2008-10-24
Does any of the commands in your script requires sudo? If not it can be added to your user's crontab.

---

### Post by northern lights on 2008-10-24
If the file operations (db dumping and compression) are done within your user's /home, none of 'em should require root rights.
If that's the case, the script needs not be run as root either, thus the cronjob can also be executed as user.

---

### Post by Rocket2DMn on 2008-10-24
As said above, you should use the minimal permissions necessary to get the job done - if sudo/root privileges are not required to perform the task(s), then you shouldn't use root's crontab to perform the operation.  Just be sure that your user (or whatever user you run the script as) has +x (executable) permissions on the script and read/write access to the appropriate files/directories.  Ideally, you should not hardcode your database password into the script either - if this must be done, take away rwx permissions from everybody but the owner/executor of the script.

---

### Post by batfastad on 2008-10-24
Ok cool.
Yes I'll be dumping/compressing into my home folder, then FTPing and deleting all the remaining stuff.

That's excellent info! Thanks everyone :D

---

