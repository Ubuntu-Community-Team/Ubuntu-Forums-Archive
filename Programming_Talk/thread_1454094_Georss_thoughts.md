---
title: "Georss thoughts?"
date: 2010-04-14
forum: Programming Talk
---

### Post by eginon on 2010-04-14
Hi,

I'm writing an RSS generator that creates the feeds out of an MySQL database. I've looked at the specifications for rss and for georss. Some of the entries in my database have lat, longs and some do not. I'm wondering what your thoughts for the best way to implement the feed are?

Right now I'm just leaving out the <georss: point> if the database items do not have geo coordinates...I did some googling but haven't seen much on what the standards in this situation are.

---

