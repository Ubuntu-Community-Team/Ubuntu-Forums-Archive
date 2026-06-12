---
title: "Regarding Mounting the external disk."
date: 2013-01-10
forum: New to Ubuntu
---

### Post by ravi sharan on 2013-01-10
Hello All,
              I recently followed the "Mount/USB - Community Ubuntu Document-ation" just because my ubuntu system wasn't able to detect my Pendrive. Later I figured out that I can just mount it using the Mount drive on "Disk Utility". The problem is just because I followed the documentation I have two Icons on my Desktop which can neither be deleted or trashed to. Any help to remove those icons is helpful. 


Regards,
Ravi Sharan B A G.

---

### Post by d4rk0wl on 2013-01-10
Are the icons still there after the USB pendrive is removed? Also, did you add any folders to the /media directory?
```
ls /media
```

Regards,
- D4rk0wl

---

### Post by ravi sharan on 2013-01-17
Firstly I am sorry for replying so late (was preoccupied with other stuff). Coming to the subject at hand, yes the icons appear even after I remove my Pendrive. That is quite irritating and what is more irritating is I have two such icons now.

---

### Post by audiomick on 2013-01-17
What do you get from the command that d4rkOwl suggested?
```
ls /media
```

I believe that if there is an entry for something in there, it will create an icon.

I just ran that to check, then accessed my windows partition via Nautilus. Before I had done that, there was noting in /media. After I accessed it, there was an icon on my desktop and an entry in /media for it. I suspect you have "orphaned" entries in /media.

---

