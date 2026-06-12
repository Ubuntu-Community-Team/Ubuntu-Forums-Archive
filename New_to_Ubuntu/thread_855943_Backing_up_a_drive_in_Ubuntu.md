---
title: "Backing up a drive in Ubuntu?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by esbo on 2008-07-11
I would like to back up my main drive to my slave drive, where my wubi
ubuntu resides.
Can I do this?
I can't do it in windows because some files are in use.
I think the file formats will be different from Ubuntu ones.

---

### Post by shp on 2008-07-11
I could be wrong but isn't the wubi ubuntu installed to your windows drive?

I think you probably want to use a livecd to back it up

---

### Post by shp on 2008-07-11
This looks like a tutorial to do it in gparted. I think gparted is on the ubuntu livecd
[http://gparted-livecd.tuxfamily.org/larry/move/move.htm](http://gparted-livecd.tuxfamily.org/larry/move/move.htm)

---

### Post by wenuswilson on 2008-07-11
> A problem which you may occasionally encounter is the unexpected loss of some of your work and settings for one reason or another. The causes of such data loss are many and varied; it could be anything from a power cut to accidentally deleting a file. It is highly recommended that you make regular back-up copies of your important files so that, if you do encounter a problem, you will not have lost those files.

It is wise to store back-up copies of files separately from your computer; that is, you should make use of some form of file storage which is not permanently attached to your computer. Options include:

    * Writable CDs and DVDs
    * External hard disks and flash memory devices
    * Another computer on the network

A simple way of backing-up your files is to manually copy them to a safe location (see above) by using the File Browser.

Alternatively, you can use a dedicated back-up application, such as HUBackup:

   1.   Install the hubackup package from the “Universe” repository (see Add Applications).

      				
   2.   To make a backup, press System &#9656; Administration &#9656; Home User Backup.
      					

      				
   3.   Select the files which you would like to make a backup copy of and choose the location which you would like to save the backup to. If you have a CD or DVD writer, it should be present in this list.

      				
   4.   Press Backup and follow the instructions given on-screen.

      				

To restore a backup made with HUBackup, press System &#9656; Administration &#9656; Home User Restore and follow the instructions on-screen.

Some general advice on how to keep good back-ups is given below:

    * Back-up on a regular basis
    * Always test your back-ups after you make them, to ensure that they have been made correctly
    * Label your back-ups clearly, and keep them in a safe place

...from typing in "backup" in System --> Help and Support

---

### Post by wenuswilson on 2008-07-11
> **shp said:**
> This looks like a tutorial to do it in gparted. I think gparted is on the ubuntu livecd
[http://gparted-livecd.tuxfamily.org/larry/move/move.htm](http://gparted-livecd.tuxfamily.org/larry/move/move.htm)

It is.

---

### Post by shp on 2008-07-11
so yeah and whats the problem?

---

### Post by wenuswilson on 2008-07-11
> **shp said:**
> so yeah and whats the problem?

My bad -- Gparted is in the liveCD, just letting you know so if you need it and use the liveCD and spend 10 minutes loading, it will be there.

---

### Post by brettg on 2008-07-11
The easiest way to backup a hard disk is to use dd

sudo dd if=/dev/hda1 of=/path/to/backup.img

Obviously the backup file can't be on /dev/hda1

If you want to compress it you can pipe it through gunzip 

If you want to backup over a network you can pipe it through netcat

---

### Post by esbo on 2008-07-11
OK thabks for all the replies.

Just to clarify the situation I have XP as my main system on drive c:
and Ubuntu in a Wubi format on drive f: which is a seperate physical drive.
I will try some of the stuff mentioned in the thread a bit later.

But what I gave done now if to copy (whilst booted in ubuntu) all the files 

in windows/system32 over onto the f: drive (not the wubi 'partition'/folder).
Or at least I am doing it as I speak (type!).
It has nearly finished, I am just copying the files in there not the folders
as that would take too lonog for a test.

It looks like it will copy them OK. When I tried to do this in windows it
would abort as it would say a file is in use. Note I am assuming that
was one of the files I am copying in the test but I cannot be sure as I
 didn't check, I am just assuming some of those files would have been in 
use by windowsXP. (I will try and copy the rest overnight). I don't
see how any files can be in use as XP is not running and does not know
I am doing it :lolflag:

OK a copy like this may not be bootable, but it can't be that far off?
Surely?

What more would I have to do?

Note I don't necessarilly have to have it bootable but I think a full
back of the drive would be an advantage incase of a failure?

---

### Post by wenuswilson on 2008-07-11
> **esbo said:**
> Note I don't necessarilly have to have it bootable but I think a full back of the drive would be an advantage incase of a failure?

note: HUbackup (if you go that route) used 12 CD-Rs to back up my home folder. 8gb in total.

---

### Post by esbo on 2008-07-11
> **wenuswilson said:**
> note: HUbackup (if you go that route) used 12 CD-Rs to back up my home folder. 8gb in total.

Hmmm..I am not keen on CD's for backup for two reasons.
1. Relaibility
2. Time and number of CD's you need to use.

I have a DVD burner so I could do 12gb in 3 however I have 30gb to back up.
That would be about 7. However I recently bought a 500gb USB hard drive for
60 pounds and I will be using that for backups.

That can hold the equivilant of 100 DVD's, it would cost me about 20 pounds
to buy 100 DVD's, and of course my harddrive is re-usable, and hopefully.
reliable!!

Anyhow that drive will back up my master 80bg drive and my slave 250gb
drive with room to spare!! I can't imagine backing up both to DVD.

In terms of time, reliability and money I think that drive will pay for
it self in the long run. Also I will have a nice compact drive the size
of a book, not a huge box of DVD's!

---

### Post by esbo on 2008-07-11
I just realise my test copy was not, as I slightly suspected, a good test
as I could copy those files in windowsXP anyway.

However I found a folder I did not have access to in XP and I managed to
copy that across in Ubuntu, so I think I will be able to copy everything
across now (hopefully).
I will try a big copy later when I am not using the computer, but it looks
like it will work.
Making it bootable is another matter, but I think I will be halfway there?
Actually I don't think it need to be bootable as if I can copy everything 
across, and back, I don't really see what more I need?

---

