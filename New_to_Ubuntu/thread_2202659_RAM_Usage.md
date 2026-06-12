---
title: "RAM Usage"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by LukasLeon on 2014-01-30
Hello,

I am new to Linux, been using Xubuntu 12.10 installed via wubi.exe only for few days now. I am sure this is a rly nooby question, but look at the picture. The task manager says my RAM is used for 8% while the top command in terminal is saying it is about 1,9gigs which is almost 50% of my 4gig Ram. Can anyone explain this to me? 50% is way to high, screen is taken after a fresh reboot. It this somehow related to the memory lock? Everytime i start Ardour i get a message saying my memory is locked.. Thanks. 

[IMG]http://oi58.tinypic.com/4ouc7.jpg[/IMG]

---

### Post by Impavidus on 2014-01-30
```
free -m
```will give more details on memory usage.

The 1.9GB as reported by top includes memory used for cache, whilst the system monitor doesn't include cache.

Using your numbers, used-cache-buffers=1917728-877076-715432=325220kB, which matches the amount reported by the system monitor.

---

### Post by mörgæs on 2014-01-30
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by philinux on 2014-01-30
Wubi is not intended for long term use at all. It's purpose was to allow new users to test out ubuntu. 
I would recommend a dual boot.

---

### Post by LukasLeon on 2014-01-30
After using -free m i see there is only around 500mb used, thanks guys ;), and yeah i am considering dual boot right now.. Thinking about using "Ubuntu Studio".

---

