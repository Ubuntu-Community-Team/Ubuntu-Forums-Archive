---
title: "slcreator -&gt; SDL Parachute Deployed"
date: 2006-04-07
forum: Programming Talk
---

### Post by TomG on 2006-04-07
Hi

I always get these error while trying to run slcreator :
  $ slcreator
  QPainter::begin: Cannot paint null pixmap
  QPainter::setPen: Will be reset by begin()
  Fatal signal: Segmentation Fault (SDL Parachute Deployed)

The requirements (gambas* packages) are all installed and I even try with additional SDL stuff.
I found a few forums on the web with same things but no answer :( 

Any idea ?
Tx
Tom

---

### Post by Smika on 2006-04-13
I have the same problems. Is there someone with a solution????

---

### Post by TomG on 2006-04-13
I finally solved it by removing current gambas version (the one from repository, 1.0.3 if I remember) and by downloading and installing the latest stable gambas version (1.0.15).
Hope this helps.

---

### Post by Smika on 2006-04-13
Thanks for your reaction. This is very helpful.

---

### Post by TomG on 2006-04-13
Enjoy now :)

---

