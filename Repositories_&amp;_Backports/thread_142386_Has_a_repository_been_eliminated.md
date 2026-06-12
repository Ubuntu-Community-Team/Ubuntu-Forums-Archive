---
title: "Has a repository been eliminated?"
date: 2006-03-10
forum: Repositories &amp; Backports
---

### Post by daacosta on 2006-03-10
This one:

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages

---

### Post by 5-HT on 2006-03-11
[LEFT]The repository itself should be up (may have been down temporarily), but I have heard that the U.S. mirror has been problematic of late.

I'd suggest you switch to the main server if you are having problems (just remove the 'us' suffix from archive.ubuntu.com)

More explicitly, the 'universe' entry in /etc/apt/sources.list for the U.S. mirrors would look like:

```

 deb http://us.archive.ubuntu.com/ubuntu breezy universe
``` 
The main server would be:
```
deb http://archive.ubuntu.com/ubuntu breezy universe 
``` 
Just edit for whichever of main, restricted, universe, or multiverse repositories you would like to add.

HTH

[/LEFT]

---

### Post by daacosta on 2006-03-11
:mrgreen: 

Thanks!  I did as you explained in your reply and I was able to update everything.

---

### Post by towsonu2003 on 2006-03-12
[QUOTE=5-HT]the 'universe' entry in fstab for the U.S. mirrors would look like:
[/QUOTE]
just to make sure for the total newbies. it is not fstab, it is /etc/apt/sources.list

---

### Post by 5-HT on 2006-03-12
[quote=towsonu2003]just to make sure for the total newbies. it is not fstab, it is /etc/apt/sources.list[/quote] 
Ouch, didn't realize I did that...:-# edited it to what it should be.
Thanks for pointing it out.

---

