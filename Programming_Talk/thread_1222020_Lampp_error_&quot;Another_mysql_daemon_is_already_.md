---
title: "Lampp error: &quot;Another mysql daemon is already running&quot;"
date: 2009-07-24
forum: Programming Talk
---

### Post by deejay_99 on 2009-07-24
When I start lampp, (sudo /opt/lampp/lampp start)  I get the message "Another mysql daemon is already running"

I researched this and it seems that another mysql service is installed (by ubuntu?) and runs on startup.

I can stop this daemon using:  sudo /etc/init.d/mysqld stop

After doing this, I can start lampp okay and everything seems fine.

My question is: How can I disable or remove this first "non lampp" sql from starting. I am a newbie so precise instructions are much appreciated.

Thanks

---

### Post by deejay_99 on 2009-07-24
I have found the solution ....

---

