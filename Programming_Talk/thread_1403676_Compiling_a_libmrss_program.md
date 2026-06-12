---
title: "Compiling a libmrss program"
date: 2010-02-10
forum: Programming Talk
---

### Post by matmatmat on 2010-02-10
I am trying to compile a program that includes [libmrss]("http://www.autistici.org/bakunin/libmrss/doc/").When I try to compile:
```

[matio@myhost clutterC]$ gcc rssReader.c -o rssReader `pkg-config clutter-1.0 --cflags --libs`
In file included from rssReader.c:3:
/usr/local/include/mrss.h:23:27: error: libxml/parser.h: No such file or directory


[matio@myhost clutterC]$ gcc rssReader.c -o rssReader `pkg-config clutter-1.0 --cflags --libs` `pkg-config libmrss --cflags --libs`
Package libmrss was not found in the pkg-config search path.
Perhaps you should add the directory containing `libmrss.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libmrss' found
In file included from rssReader.c:3:
/usr/local/include/mrss.h:23:27: error: libxml/parser.h: No such file or directory

```

How can I add the library?

---

