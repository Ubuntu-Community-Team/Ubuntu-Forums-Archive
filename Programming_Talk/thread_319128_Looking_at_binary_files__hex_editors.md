---
title: "Looking at binary files / hex editors"
date: 2006-12-15
forum: Programming Talk
---

### Post by Julolidine on 2006-12-15
So I have a binary file which is pretty much a header followed by a bunch of data.  The problem is that I don't know how long the header is so I can strip the data from it.  I know I need a hex editor, but what should I be looking for?  

Edit: I guess that wasn't very clear.  What can I pay attention to that differentiates the header from the rest of the file?  

Also, out of the billion hex editors available, is there one that anyone recommends in particular?

---

### Post by pmasiar on 2006-12-15
midnight commander is your trusted swiss sysadmin knife :-) Has hex editor too, of course. And many more goodies. mc to the rescue! :-)

---

### Post by chenxing on 2007-11-16
I also want to know if there is a better binary file editor in linux. It seems that hexedit is not powerful enough for me.

---

### Post by LaRoza on 2007-11-16
I use [http://mh-nexus.de/hxd/](http://mh-nexus.de/hxd/), it is a Windows program, but runs in Wine, although some features won't work.

---

### Post by NathanB on 2007-11-16
> **Julolidine said:**
> So I have a binary file which is pretty much a header followed by a bunch of data.  The problem is that I don't know how long the header is so I can strip the data from it.  I know I need a hex editor, but what should I be looking for?  

First, identify the 'type' of binary file that you have.  Second, go here...
[http://www.wotsit.org/](http://www.wotsit.org/)
...to discover the format of that file -- then you will know exactly what to look for.
> 
Edit: I guess that wasn't very clear.  What can I pay attention to that differentiates the header from the rest of the file?  

This will, obviously, depend on the 'type' of file that it is.

---

