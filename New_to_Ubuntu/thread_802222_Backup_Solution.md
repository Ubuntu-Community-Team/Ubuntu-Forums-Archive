---
title: "Backup Solution"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-05-21
My Current backup is in 4 phases. 

1. I did a full backup using simple backup (sbackup) and now daily it runs an incremental backup (I exclude all media as this rarely updates and the remainder comes to about 1.5gb). This is on ONE partition of a 60gb external hard drive. So far it has taken up about 3.2gb of data.

2, I have a small 4gb pendrive onto which I transfer my most important documents and files (about 1.5gb), I do this whenever I feel its necessary.

3. I have another external hard drive onto which I copy all my music, pictures and up to date documents, again I do this after major changes.

4. On the second partion of my 60gb partition, I use partimage to create a complete image of my current install (I remove the music files from my computer when doing this to save space) - this comes to about 15gb.

Number 1 is supposed to be the most up-to-date, 2 is meant for portability (if I need to take my documents anywhere), 3 is mainly for my music but I figure I may as well have my documents there. And 4 is just to have a quick restore solution but since I do 4 only about once in 2-3 weeks it isn't that reliable a place for up-to-date documents.

I think my set-up works because at all times somewhere I'll have the latest files, while at the same time I can always restore everything from scratch (using solution 4).

Now my problem:

Although I like solution 1, and sbackup is easy to use and configure I have never actually had to use it to restore anything. My issue is this. Lets assume my computer crashes, and I use solution 4 to restore the image. Now I have my computer back, clean and simple. BUT i have outdated documents. So what do I do? I have to use sbackup. Now looking at the simple backup restore dialog I see the following: 

A place to select the backup directory and a drop down of available backups. This drop down list has the initial full backup and (now) about 2 weeks of incremental backups. The incremental backups only contain the latest CHANGED files. So in my situation where the computer crashed and I used solution 4 (partimage) to restore my system, I am left with old documents, so now I want to use simple backup to restore my data. How would I do this? Individually going through ALL 20? sets of backups and restoring? Is there no way to sort of do a restore EVERYTHING up-to-date option?

I don't mind using a different backup manager, rather than simple backup if this can solve the problem. The thing is I'm not really the type who goes back 2 weeks looking for a document, if I delete something I usually won't need it, so I was thinking perhaps it would be easier just to do full backups daily and then erase it weekly.

Any thoughts?

---

### Post by indytim on 2008-05-21
I just use Partimage and do the following:

1.  Each Saturday morning I run the ops updates for the week (I have 1 Ubuntu and 2 Kubuntu in use).
2.  I then run a partimage backup of each ops partition along with the /home (separate partition).
3.  This is put on the 2nd h/d (320G SATA).
4.  I then run (about 1-2 x per month) a partimage of my music and photo partitions.  The partimage files are put on the 2nd h/d.
5.  After I've completed #1-#4 each week, the whole shabang is backed up to a 320G external.

It's a bit over the top, but I think I'm prepared for 95% of possible disaster recovery.

IndyTim

---

### Post by abhiroopb on 2008-05-21
Hmmm all that seems far too complicated :P But in any case my problem is I need a DAILY backup of everything, and if its automatic it'll save me a LOT of hassle!

---

