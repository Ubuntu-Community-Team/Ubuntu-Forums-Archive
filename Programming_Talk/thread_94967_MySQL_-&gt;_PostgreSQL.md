---
title: "MySQL -&gt; PostgreSQL"
date: 2005-11-25
forum: Programming Talk
---

### Post by Jeconais on 2005-11-25
First off: I'm not trying to start a flame war here, honest :)

I've been using MySQL for several years both professionally and privately - however, my current host only comes with MySQL 3.23, and while I can upgrade it myself, I'd rather not (I like having people to shout at if anything goes wrong)

I do, however, have the option of moving to Postgre.

From a code perspective, switching is not going to be a major issue, I wrote the software with a DB abstraction layer by default, so I can stick a new file in place and the site will switch.

From an educational perspective, I'd quite like to switch, to see what the grass is like on the other side.  And from a data quality (transactions) perspective it's attractive.

The small website I'm running is basically on around 500,000pi's a week, and at the moment, is lighting fast.  Page generation time is in the sub 0.01s range.

So, to finally get to the point, I've got the general idea that "MySQL == Fast" "Postgre == Feature Packed".  Is this still true, and if I switch, will I notice a slow down?

Second, are their any "gotchas" to look out for?  Most of the queries I run are simple joins, and obviously I'll be doing a lot of testing before I put it on the server, but any advice would be welcome.

Cheers,

J

---

### Post by hoodwink on 2005-11-25
Good luck. You probably won't be able to avoid the flames.

I would suggest you just give it a try and measure for yourself. With a database abstraction layer, you've already done half of the work.

Over the years, Postges has gotten a lot faster, and MySQL has added some features. If you only have a few tables with simple joins, MySQL is probably OK.

OTOH, Postgres has had the ACID features that real production databases need (MySQL is now beginning to offer some) since the time when MySQL wore a training bra. One senior dba whom I trust says with enough complex table relationships (he has 50 or more in some transactions), MySQL will be slower (no left outer joins) and data corruption is only a question of when not if.

PS. I use very simple tables myself, and I haven't taken the leap to Postgres yet, but it's on my agenda.

Good luck.

---

