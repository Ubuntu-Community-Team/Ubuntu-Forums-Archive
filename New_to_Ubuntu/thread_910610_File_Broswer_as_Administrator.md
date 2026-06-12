---
title: "File Broswer as Administrator"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Yanced on 2008-09-04
How do I run File Browser as administrator?  I remember some wierd command using te teminal, but is there an easier way?

---

### Post by Dr Small on 2008-09-04
You can press ALT + F2 and then type:
```
gksudo nautilus
```

---

### Post by HunterA3 on 2008-09-04
you can cd to the directories you're looking for and ls to see the files if you're browsing from the command line.

If you're not that familiar with the command line and would rather have a GUI to look at, you can load up nautilus as the superuser and browse to your files that way. It's probably not the best way to do it, but it does work. I would suggest using the command line as the superuser though. Get familiar with the console and it will help you become familiar with linux commands faster.

---

### Post by MasterSander on 2008-09-04
You can make a script for nautilus that you can access through right clicking and that enables sudo nautilus.

---

### Post by lazyart on 2008-09-04
Just be careful.  A root nautilus can look just like any other terminal and it's ridiculously easy to move files around and screw up permissions.

---

