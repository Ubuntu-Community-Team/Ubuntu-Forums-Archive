---
title: "Kill npviewer.bin via launcher?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by mispelt on 2008-10-12
Hi,

I've been using Ubuntu for quite some time, but I still haven't learned a lot of the finer points of our favorite OS. I've been having some troubles with Firefox and npviewer.bin, which from what I understand is fairly common.

To combat this, I've placed a launcher for my system monitor on my panel so I can kill it fairly quickly, but I wonder: Is there a more efficient way to do this? Is there a way I could create a launcher that kills npviewer.bin with a single click?

How would I create something like this, and how would I add it to my panel? Is it even possible in the first place? I apologize for my ignorance, but how else am I supposed to learn, right?

---

### Post by freak42 on 2008-10-12
use the killall command:

e.g.
```
killall npviewer.bin
```

or 
```
killall npviewer
``` (depending on how the process is really named (try top to find out)

if you need root rights to kill the process prepend gksudo
```
gksudo killall npviewer.bin
``` as your launcher command

---

### Post by mispelt on 2008-10-12
Thanks! I knew it was something simple. Works like a dream.

---

