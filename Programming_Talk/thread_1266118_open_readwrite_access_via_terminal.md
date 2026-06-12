---
title: "open read/write access via terminal"
date: 2009-09-14
forum: Programming Talk
---

### Post by aytacd on 2009-09-14
Hi,

I've been trying to give read/write access to all users for a certain folder via terminal. Is there a function or a script that I can use?

Thank you for your help...

---

### Post by DaithiF on 2009-09-14
```
chmod -R a+rw folder
```
-R for recursive (assumes you want to read-write permissions to cascade down to any subdirectories)

---

### Post by realzippy on 2009-09-14
..have a look:

[http://ubuntuforums.org/archive/index.php/t-969822.html](http://ubuntuforums.org/archive/index.php/t-969822.html)

---

### Post by aytacd on 2009-09-14
[FONT=monospace]thank you so much.. :)))
[/FONT]

---

