---
title: "How do I update iso image via zsync?"
date: 2011-06-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-06-19
Hi,

I noticed that there's a small iso.zsync image file in addition to the regular daily build iso image file.  I understand the zsync file serves to add changes to the iso file. So how do I make changes to the daily iso image file before burning it to CDs?  For example, yesterday I downloaded June 18 daily build iso file but not yet burn any CD, then this morning I saw the iso.zsync file for June 19.  How do I use June 19 zsync image file to add changes to June 18 iso file?

Thanks for your help.

---

### Post by ronacc on 2011-06-19
install zsync it's in the repos . then cd to the directory where the .iso is and run
```
zsync http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync
``` 

note !  adjust your iso name to your arch .

---

