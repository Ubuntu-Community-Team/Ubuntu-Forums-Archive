---
title: "No root file system"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by will1982 on 2012-10-20
I've been trying to save an old junker of mine.
I used Wubi to install Lubuntu, and it went well until I restarted and selected lubuntu from the manager. It progresses, but at the end I get the error in a window: 

> No root file system is defined.
Please correct this from the partitioning menu.

What can I do?

---

### Post by garginis on 2012-10-20
I don't have any experience with  wubi but i'll try to help you.I think that you need to make new partition and install ubuntu in that partition.For partition type choose 'ext2', and for root folder choose '/'.I hope that this will solve your problem.

Cheers, Dragan

---

### Post by will1982 on 2012-10-20
Ah screw it, I'll burn a CD. That's better. :)

---

### Post by garginis on 2012-10-20
Yea, wubi has too much bugs.I had problems with wubi too, so i've burned ubuntu to disk and i did install through boot menu.

Cheers, Dragan

---

### Post by bcbc on 2012-10-21
You'll see this same error when you do the normal install. Boot to a live desktop and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can see what's up.

---

