---
title: "Where to save backup?"
date: 2018-02-01
forum: New to Ubuntu
---

### Post by sofiac on 2018-02-01
[SIZE=4][/SIZE]Hi, 

I´m trying to create a backup of a linux ubuntu 14.04 wordpress server in the cloud.  The instructions say to 

[SIZE=2]1. [COLOR=#2F3032][FONT=&quot]Change to the directory in which you wish to save your backup: [/FONT][/COLOR][/SIZE][SIZE=4][SIZE=2]**[COLOR=inherit]cd /your/directory.[/COLOR]**[/SIZE][COLOR=inherit]

[/COLOR][/SIZE][COLOR=#2F3032][FONT=&quot]I´m stuck there.  And before I try interpreting  the Filesystem Hierarchy Standards, I thought that I should ask where should I store the backup?  Where should I definitely not save it? 

By the way, the command that I´m supposed to use according to Bitnami documentation is:

[/FONT][/COLOR]**[COLOR=inherit]sudo[/COLOR]**[COLOR=inherit]** tar -****pczvf**** application-backup.tar.gz /opt/**[B]bitnami


[/B]&#8203;Thanks for any help![/COLOR]

---

### Post by TheFu on 2018-02-01
Welcome to the forums.

tar is the backup solution from 1980.  It is useful for tiny things, not versioned, where the total amount saves is less than 500MB (my arbitrary limit).  Tar was designed to be used with tape, not disks.

Modern backup systems really don't use tape much.  I haven't used tar for backups since the mid-1990s.  There are 50+ different ways to backup a Unix system.

Where should you store a backup?
Simple:
* On different physical hardware (really it should be on 2 different physical media types too)
* Don't use network storage mounts. This is how lots of backups are encrypted by MS-Windows malware. Use a client/server backup system.
* In a different city from the primary storage (natural disasters tend to impact an entire region, so 500+ miles apart is good)
* on encrypted storage (backups that anyone can read just means that anyone will read them)
* and using an encrypted connection between the source and the target  (ssh or a vpn or pre-encrypted backup data)

And while you are at it, the backups should also be 
a) versioned - websites, especially wordpress, get hacked all the time. Best to have 120 days of versioned backups since it is unlikely you'll notice the hack when it happens.
b) automatic - no human buttons to press. Use cron.
c) validated - Some method to ensure the backups aren't corrupted. This is really important for a running DBMS.
d) tested - a backup that has never been restored is just "hope."  Hope is not a plan. A plan, that you know works, is needed.

I really wish books and "helpful web articles" would stop pushing tar.

Don't know anything about Bitnami, except they provide pre-built stuff for free. Not certain I'd trust that, but people do generally consider me paranoid.  We all have different levels of risk acceptance.

So, none of that is really helpful to you - what I wouldn't do and what the "end goals" for a backup should be.  I don't run wordpress on the internet (won't use php myself) due to security considerations, but WP works like many other webapps, so the high level steps are the same.

[LIST=1]
[*]Make a list of everything you need to backup
[*]Check the file system heirarchy to ensure you aren't missing anything
[*]Or just backup everything except /proc, /sys, and other non-real file systems.
[*]If you don't have LVM for storage, you can't use LVM snapshots. With snapshots, you can leave the DBMS running.
[*]No LVM, you have to either dump the data from the database OR shutdown the DBMS to ensure the backup isn't corrupt
[*]The DBMS will determine how to dump/shutdown the DB. Do that.
[*]May want to stop the webapp from running during backups. stop apache/nginx or whatever web-server you are using.
[*]Use a good, versioned, backup tool that can pull the data from the server to where you want it stored.  duplicity, rdiff-backup, rsnapshot, rbackup, there are 50 others.  Most work through an ssh-tunnel and leverage librsync for versioning.  I use rdiff-backup.  "PULL" is important. Never "push" a backup. Pushing a backup is a security failure.
[*]Once all the files are pulled to the remote backup server, you might want to do some clean up of the backup area.  Each server I handle has a different number of backup versions.  I need to remove the oldest versions.  I keep 120 versions for an email gateway - it is high risk.  I don't want 121 versions, so the oldest needs to be removed. The backup tool has an option for that.
[*]Backup done.
[*]Bring the DB back online (or skip if you've used LVM or just dumped the DB)
[*]Enable the web-app server again.
[/LIST]
Those steps are from memory. Don't think I skipped any, but they are high level, so you'll need to figure out the details for your specific setup.

LVM makes backups easier thanks to snapshots.  Highly recommended.

For most people, **duplicity** is the backup tool that simplifies the solution. It encrypts the data, sends it a chunk at a time to many different remote storage types.  It is a little old-school, since it requires doing "full" backups every week or month and diffs daily between the full backups. If you do monthly full backups, then there might be 30 incremental backups to be restored if a failure happens on July 31.  
Rdiff-backup works differently.  The most recent backup looks like a mirror of the source and as backups get older, they are compressed diffs from the most recent backups.  rdiff-backup doesn't encrypt the data at rest (on storage), so that encryption has to be handled outside - simple, use a dm-crypt/LUKS partition.  It does use ssh tunnels between the source and target. It is very efficient with data transmission and storage.  Only 1 "full" backup is necessary. Everything after that is incremental.  I'm going on 7 yrs using rdiff-backup.

The best how-to for rdiff-backup I've seen has been removed by the author. I don't know why, but the archive.org version of the page is still available.  [https://web.archive.org/web/20160330235717/https://www.kirya.net/articles/backups-using-rdiff-backup/](https://web.archive.org/web/20160330235717/https://www.kirya.net/articles/backups-using-rdiff-backup/) Just remember to "pull" the backup.  The source can be a *userid@server-name::/directories*  It doesn't need to be local.  Just setup ssh between the backup server and the source and rdiff-backup will work too. ;)

Clear as mud?

Whatever you do, be certain to verify that a restore of the backup actually makes for a system that can be used.  It is common to need 3-4 attempted backups when first setting this up before you get all the stuff necessary.  Virtual machines are your friend for testing, BTW.

Of course, there are 500 different ways to do this. Others might post their methods here too.  Plus there are 100s of "how to backup" questions in these forums.  Only you can decide which solution works best for your needs, with your current skills, today.

---

### Post by sofiac on 2018-02-01
I´m such a newbie!  I had no idea what I was getting myself into with my question.  

First of all, thank you for sharing such an in-depth perspective.  I will carefully read through it.  

To be honest, my confusion (before I knew that there were so many considerations) centers around the choice of directory for the tar file.  The instructions say first to change directory to where I want to save the file (before later downloading or transfering it to a safe place). 

I simply don´t know the conventions of which directory to choose for this or not to choose.  Can I create a directory dedicated to this?  Is there a particular directory that you suggest that I use?

Again, thank you for all your help!

Sofia

---

### Post by TheFu on 2018-02-01
Where you place the backups doesn't really matter. 
It just shouldn't be anywhere that the rest of the system uses.  On my backup server, I put backups into /Backups/{hostname}/. This is a separate disk connected just for backup purposes. You can put backups anywhere you like.  It is your system and your choice.

---

### Post by sofiac on 2018-02-02
Thank you, thank you!!

---

### Post by TheFu on 2018-02-02
If it is a temporary location, I'd use /tmp/  - that is what that directory is for.  It gets wiped at reboot (or shutdown?) automatically.  But it can't hold an entire backup, usually. Check the partition storage size and available space first.

This is part of the reason that tar isn't the best choice.  While it is possible to stream tar output between machines through a piped ssh connection, pretty much every other backup tool will handle that for you. No need to huge temporary storage areas.

Anyway, if you are happy with the answer, please mark the thread as SOLVED. This helps the entire community - people looking for answers and stops people trying to help from bothering to respond to a thread that isn't being read anymore.

---

### Post by SeijiSensei on 2018-02-02
I bought a small portable hard drive to write backups to: [https://www.newegg.com/Product/Product.aspx?item=N82E16822178741](https://www.newegg.com/Product/Product.aspx?item=N82E16822178741)   Plugged it in, reformatted it to ext4, and away we went.  It backs up my home server and three remote servers that I maintain in the cloud every night.

NewEgg runs specials on these from time to time.

---

### Post by TheFu on 2018-02-02
Before buying a HDD, might be good to see some valid statistics for disk failures.
Every quarter, Backblaze publishes their HDD failures ... [https://www.backblaze.com/blog/hard-drive-stats-for-2017/](https://www.backblaze.com/blog/hard-drive-stats-for-2017/)  Pro tip - avoid Seagate.  There are other vendors with some bad disks in specific sizes that I'd avoid too.

---

### Post by SeijiSensei on 2018-02-03
This one has been working flawlessly for well over a year now.  All manufacturers have bad drives.  I've had failures with WD, Seagate, and Hitachi drives among others.  

Like the reviews for most hard drives at Newegg, there are a lot of fives and a bunch of ones.  The latter usually come from people with failed devices.  Overall the device gets four eggs.

I gave two of these are gifts; both are working well as far as I know

---

### Post by mastablasta on 2018-02-05
my WD external drive inexplicably just went dead after 3 years of very little service. i basically had a few manual backups (work an home) on it nothing else. it just stopped working. and i used it only a handfull of times. so hardly any wear and tear. it was safely stored in original packaging.

also i would put backup to /home/user and then move them to another disk.

---

