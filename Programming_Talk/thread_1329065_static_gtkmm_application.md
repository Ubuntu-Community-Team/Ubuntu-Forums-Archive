---
title: "static gtkmm application"
date: 2009-11-17
forum: Programming Talk
---

### Post by jediborger on 2009-11-17
I am having issues statically compiling/linking a gtk application. It compiles fine dynamically and runs, but when I add the static option it gives me the following error:
```
/usr/bin/ld: cannot find -lgtkmm-2.4
collect2: ld returned 1 exit status

```
Here is the command I am using to compile it:
```
g++ gtk.cpp -o gtk --static `pkg-config --cflags --libs gtkmm-2.4`
```

---

### Post by jediborger on 2009-11-30
bump, anyone know how to do this?

---

