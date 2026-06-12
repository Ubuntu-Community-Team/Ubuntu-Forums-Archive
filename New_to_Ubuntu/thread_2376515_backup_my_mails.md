---
title: "backup my mails"
date: 2017-11-03
forum: New to Ubuntu
---

### Post by med304 on 2017-11-03
Hello everyone. 
Have been using Evolution for quite a time. facing a heap of bugs every other day. I use mail Backup X in my Mac which runs impressively. Looking up for a tool in ubuntu that matches my expectation. any suggestions please?

---

### Post by TheFu on 2017-11-05
Welcome to the forums.

I don't know anything about Apple stuff (tried it for a few weeks, no real control possible).
On Linux/Unix systems, all user data is stored in your HOME directory. That means any emails that are stored locally are also placed there somewhere. This won't help with imap emails, just pop3 stuff that gets pulled local.

There are multiple different types of backups for Unix systems.  Generally, they are split into 4 categories.
a) Full system backups - which have to run as root
b) End-user only backups - which can run as the end user
c) Image-based backups - these must be run from a different boot device and require downtime.
d) Versioned backups - these store many days of backups efficiently and usually require 1-3 minutes per had to create a backup version.

So, I use a+d to minimize down time and have everything necessary to restore should something terrible happen.  I use rdiff-backup. It doesn't have any GUI, but it is fast and convenient once setup and working the way you like.  

So, few tools to look into:
* rdiff-backup - anything, with versioning
* rsync / grsync - anything, versioning isn't automatic.
* aptik - User data
* clonezilla - disk imager
* fsarchiver - partition imager
* duplicity / deja dup / duplicati (there are many others based on duplicity)

I suspect what you want is aptik.

---

### Post by HermanAB on 2017-11-06
Well, you could use an always BCC command and a dummy account with outlook.com, gmail or yahoo for free email backup.  Why waste your own money on an extra disk drive?

---

### Post by Quarkrad on 2017-11-06
I use Thunderbird as my email client for 5 accounts I have - these accounts are mainly imap and I also have a lot of local folders.  Everything is located in /.thunderbird so if ever I have to rebuild my system I copy /.thunderbird from my backup disk and I have everything working asap.  I backup /.thunderbird to a physical hd but the back medium could also be a cloud server that is backing up in real time.  This approach is not as full proof/sophisticated as outlined by TheFu but it shows (again) there are many options to backup your mail within the ubuntu environment.  (Although off-topic the same applies to Firefox - everything is in /.mozilla so by backing up ./thundbird and ./mozilla you can have your email and browsing environments up and running in no time).

---

### Post by leunam12 on 2017-11-06
Doesn't Evolution have an integrated backup command under "File"?

---

### Post by Quarkrad on 2017-11-06
I do not use Evolution so cannot answer your question - someone who does might answer soon.  However, if you keen backing up emails are you not keen on backing up other things (e.g. Bookmarks, personal documents, etc)?  There are a number of utilities built into ubuntu where you can backup a number of files/folder etc in one go.  For example, I use gadmin to backup all sorts of files/documents (including all my mail) as the same time - these utilities can be configured to perform the backup either manually (you running the backup when you want) or automatically (scheduled times/events).  TheFu listed a number of these tools - backups can be simple or very sophisticated - depends on your needs.  I think many people tend to backup *many things at once* rather than individual applications one after the other.

---

### Post by TheFu on 2017-11-06
Nicely put Quarkrad.

By getting 3 things, most people can restore to a different system with minimal fuss and still have all the applications, data and system settings.  Two of these things are tiny and the 3rd is completely under the users control for how large it gets.

They are:

[LIST=1]
[*]**/etc** - this is where system settings are stored and it is TINY! Grab it with every backup, even if you do them24 times a day.

[*]**List of manually installed applications** - there are multiple ways to get this list in a format to automate re-re-re-installing them on the next system.  apt-mark can generate the list. dpkg --get-selections generates a list, but it gets all the installed packages, not just those manually installed.  Aptik, a relatively new GUI program, will grab a list. I'm unsure of how good this list is at restore time. People seem to like aptik. Anyway, having a way to put all your favorite apps back is a huge time saver when you get to a new machine, especially for a desktop.

[*] Your **HOME directories**. Linux is multi-user, so I won't assume only 1 userid is being used.  Actually, I have 3 different userids on my systems to make different things easier to accomplish and to test out new programs/settings without risking my normal accounts.  Obviously, nothing huge gets put into HOME unless the user does it on purpose.  It isn't hard to skip backing up huge video+audio files, if you don't have room on the backup storage.
[/LIST]
Those 3 things are the difference between a minor inconvenience and total disaster when it comes time to recover, for a desktop machine.

---

