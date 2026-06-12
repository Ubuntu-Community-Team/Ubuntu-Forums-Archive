---
title: "Nautilus in Super User Mode"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-17
```

root@cosp-hq:~# nautilus
Initializing nautilus-share extension
Initializing nautilus-open-terminal extension
seahorse nautilus module initialized
Segmentation fault

```
after this nautilus never opens up in super user mode, though i can use it as a normal user from places of applications> accessories menu as always...

PS:
i do know about gksudo nautilus, it gives the same output...

---

### Post by _sphinx_ on 2008-06-17
Try deleting .nautilus folder in the /root folder?

---

### Post by shoaibi on 2008-06-17
no use :(

---

### Post by pedro_orange on 2008-06-17
Isn't this a known bug with Nautilus?
I think it was caused by a recent update; I've not updated any packages in a while and mine seems to work; so I would not know.

---

### Post by markbuntu on 2008-06-17
I have all the updated packages and a bunch are from hardy proposed.

I have no problems with sudo nautilus.

---

### Post by Troll_the_Great on 2008-06-17
Hit Alt F2 and type

```
gksu nautilus
```.

That will open nautilus in super user mode.Tell me is this if working.

---

### Post by philinux on 2008-06-17
Best to use gksudo etc.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

