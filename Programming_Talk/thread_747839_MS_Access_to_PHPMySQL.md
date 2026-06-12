---
title: "MS Access to PHP/MySQL"
date: 2008-04-06
forum: Programming Talk
---

### Post by Waves77 on 2008-04-06
I need to transfer an MS Access based database to MySQL with a webbased frontend (php). I've already extracted the table using MySQL's migration tools, but would highly appreciate any pointers, tips and links from people that have had to solve the same problem...

TIA!

---

### Post by bovus on 2008-04-07
[http://www.kitebird.com/articles/access-migrate.html](http://www.kitebird.com/articles/access-migrate.html)

I did the same thing you want to do a while ago, I just followed the steps on this site, it was easy

---

### Post by Waves77 on 2008-04-07
> **bovus said:**
> [http://www.kitebird.com/articles/access-migrate.html](http://www.kitebird.com/articles/access-migrate.html)

I did the same thing you want to do a while ago, I just followed the steps on this site, it was easy

Thanks, I had found this article... did you keep the Access frontend? My main problem is that I did not create or use the Access stuff, so I'm trying to figure out the most efficient way of analizing the table structures in order to create a new frontend.

---

### Post by bovus on 2008-04-07
when I did it, it was a very simple database with only 3 tables with a key index on each.  dont think ill be able to help you with more complex stuff than moving importing tables into mysql from access. sorry

---

