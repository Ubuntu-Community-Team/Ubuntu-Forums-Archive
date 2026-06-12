---
title: "Where does Kindle Cloud Reader App store the downloaded books?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by akoubu.9a on 2014-04-26
On the Chrome browser, I have installed the Amazon Kindle Cloud Reader app ([http://read.amazon.com](http://read.amazon.com)). I have downloaded some of my Kindle books onto my computer. Where on my computer are the downloaded files?

---

### Post by caver12 on 2014-04-26
Why don't you go into Nautilus and use the search funtion tofind the name of a book you downloaded?
Make  sure that under Devices your computer is highlighted so it will search your entire file system.
When it finds it you will be able to see the path. If you don't see it right away right click on it and select properties.

---

### Post by jrgsampaio on 2014-12-29
> **caver12 said:**
> Why don't you go into Nautilus and use the search funtion tofind the name of a book you downloaded?
Make  sure that under Devices your computer is highlighted so it will search your entire file system.
When it finds it you will be able to see the path. If you don't see it right away right click on it and select properties.


Well, if you are using chrome, go to Nautilus and under home press ctrl+h to show hidden files.  Then find 

.config/google-chrome/Defaults/database/https_read.amazon.com_0 
In this folder you will may find some SQLite3 files... these are the books you have downloaded from amazon using kindle cloud. Good luck!
Jorge

---

