---
title: "Won't let me set correct time"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by goldengreeke on 2008-09-11
Tried everything and still shows date two days in advance. Otherwise, every thing else works fine, browser, media player, fast loading of web pages, etc.

---

### Post by gvartser on 2008-09-11
This is one way of doing it: (from a terminal/shell)

1) open a terminal/shell
2) Set the new date: (You need to do this as an privileged user "root", thats why using "sudo")
   ```
sudo date -s "11 SEP 2008 13:00:00"
```
3) Done.

Best regz,
/g

---

