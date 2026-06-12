---
title: "Hard drive storage"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by Momof9Blessings on 2012-01-10
Hi all,

I am using Ubuntu 11.10 and loving it.... 

If I never have to open windows again, I will be so happy!!!  My husband wants me to keep windows on there or make a recovery drive or something in case I have any problems later on.....  (He is using some version of linux not sure which flavor he has settled on - he keeps trying new ones).....

I have a 500 gb hard drive on my laptop (and I have an external as well)....  most of it is full from the windows side - since I have only  been using ubuntu again for about 3 weeks or so....  

My question has to do with "where" is should be storing stuff.... I have a ton of graphics that I use daily as a graphic artist - and tons of photos etc....

Should I leave everything where it is (in windows partition)....  

Back it up somewhere else, reformat or whatever I need to do to that part and have a better storage area....  Would it make it run any faster?  I have links to my windows partition in documents and downloads etc....

Also, when I am adding new stuff (I like to be very organized with my filings) should I just keep adding it to my windows partition?  I know it will drive me crazy to have two areas to look for things.... I already have that with downloads....  

Thank you for your help!

---

### Post by QIII on 2012-01-10
To be honest, for the time being I'd leave what you have in the same closet so you don't break it or misplace it.  If you can access it, don't mess with it.  But DO back up regularly!

---

### Post by BertN45 on 2012-01-10
I would leave it on the windows partition and keep adding new stuff there. After you mount the windows partition in Ubuntu, you can use it as before.

Back up your data to the external drive. 

If in the coming year, if you did not use windows anymore, it could be time to reorganize the windows partition.

---

### Post by Paqman on 2012-01-10
Up to you really. Storing stuff on an NTFS partition isn't a problem. 

The only potential problem could be if you have a bad shutdown on the machine. Your NTFS partition could be flagged and you wouldnt be able to mount it. Normally this is solved simply by booting into Windows and shutting down, so if you've still got Windows available it's not an issue. Even if you don't have Windows there is a way to force it to mount, but it involves cryptic command line shenanigans.

Overall I'd say store your stuff wherever you like. The most important thing is that it's backed up, not what type of filesystem it's on.

---

### Post by Mark Phelps on 2012-01-11
> **Momof9Blessings said:**
> Back it up somewhere else, reformat or whatever I need to do to that part and have a better storage area....  Would it make it run any faster?  I have links to my windows partition in documents and downloads etc....
If you ran some really precise benchmarks, you might find that Ubuntu will run a little faster using a Linux filesystem for data storage than using an NTFS filesystem -- but in actual use, you won't see a difference.

Main concern, as others have mentioned, is that in using an external drive with NTFS, it's easy to have an "unclean shutdown" (as in just removing the drive).  But, with Windows still on the PC, it would only take a couple of minutes to reconnect the drive, run CHKDSK, and get it back.

---

### Post by Kniveau600s on 2012-01-11
Back it up on the external drive and let Ubuntu mount your Windows partition. Moving files over 100Gi could be a little pain..

Enjoy Linux free world! :popcorn:

---

