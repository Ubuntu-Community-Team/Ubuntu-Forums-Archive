---
title: "Cloning server"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by EskimoSanjoMan on 2014-09-10
Hello folks!

I am quite new to the world of Ubuntu but as a Mac user since I was a small child (my first Mac was a Classic with System 6) I think Ubuntu has an incredible amount to offer and I am huge fan! 

So, this is my ubuntu story! I sold a dream to my boss, a bespoke MIS built on LAMP. I did this with only amateur knowledge of the P in the word LAMP, and very amateur knowledge of LAM. We designed the system and an external developer built it for us using Django, Python, HTML5, MySQL and Ubuntu 12. We picked Ubuntu 12 over 14 because v12 it is certified for that server. This is stored on a dedicated IBM x3650 M4 2U rack server. Everything is going great and the staff and starting to use the system, it is becoming an important business tool. We setup the IBM server, it's internal Raid 6 (via a M5014e ServeRaid Hardware card thing + hardware key of some sort that I entered via the BIOS). As you can tell this level of IT is slightly above my level! We are happy with that server, it is way over spec'ed for the size of the system and user count so we are not concerned about its performance. What we are concerned about is our live (or near live) backup solution which is currently non existent, so I have purchased a couple of second hand HP DL360 G5's (with 2x 300gb SAS drives) which we are hoping to create mirrored Ubuntu 12 servers from our IBM server. We don't mind if this server is anything up to 24 hours behind the main server in terms of its database / raid contents. Our developers have told us they can setup replication of the database so we can move that over to the backup servers easily.

So after all of that typing I guess I should ask the question! Can anybody tell me how I can clone the IBM server onto the HP server. If I was using a Mac I would just use Carbon Copy Cloner and it would just copy the entire contents of the hard drive and away we go but I am concerned that these servers whilst both certified for Ubuntu 12 they use two different types of Raid technology, so I doubt I can just clone them. I have installed Ubuntu 12 on the HP server but now I am struggling to understand how I can get Django and the rest of the system onto the HP server. Any ideas or any tools that can do that for me?

Warm Regards, I totally understand if you gave up reading this a long time ago ;) Not that you will ever read this bit if you do! :)
G

---

### Post by yancek on 2014-09-10
After reading your post, all I can do is point  you to the link below.  Clonezilla can easily clone/restore partitions and entire drives.  Not being familiar with RAID and having used clonezilla only a few times, that's the extent of my knowledge.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by rbmorse on 2014-09-10
Bacula will do what you need (may not be exactly what you want) but you'll probably have to hire a pro to set it up and maintain it.  Well, I say that, but the documentation is quite good...only there's a lot of it and you'll have to master it all. 

The thing is, if this is for business purposes...and it sounds like it is...depending upon where you are you may be faced with some legal requirements in regard to data collection and retention policies and also in regard to safeguarding customer data and privacy.  Tax issues, too. All of this needs to get wrapped into your backup plan. Your accountant(s) can give you some advice about the legal requirements for your locale, and maybe recommend an IT pro to help you architect a backup scheme.

---

