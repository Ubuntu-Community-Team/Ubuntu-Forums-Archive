---
title: "moving and deleting files/folders"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by AtariBaby on 2012-08-28
Please help me troubleshoot problems with renaming and deleting folders.

Total n00b here. I decided to be more of a true nerd and learn linux, so I set up an Ubuntu machine. Project: Create a machine that downloads video files from the internet, using Sabnzbd+ and Sickbeard. :popcorn:

Problem: It seems that these programs **a)** can't create folders after rebooting, unless I go in first and manually create a folder or at least access these locations. Then these automated processes seem to be able to do it without generating errors.

**b)** These programs are supposed to move files. Sabnzbd+ has files in an incomplete folder then moves the files to a complete folder. Then Sickbeard moves the files to a Popcorn Hour A300. But these programs can never delete the existing files and folders as part of the moving process. I have to go in an manually delete things.

I suspect I've screwed up permissions, but I really don't know. Can someone help me troubleshoot? I thank you in advance for the learning experience.

---

### Post by AtariBaby on 2012-08-30
Well, it was probably an annoying question that every n00b asks. Sorry, couldn't really find definitive guidance and was hoping to.

In the meanwhile, I kept searching. I appear to have solved the problem with a program called "NTFS Configuration Tool".

I have only been running this for 24 hours, but so far, so good.

---

### Post by Megaptera on 2012-08-30
> **AtariBaby said:**
> Well, it was probably an annoying question that every n00b asks. Sorry, couldn't really find definitive guidance and was hoping to..

More likely that no one who knows the answers has been on line and read your question. Don't despair I'm sure someone will be able to help :P

---

### Post by AtariBaby on 2012-08-31
Looks like the configuration tool did NOT solve my problem. My programs SABNZBD are still not able to move files and folders. It copies them but the original files in original locations can't be deleted.

Besides, I want to learn Ubuntu the right way. Help me get permissions down, someone?

---

### Post by lordievader on 2012-09-01
In problem A, where are you (or the program) trying to create folders? And what are the permissions to that folder and who is the owner?

In problem B, I think you have the same problem, you don't own the files/folders. You are perhaps allowed to read the file but that is it. In other words the same information as above would be helpful.

To check out issue the following command:
```
ls -la
```

---

### Post by AtariBaby on 2012-09-01
I thank you very much for this help!

The results of my ls -la. Does this mean "list all including hidden files in detail"?

The drive is partitioned into two parts: the part where ubuntu lives, which is whatever is the default format, and then a partition is NTFS. I dont know if I was guided to set it up this way or it was set up like that by default. 

Problem A is partially resolved and occurs inconsistently. The programs seem to be able to create directories always, but files are not always deleted like they are supposed to be, once moved! Only sometimes. Other times, they download, they copy, but they don't move (i.e., they don't delete, they remain in original location as well as new location).

But Problem B still occurs. This is on the NTFS partition in the folder /media/DATA/sab/complete

The list was multicolored. Text was white unless specified in parentheses below:

drwxr-xr-x  2 misterfantastic misterfantastic    4096 Jul 15 00:21 Music (blue)
drwx------  3 misterfantastic misterfantastic    4096 Jul 15 00:21 .nv (blue)
drwxr-xr-x  2 misterfantastic misterfantastic    4096 Jul 17 08:15 Pictures (blue)
-rw-r--r--  1 misterfantastic misterfantastic     675 Jul 14 23:46 .profile
drwxr-xr-x  2 misterfantastic misterfantastic    4096 Jul 15 00:21 Public (blue)
drwx------  2 misterfantastic misterfantastic    4096 Sep  1 10:03 .pulse (blue)
-rw-------  1 misterfantastic misterfantastic     256 Jul 15 00:21 .pulse-cookie
drwxrwxr-x  4 misterfantastic misterfantastic    4096 Aug  5 18:44 .sabnzbd (blue)
drwxrwxr-x 12 misterfantastic misterfantastic    4096 Sep  1 10:04 .sickbeard (blue)
-rw-rw-r--  1 misterfantastic misterfantastic 2356340 Aug  5 20:58 sickbeard.tar.gz (red)
-rw-------  1 misterfantastic misterfantastic      27 Aug 11 14:31 .smbcredentials
drwx------  2 root            root               4096 Aug 19 19:30 .ssh (blue)
drwxrwxr-x  3 misterfantastic misterfantastic    4096 Jul 16 22:28 .teamviewer (blue)
drwxr-xr-x  2 misterfantastic misterfantastic    4096 Jul 15 00:21 Templates (blue)
drwx------  4 misterfantastic misterfantastic    4096 Aug 13 23:19 .thumbnails (blue)
drwxr-xr-x  2 misterfantastic misterfantastic    4096 Jul 15 00:21 Videos (blue)
-rw-------  1 misterfantastic misterfantastic     178 Sep  1 10:03 .Xauthority
-rw-------  1 misterfantastic misterfantastic    1656 Sep  1 10:04 .xsession-errors
-rw-------  1 misterfantastic misterfantastic    3441 Sep  1 00:14 .xsession-errors.old

The DATA partition wasn't listed, so I changed directories and did the ls -la command again:

drwxrwxrwx 1 root root       8192 Aug 18 11:59 . (green highlighted)
drwxr-xr-x 4 root root       4096 Aug 31 19:08 .. (gray)
drwxrwxrwx 1 root root          0 Mar 12  2007 839e83466a8b8d66f2d04cc8 (green highlighted)
-rwxrwxrwx 1 root root         24 Sep 18  2006 autoexec.bat (green)
-rwxrwxrwx 1 root root         10 Sep 18  2006 config.sys (green)
lrwxrwxrwx 2 root root         60 Nov  2  2006 Documents and Settings -> /media/DATA/Users ("Documents and Settings" is blue, rest is green highlighted)
-rwxrwxrwx 1 root root 2145443840 Sep 29  2009 hiberfil.sys (green)
-rwxrwxrwx 1 root root 2459238400 Sep 29  2009 pagefile.sys (green)
drwxrwxrwx 1 root root          0 Sep 19  2008 PerfLogs (green highlighted)
drwxrwxrwx 1 root root          0 Aug 18 06:39 sab (green highlighted)
drwxrwxrwx 1 root root          0 Aug 16 23:47 .Trash-1000 (green highlighted)
drwxrwxrwx 1 root root       4096 Aug 18 06:36 Users (green highlighted)
drwxrwxrwx 1 root root          0 Aug 18 12:00 watch (green highlighted)

---

### Post by gnometorule on 2012-09-01
In terms of getting an answer to your specific question, those are very specific programs I think only few reading this are familiar with. 

But prior to that, in order to use Linux w/o permanent frustrations, you should read up on some basics. Google 'Linux file permissions', 'super user' (or 'root user') for starters. The ls will make more sense. One thing you'll note is that the last listing you posted has all files owned by the root user. As you probably run your programs under your own permissions, the program might have trouble writing there. One recommended way to read up is straight from the command documentation, which is generally good. For that, open a shell (somewhere under 'accessories' or so, but I'd shortcut it for future use to the top of your screen), and type in 'man man', then 'man chown' and 'man chmod'. If you see too much ouput, also do 'man less | less' (that's a vertical bar (pipe) before the 2nd less). Linux is an excellent OS, but it has a steeper original investment. 

After some such research, I suggest updating with any findings.

Good luck! 

P.S. Other commands that you should consider man'ing:
cd, ls, cat, rm, rmdir, touch, mkdir.

---

### Post by AtariBaby on 2012-09-01
I am reading and learning. Thank you!

I also figured out I had a setting wrong in one of my programs *headsmack*

But I still want to learn this!

---

### Post by Miljet on 2012-09-01
Like most everyone else here, I am not familiar with the two programs you are using.  However I suspect that a lot of your problems stem from this comment
> But Problem B still occurs. This is on the NTFS partition in the folder /media/DATA/sab/complete

You see, NTFS does not support Linux permissions.  Any file permissions on NTFS partitions have to be set at the mount point and they can sometimes be a bit tricky.

Is there some particular reason you are using a NTFS data partition?

---

