---
title: "Amarok"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by bgast1 on 2008-09-05
Does Amarok have any limits as to how many CD's can be included in it's collection. I have ripped a couple of CD's to my hard disk where I have told Amarok to look and they don't show up anywhere. I don't know for sure how many CD's it has in the collection but I would guess that it is at least 250 gigs in MP3's.

---

### Post by northern lights on 2008-09-05
What are you using for your database?
For large collections it is advisable to refrain from using SQLlite and going with MySQL.

Further, are these files on an internal HDD?
Amarok still dislikes USB devices for the premanent collection.

---

### Post by bgast1 on 2008-09-05
External USB hard drive 750 Gig. Also probably SQLite. Anything deeply involved in switching over to MYSQL other than changing it in preferences?

I am doing a rescan to see it that picks the missing CD's up. 

edit: I did the rescan and it picked up the missing cd's but if I try to change to MYSQL from SQLite my collection disappears.

---

### Post by lintoon on 2008-09-05
Open Amarok, go to the tools menu and select "Rescan selection".  I think that's what it was.  It's been a while since I've added anything but there's only 2 options and the other one's "Update collection".  Must be one of them.  Good luck.

---

### Post by rihannaisco on 2008-09-05
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by dizee on 2008-09-05
> **bgast1 said:**
> External USB hard drive 750 Gig. Also probably SQLite. Anything deeply involved in switching over to MYSQL other than changing it in preferences?

I am doing a rescan to see it that picks the missing CD's up. 

edit: I did the rescan and it picked up the missing cd's but if I try to change to MYSQL from SQLite my collection disappears.

i'm not sure how to do it myself but MySQL requires a bit more setup than simply changing it in the preferences. 

[http://amarok.kde.org/wiki/MySQL_HowTo#Database_Conversions](http://amarok.kde.org/wiki/MySQL_HowTo#Database_Conversions)

looks fairly complex.

---

