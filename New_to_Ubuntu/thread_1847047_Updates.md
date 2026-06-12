---
title: "Updates?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by BruceCM on 2011-09-20
Just installed Ubuntu 11.04 64 bit and checked for updates. It came up with plenty but says something about an 'unauthenticated source', so it won't install them! Can't see which of the 245 odd is/are the problem one(s) to de-select them.

---

### Post by Elfy on 2011-09-20
Try running it from a terminal 

```
sudo apt-get update &&sudo apt-get upgrade
```

---

### Post by raja.genupula on 2011-09-20
post the output of ```
sudo apt-get update
```here

---

### Post by raja.genupula on 2011-09-20
> **forestpiskie said:**
> Try running it from a terminal 

```
sudo apt-get update &&sudo apt-get upgrade
```
same post , please delete mine . this is second time i am facing situation like this .

---

### Post by SirWeazel on 2011-09-20
Just ran into this problem a minute ago. I narrowed it down to the time zone updates. I had to uncheck the time zone updates, then installed all the other updates. After all other updates were installed, i then installed the time zone updates.

Weird, these updates must have just come out because i'm running ubuntu on multiple computers and was updating them. The time it took me to walk downstairs, i ran into this problem. I'll have to go back upstairs to see if there are new updates? Hope this helps.

P.S. know idea why/what caused this error, but that was the work around for me.

---

### Post by BruceCM on 2011-09-20
All sorted, now, thanks! :P

---

### Post by coldraven on 2011-09-20
I just tried to update 11.04, the update manager said there were 100MB of them.
All I get is "404 not found" errors, my internet connection is working fine at 8128kbs.
And who programmed that non-resizable window? Why??

---

### Post by SirWeazel on 2011-10-04
Cold Raven, did u get this fixed?

---

