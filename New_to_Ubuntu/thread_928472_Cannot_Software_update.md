---
title: "Cannot Software update"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by benjo3683 on 2008-09-24
Hi forumers....my problem is i cannot software update...

i need to update manually....but i dont know how

the error message is as below

[COLOR="Blue"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/COLOR]


Thanks

---

### Post by Paqman on 2008-09-24
The solution is actually given in that error message. Open a terminal and paste in:
```

sudo dpkg --configure -a

```

---

### Post by Sef on 2008-09-24
> Open a terminal

To open the Terminal:

Applications > Accessories > Terminal

---

