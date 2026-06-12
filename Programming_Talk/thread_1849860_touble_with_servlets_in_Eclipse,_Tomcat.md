---
title: "touble with servlets in Eclipse, Tomcat"
date: 2011-09-25
forum: Programming Talk
---

### Post by jdunn on 2011-09-25
I have Eclipse EE Indigo and Tomcat 7 installed on Ubuntu and Windows.  I'm a noob when it comes to JEE.  I was able to get a simple servlet to work on Windows with Tomcat using port 80.  On Ubuntu I can't use port 80 because of root restrictions for port < 1024...So, I'm using the default port 8080.  The HTML part of my code works fine but when a post/get calls the servlet code, I get "Cannot connect to destination (localhost)" message in the web browser.  Are there any ideas what I'm doing wrong?

Enclosed is the archived eclipse project.

Also, I tried to force port 80 access with a feeble attempt at iptables modification and Authbind but had no luck.

---

