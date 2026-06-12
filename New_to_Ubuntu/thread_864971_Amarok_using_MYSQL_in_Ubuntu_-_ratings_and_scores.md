---
title: "Amarok using MYSQL in Ubuntu - ratings and scores"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by crazypiglady on 2008-07-20
I'm using amarok 1.4.8 on ubuntu 7.10 with kde installed.
I read a how to which explained how to change the database from sqlite to mysql.

[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

I did this and it seems to work OK but I cant guarantee it isn't crashing it just didn't when I used it. the problem I have is that when I changed the database, although it rescanned my collection correctly, it didn't copy the score, rating, play count etc. can someone tell me where this info is stored and where mysql is looking. 
if I change back to sqlite, all the settings are there again so they haven't been lost just aren't seen by mysql. if anyone could point me in the right direction, I'd be grateful and can keep using mysql rather than sqlite. many thanks.

PS if you can think of a more appropriate place to post this then let me know and I will.

---

### Post by hyper_ch on 2008-07-20
well, if you change database it will not copy over the old stuff.... you'd have to write a script that manually does it.

---

### Post by donald.gallagher on 2008-07-20
I also recently switched to MYSQL for my Amarok Database from SQLITE.  I seemed to hit a brick wall at 6500 songs - once I installed and set up MYSQL Amarok connected across the network perfectly, created the databases and now I have a library of over 11,000 songs (I digitized my entire CD collection so I can have a digital jukebox with Amarok on an old DELL Dimension 700 MHZ box running Ubuntu 7.10) with about 384 MB RAM and an 80 GB hard drive - works great!

The "hardest" part was getting Ubuntu to log in automatically  and run Amarok :) Took all of 10 minutes to figure it out I think.

---

### Post by crazypiglady on 2008-07-20
hyper_ch, isn't there a file in which all the information is stored that could be accessed by both sqlite and mysql? I'm completely newb about sql. otherwise could you point me in the direction of what sort of script and information. that sounds more complicated that I'd expected. I'll have a look around my system. see if I can change anything. thanks.

donald.gallagher, did you keep your ratings and play counts etc? since no one mentioned it on the original site, it looked like no one else had that problem. maybe they all changed databasesbefore playing any songs but I'd assume there'd be quite a few people like me who used sqlite for ages then changed. 

thanks.

---

### Post by hyper_ch on 2008-07-20
search the net for sqlite mysql conversion

---

