---
title: "help installing libgnomeui.so.32"
date: 2009-02-10
forum: Programming Talk
---

### Post by superlambchops on 2009-02-10
I am getting the error "**error while loading shared libraries: libgnomeui.so.32: cannot open shared object file: No such file or directory**" on an installation of 64bit Intrepid. The program that causes the error will execute on a 32bit installation of Intrepid.

> **leibowitz said:**
> What do you get when trying the following command.

```
locate libgnomeui.so.32
```


On my system, the file is located at **/usr/lib/libgnomeui.so.32**

If you don't have this file, then you need  to install the package **libgnomeui32**

To install it, use the following command.

```
sudo apt-get install libgnomeui32
```

locate returns nothing even though **libgnomeui32** has been installed and the file **/usr/lib/libgnomeui.so.32** exists

---

### Post by dmizer on 2009-02-10
Moved this to it's own thread. It's preferable to start your own thread rather than reviving someone else's two year old thread. :)

---

