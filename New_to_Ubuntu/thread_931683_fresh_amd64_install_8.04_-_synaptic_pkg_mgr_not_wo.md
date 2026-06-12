---
title: "fresh amd64 install 8.04 - synaptic pkg mgr not working"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by bth73 on 2008-09-27
finally got high speed cable and did a new install as last one was bad - (comp turning itself on). followed the multimedia new sticky after doing initial update. when I got to googleearth, the user agreement came up with no way to ok it so i reset terminal closed and turned off comp and went to bed. fired it up today and update mgr informed of new updates but i get this message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." synaptic mgr won't even open.

help please
thanks, bruce

---

### Post by drs305 on 2008-09-27
Run:
```
sudo dpkg --configure -a

```

By the way, for many apps when you get to a point where you need to make an preselected input, try using the tab key until you see the "OK" or other selection highlighted, then hit Enter.

---

### Post by bth73 on 2008-09-27
THANK YOU VERY MUCH, been sick for a week now and brain not working very good right now.

---

### Post by Crafty Kisses on 2008-09-27
If this has solved your issue, please mark the thread as solved. :)

---

