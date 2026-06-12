---
title: "Fatal error: Call to undefined function curl_init() in /var/www/filename"
date: 2009-03-10
forum: Programming Talk
---

### Post by alcatraz678 on 2009-03-10
Hey guys,

I dont know why im experiencing this problem. I checked google and found out that I dont have curl installed in my PHP.

My php.ini file doesn't have curl. I installed my PHP from LAMP through this [guide]("http://www.howtoforge.com/ubuntu_lamp_for_newbies").

So I think my php doesn't have curl. How do I install one?

---

### Post by LegendofTom on 2009-03-10
Try this:

apt-get install php4-gd php4-curl 

you might not need gd.

---

### Post by alcatraz678 on 2009-03-10
> **LegendofTom said:**
> Try this:

apt-get install php4-gd php4-curl 

you might not need gd.

hi tom,

i changed something, and it worked. i put sudo apt-get install php5-curl

hehe my php is version 5

and it worked! thanks man!!

---

