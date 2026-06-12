---
title: "Check for program upgrades in Java"
date: 2010-08-14
forum: Programming Talk
---

### Post by chaanakya_chiraag on 2010-08-14
I wrote a program called Musik hosted on Sourceforge.  It's written completely in Java.  I would like my program to notify users that a new version is available when I upload it.  How would I do this in Java?  It doesn't need to actually download the update, although that would be a bonus.  All I need it to do is check for the update.  Thanks!
- Chaanakya

---

### Post by myrtle1908 on 2010-08-14
> **chaanakya_chiraag said:**
> I wrote a program called Musik hosted on Sourceforge.  It's written completely in Java.  I would like my program to notify users that a new version is available when I upload it.  How would I do this in Java?  It doesn't need to actually download the update, although that would be a bonus.  All I need it to do is check for the update.  Thanks!
- Chaanakya

Assuming your update resides on a HTTP server somewhere ...

On program launch, use a HTTP Client to poll the web server to check the update file(s) last modified date.  If greater than the current version, download and apply locally.  It's quite simple.  [http://hc.apache.org/httpclient-3.x/](http://hc.apache.org/httpclient-3.x/)

Good Luck.

---

### Post by chaanakya_chiraag on 2010-08-15
Thanks. I'll look into it later and let you know how it goes.

---

### Post by chaanakya_chiraag on 2010-08-31
In case anyone else is interested, I solved the problem by parsing an RSS feed of my project (it's hosted on Sourceforge) and looking for the next version string in the link.  I used rssParser, obtained and documented at
[http://java.sun.com/developer/technicalArticles/javaserverpages/rss_utilities/](http://java.sun.com/developer/technicalArticles/javaserverpages/rss_utilities/)

---

