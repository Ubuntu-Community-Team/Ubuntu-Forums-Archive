---
title: "programming issue"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Chapeen on 2008-08-22
when I type in localhost/mywebsite , the browser says "the requestes url was not found on this server", and my php files are in the www folder.
What can be the problem ?

---

### Post by fedex1993 on 2008-08-23
try doing ifconfig in a terminal and look for 192.168.1.XX not your router but the internal ip of the box and then go to it in a broser.

---

### Post by dje on 2008-08-23
is apache running:
```
ps -ef | grep "apache"
```
post the output here

dje

---

### Post by Iowan on 2008-08-23
If you're accessing the site from the server, try just **[http://localhost](http://localhost)**.
What is your DocumentRoot, and where are your files?

---

