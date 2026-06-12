---
title: "FTP sync?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by ubudave on 2008-10-22
Hello all

I have been trying out ubuntu for a bit now and I have the good fortune to have found a old laptop that works great with it. I am now using three computers and I am starting to have problems keeping track of my data.  I have a domain with 500gb of space for files so I thought I would start to use ftp to sync files there then down to my computers. To sum this up does anyone know of a easy to use and understand way to sync files via ftp?  Thanks in advance for any help!

---

### Post by bodhi.zazen on 2008-10-22
I am not so good with ftp, may I suggest samba, NFS, or rsync ?

It depends on what you mean by "sync".

---

### Post by Nxion on 2008-10-22
As bodhi.zazen suggested, rsync sounds like the way to go. 

What is your domain hosting service company?

---

### Post by ubudave on 2008-10-22
I use Bluehost for domain hosting.  I Have a windows PC at work.  I have a Mac at home and I am playing around with Ubuntu on a laptop.  I want one central place to keep "My documents" and music/video files so that If I add something or make a change I can get it form any computer I am on.

---

### Post by Nxion on 2008-10-22
Lets approach this from another way. How much data do you want to sync? What is the total size?

---

### Post by ubudave on 2008-10-22
> **Nxion said:**
> Lets approach this from another way. How much data do you want to sync? What is the total size?


it's going to be between 40-60gb total. No single file over 1.3 gb

---

### Post by jerome1232 on 2008-10-22
I would go rsync since it can send only what needs to be updated, only the first round of transfers are gunna take 2 years :D. You don't want to transfer 40-60G every time you want to sync up.

---

### Post by ubudave on 2008-10-22
Ok looks like its time to learn rsync.  I have been trying to avoid that :)  I will use a ext hard drive to move the data at first.  That should save a lot of time.  Thank you for your advice.

---

### Post by Nxion on 2008-10-22
Here is a little bit more info fro you
[URL="https://help.ubuntu.com/community/rsync"]
https://help.ubuntu.com/community/rsync[/URL]

---

### Post by Titan8990 on 2008-10-22
Also, the rsync man page is one of the best resources out there.

---

### Post by bodhi.zazen on 2008-10-22
rsync is a snap to learn and you can tunnel over ssh if you wish :twisted:

[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

---

### Post by Moglum on 2009-03-16
I am a fresh Ubuntu user - loving it so far ;) - but I found a pretty simple way to synchronize files over FTP, using lftp.

Create a script for lftp:
```

open ftp://username:password@ftp.mydomain.cz
mirror -R -v --only-newer /home/moglum/folderToBackup /remoteFolder

```
and a shell script to execute it 
```

lftp -f backupScript.txt &

```

This makes a backup of your local folder to the remote server. 
To get your files from the server you would use a similar script. Something like this:
```

open ftp://username:password@ftp.mydomain.cz
mirror -v --only-newer /remoteFolder /home/moglum/folderToBackup 

```

Simple enough for me and working well. man page for lftp is a great resource. You can easily backup multiple folders, log the activity to a file or schedule your backups.

---

### Post by stefsegers on 2010-02-11
Hi Moglum,

You tutorial is really great. Since I am a real noob on Ubuntu (Mac User) this was very hard for me to do.

I made the script working with lftp and it's downloading/mirroring the webserver to my local machine.

There are some thing I still have a question about and I can't find the answer.

1. how can I schedule the lftp scrip.txt to run every week or so?
2. can I monitor and see how far the ftp mirroring is?
3. can I add more servers in my scipt.txt? So I have 2 webservers I want to backup to my local machine.

I hope you understand what I am trying to do and can help me out here


Stefan

---

### Post by qwerty9967 on 2011-08-30
Ubuntu has a great way to do scheduling of anything that can be run from the command line.  There is a great tutorial for this that can be found here:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I hope this helps.

---

