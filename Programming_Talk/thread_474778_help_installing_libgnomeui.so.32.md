---
title: "help installing libgnomeui.so.32"
date: 2007-06-15
forum: Programming Talk
---

### Post by haftan on 2007-06-15
I get the following when I compile some old code:

 error while loading shared libraries: libgnomeui.so.32: cannot open shared object file: No such file or directory

Do I / can I install this library?

---

### Post by leibowitz on 2007-06-15
What do you get when trying the following command.

```
locate libgnomeui.so.32
```


On my system, the file is located at **/usr/lib/libgnomeui.so.32**

If you don't have this file, then you need  to install the package **libgnomeui32**

To install it, use the following command.

```
sudo apt-get install libgnomeui32
```

---

