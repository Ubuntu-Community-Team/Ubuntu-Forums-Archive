---
title: "Recommendation Please"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by mrwg1975 on 2008-06-27
G'day everybody .

I am currently using windows xp and will be updating to a new computer in the next 6-12 months . This new computer I will take the plunge on and run Ubuntu .
Would people please recommend an open source software backup utility that I can use at the moment on windows xp and then restore those files with the same program when I switch to Ubuntu .
It's just my personal desktop containing spreadsheets , word documents , music etc .
Not after bells and whistles just reliable service .
If it matters I backup to a external hard drive connected via usb .

Thanks

mrwg1975

---

### Post by Xiong Chiamiov on 2008-06-27
If you're just saving some documents and such, I would just copy the folders over that you want; it's much simpler.

---

### Post by mrwg1975 on 2008-06-27
G'day Xiong ,

Thanks for the reply mate .
The current utility I'm using at the moment shows my computer in a tree structure and allows me to tick boxes next to files and folders I want to backup .
Although the method you suggested would be as easy the first time I back up , the utility I'm using at the moment allows me to backup the same files and folders the next time I use it , so the 2nd and consequent backups are one click affairs . The method you suggest would not be as easy the 2nd and subsequent time as I would have to manually choose each file and folder and hope I have not forgotten any since the last backup .
So in addition to the requirements in my first post the software I'm looking for would also have a simple tree structure for me to click which files and folders I want to backup and the option at subsequent backups to use a existing backup selection .

Thanks 

mrwg1975

---

### Post by hyper_ch on 2008-06-27
on linux I'd use rsync... but that's more linux-to-linux backup (well synchornization)

---

### Post by ukripper on 2008-06-27
> **mrwg1975 said:**
> G'day everybody .

I am currently using windows xp and will be updating to a new computer in the next 6-12 months . This new computer I will take the plunge on and run Ubuntu .
Would people please recommend an open source software backup utility that I can use at the moment on windows xp and then restore those files on Ubuntu .
It's just my personal desktop containing spreadsheets , word documents , music etc .
Not after bells and whistles just reliable service .
If it matters I backup to a external hard drive connected via usb .

Thanks

mrwg1975


this is a good one and easy freeware fro windows.
[http://www.snapfiles.com/get/Syncback.html](http://www.snapfiles.com/get/Syncback.html)

---

### Post by Lod on 2008-06-27
> **mrwg1975 said:**
> 
Although the method you suggested would be as easy the first time I back up , the utility I'm using at the moment allows me to backup the same files and folders the next time I use it , so the 2nd and consequent backups are one click affairs .Are you afraid of the command prompt? If not you could check out this thread on how to backup with rsync: [HOWTO: Backup multimedia with rsync](http://ubuntuforums.org/showthread.php?t=187894). 
Otherwise there is Unison, which I quite liked and available for both Linux and Windows. Unfortunately it's no longer developed.

---

### Post by Cadmus on 2008-06-27
If you install cygwin on windows you can get rsync, then from the XP machine rsync over your documents folder to the Ubuntu machine.

This may be redundant, but I'm quickly going to say what rsync is in case you're not familiar with it.

Rsync is a program that copies files like, the clever bit is it compares files in the source and destination and only copies those that have changed, this makes it great if a copy will have to be done over a period of time or may have to interrupted. Also makes it pretty sweet for backups as it only takes a long time to do the first backup.

---

### Post by mrwg1975 on 2008-06-27
G'day ,

Thanks for the replies .

ukripper snapfiles doesn't run on linux from what I quickly read , so I can't install it on the new ubuntu computer when I get it and then restore my files .

Lod terrified of the command prompt . Only interested in utilities with a graphical user interface until I get my feet wet a bit .

Cadmus I don't have the new computer yet . So I want a utility I can be using on windows xp for the next 6-12 months and then install the same utility on the new ubuntu computer and restore my files . rsync sounds great and time saving once you have done the initial backup and is something I will look at when ubuntu is the only computer I have .

So keep the suggestions coming , 

tree structure
one click subsequent backups
graphical user interface
can be installes on windows xp and ubuntu
open source
stable in the sense they have been around for a long time and will continue to be around in the future ,

Thanks

mrwg1975

---

### Post by phidia on 2008-06-27
[Here]("http://www.foogazi.com/2008/02/25/free-linux-backup-solutions/") are several methods to look over-they don't all meet your requirements but some do.

---

### Post by mrwg1975 on 2008-06-27
Thanks

mrwg1975

---

### Post by tamoneya on 2008-06-27
I personally use sbackup at the moment (called simple backup in the link above)  I find it very easy and intuitive.  I am looking to switch over to something a little robust (probably bacula) but sbackup definitely served its purpose and was easy to use.

---

### Post by ukripper on 2008-06-28
> **mrwg1975 said:**
> G'day ,

Thanks for the replies .

ukripper snapfiles doesn't run on linux from what I quickly read , so I can't install it on the new ubuntu computer when I get it and then restore my files .


mrwg1975

i thought you want to backup your files from windows and then install ubuntu and copy your files over then SyncBack would work to for windows but if you want backup solution in ubuntu there are plenty of options.

---

### Post by TVC15 on 2009-03-21
Hi there,

Backup utilities seem to be a hot item on the forum.  A lot of people want something that looks and feels similar to the popular Windows tool Syncback.

But if you really want to take the plunge, then leave those old windows utils behind!

For Linux, the best backup tool for me (and surely many others) is rsync.
Best of all: rsync now has a GUI called grsync that you can find in the Ubuntu repositories.
Looks and feels a lot like Syncback and also works on Samba shares or mounted network drives or over an ssh, ....

Very much worth giving a try!


Good luck!

---

