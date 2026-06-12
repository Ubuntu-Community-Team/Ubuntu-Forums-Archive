---
title: "Start subprocess from python, and keep going while subprocess is working?"
date: 2008-12-25
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-25
subprocess.call() opens a subprocess but waits until subprocess is done.
I don't want that. I want the program to continue execution after subprocess is started.

And I would like to make the processes communicating, the first process sending data to the second and vice versa.

---

### Post by slavik on 2008-12-25
you need to fork->exec ... search this forum, I wrote the basics about it a while ago.

---

### Post by imdano on 2008-12-25
Check out subprocess.Popen, that's capable of exactly what you want.

---

