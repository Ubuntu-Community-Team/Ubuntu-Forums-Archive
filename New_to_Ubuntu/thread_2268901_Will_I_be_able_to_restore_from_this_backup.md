---
title: "Will I be able to restore from this backup?"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by soundgeek on 2015-03-12
I have re-installed Ubuntu 64-bit & installed updates.

I booted from a Live disk  ran the bundled backup for my root & home (gray) directories.

Given  the error messages below, will I be able to do a full restore from this  backup?  If not, how should I go about reliable backup & restore?

[ATTACH]260582[/ATTACH]

---

### Post by ajgreeny on 2015-03-12
There are no error messages in that odt file; it is simply a list of the files that you presumably backed up in some way, but as there is no indication of how you backed them up it is impossible to help you more.

What application or command did you actually use to backup your system?

---

### Post by soundgeek on 2015-03-12
Thanks for responding ajgreeny.

I used the backup utility that is bundled with Ubuntu. The icon just has the name "Backups".

I tried to back up everything, so that if necessary, I can do a full restore to a known state.

So they are not error messages, aha! The list looked a bit alarming. I was hoping for "you are all backed up, nice and safe now"!

---

### Post by ajgreeny on 2015-03-12
I don't use the backup facility in Ubuntu or Xubuntu so can not actually help you with details of how to restore the backup you have.  I use rsync or grsync which does incremental backups of my home; I don't see the point of backing up the system itself because it is so quick to clean install as I have a separate /home partition.

---

### Post by soundgeek on 2015-03-13
Thanks ajgreeny. I'll see if I can make sense of rsync & grsync.  So it is possible to re-install the system & then restore /home? Won't there be all sorts of system settings to do with applications in under the system root?

---

### Post by HermanAB on 2015-03-13
Just backup your data.  There is absolutely no point in backing up Ubuntu.  It is already on countless mirrors.

---

### Post by soundgeek on 2015-03-14
Hi HermanAB!  So re-installing the system won't lose me system settings or anthing so long as I restore home?

ajgreeny, I have just re-ran Backups in the same way(booting from a Live disk). The messages are error messages. The heading for the report is: "Could not backup the following files. Please make sure you are able to open them".  So the question is the same really: will I be able to restore my system from this backup?

---

### Post by HermanAB on 2015-03-14
You may think now that the system settings etc are a big deal at the moment, but they are not really.  Just backup your data.  One day when your HDD goes to the data fairy in the sky, you would want to install the latest and greatest version of Linux, not some old and tired version of Ubuntu.

---

### Post by soundgeek on 2015-03-16
I'm guessing the the list of files which failed to back up issomething to do with permissions.  Can anyone help me understand why I have got them & how to avoid them & get a full backup with all my scripts & settings etc.?

---

