---
title: "Backup questions"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by Bo0ddha on 2014-02-11
I am looking for an easy backup solution for a NAS.  This does NOT include the content hosted on the server.  The only thing that I would like to backup at this time is the basic system files.  I want to be able to weekly backup the system to be able to just re-install the system and have my computer restored to a running version.  Currently I have partitioned on the same drive / /home and swap.  Right now rsync seems like a great solution to my problem.  I'm not sure exactly what to backup.  I'm not worried about losing the hard drive to a failure.  If that happens I have all of the things I can not afford to lose on other drives.  I am looking for a time saver in case (when) I break the system (seems to happen the more I play with it ;) ).  If I just tell it to backup / will it back up /home also (I don't want this since it is on a separate partition)?

---

### Post by tfrue on 2014-02-12
The answers to this question varies far and wide depending on what you want to do, like always.

One option would be to set up a bash script that will copy the contents of the desired directories, then compress them to save space, then name then by some schema, then possibly delete the old backups after so many days, then set up a cron job to run the script at certain times, then so on and so forth. 

You could set up a script that would simply back the specified files up to a certain drive/directory and set it as a script so you just have to invoke the script to back up your files.

Bacula may be of interest to you.
[http://www.bacula.org/en/](http://www.bacula.org/en/)

It's what you want, if you can think it, it can probably be coded lol

Chris

---

### Post by Bucky Ball on 2014-02-12
I use Luckybackup. Sounds like a toy or a joke, but believe me, it is not. Very powerful little app. It is in the repositories so simple to install and have a look.

PS: Also lets you do a 'dry' run and shows any errors you might get so you can fix and know it will work before committing. You can be very specific with settings and what you back up. It can also backup recursively which means it only backsup what has changed since the last backup, which saves a heap of time.

(I have triple checked this and it is exactly what it does, even if I change just one word in a document, it will back up just that document and leave the other few hundred as they were if unchanged at the source.)

---

### Post by monkeybrain20122 on 2014-02-12
It sounds like you want to clone the system so you can restore the whole thing either on the same machine or on another in case of hardware failure rather than just backing up data. I use fsarchiver for that
[http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983](http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983)

---

### Post by Bucky Ball on 2014-02-12
Or Clonezilla for cloning partitions/disks. You can create an image or do a direct 'verbatim' clone.

---

### Post by monkeybrain20122 on 2014-02-12
> **Bucky Ball said:**
> Or Clonezilla for cloning partitions/disks. You can create an image or do a direct 'verbatim' clone.

If use Clonezilla the partition restored to has to be at least as big as the one imaged even though the latter may be mostly empty. It is not as flexible as fsarchiver if you may have to restore to a different drive or machine which may very well be smaller (or repartition the same drive to shrink some partitions)

---

### Post by Bucky Ball on 2014-02-12
Just had a look at fsarchiver and like what I see, but don't like this:

> It's still under heavy development so it _*should not be used for critical data.*_

[Italics and underline mine.] Puts me off a tad. I also prefer a clone of the partition rather than a compressed image, but yes, don't like the way Clonezilla insists on cloning the empty space as well. I generally shrink the cloned partition to sidestep the waste of space, though. I notice fsarchiver deals with that for you. I like.

---

### Post by monkeybrain20122 on 2014-02-12
> **Bucky Ball said:**
> Just had a look at fsarchiver and like what I see, but don't like this:

[Italics and underline mine.] Puts me off a tad. I also prefer a clone of the partition rather than a compressed image, but yes, don't like the way Clonezilla insists on cloning the empty space as well. I generally shrink the cloned partition to sidestep the waste of space, though. I notice fsarchiver deals with that for you. I like.

I think that disclaimer was from sometimes ago. I have used it regularly and never had a problem (except for Fedora, which I think is a Fedora problem) I think in 13.10 the version is up to date. In 12.04 may need to install from ppa.

---

