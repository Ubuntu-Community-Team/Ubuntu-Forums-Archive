---
title: "Backing Up Multiple MAchines to One Drive"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by Chris_Nickel on 2012-01-31
Hi,
I need to back up the data my companies three critical servers.
All of the servers are running Ubuntu and need to backup to the same external drive.
I'm thinking of just tarballing the relevent files and using a chron to run each backup once a week.
The problem I am running into is that I can't find anything about pathing from the two minor servers through the majoe server and into the external hard drive.
 
Can anyone point me in the right direction?
 
Thanks
 
-Chris

---

### Post by Lars Noodén on 2012-01-31
One way would be to use [tar over ssh](http://meinit.nl/using-tar-and-ssh-to-efficiently-copy-files-preserving-permissions).  

However, that will copy everything each time.  You might consider using [rsync over ssh](http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html), since that will transfer only the changes and be much more efficient.

---

### Post by Chris_Nickel on 2012-02-06
Hi,
Thanks for the reply and sorry for the delay in answering, its been crazy busy here latley.
Anyway, my boss told me he would like me to set up an incremental backup, I.E. only backing up the files that have changed. So I'm guessing that resync is the option I want. 
I'm still a little confused about routing through the main server to the external drive though. For example we have a development server on our network and need to get info off of it to the external drive attached to the main box in the server room. The external drive is swapped out weekly as a take home drive and second drive is hooked up for any current weeks backups.
What do the commands look like to find the external drive so info can be downloaded?

---

### Post by bab1 on 2012-02-10
> **Chris_Nickel said:**
> Hi,
Thanks for the reply and sorry for the delay in answering, its been crazy busy here latley.
Anyway, my boss told me he would like me to set up an incremental backup, I.E. only backing up the files that have changed. So I'm guessing that resync is the option I want. 
I'm still a little confused about routing through the main server to the external drive though. For example we have a development server on our network and need to get info off of it to the external drive attached to the main box in the server room. The external drive is swapped out weekly as a take home drive and second drive is hooked up for any current weeks backups.
What do the commands look like to find the external drive so info can be downloaded?

Chris,

Take a look at [**_[COLOR="Blue"]rsnapshot[/COLOR]_**]("http://rsnapshot.org/"). It's a set of wrapper scripts for rsync.  You can easily create incremental backups using rsync from many machines.  I have three that I backup.  There are more pluses then you realize.  the incremental backups are really deltas of the original file (partial files).  You can do hourly, daily, weekly and monthly if you wish; all over ssh.

---

