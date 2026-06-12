---
title: "Glib and valgrind, popular kind of question still stumble me"
date: 2009-02-18
forum: Programming Talk
---

### Post by mhexyl on 2009-02-18
Following the guide, I tied G_SLICE=always-malloc and G_DEBUG=gc-friendly to turn off glib's optimizations and used a supprsion file got from [http://live.gnome.org/Valgrind](http://live.gnome.org/Valgrind), but until I installed libglib-2.0-dbg package from synaptic there still ware possibly lost reports for the simplest glib applecation shown later.

 1. Have any trick I missed to avoid those false warnings caused by glib? Is the supprsion file provied by [http://live.gnome.org/Valgrind](http://live.gnome.org/Valgrind) outdate(The version of glib i use is 2.16.6)?
 2. What has happened, when lib glib-2.0-dbg installed, so that these possibly lost repots disappeared?

The source code I have used for the test.
```
#include <gio/gio.h>
#include <stdio.h>

int main()
{
     g_type_init();
     return 0;
}
```

Command line I used to run valgrind.
```
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind --tool=memcheck --leak-check=full --leak-resolution=high --num-callers=20 ./test
```

Segment of the log.
 1. libglib-2.0-dbg was uninstalled

```
==6774== LEAK SUMMARY:
==6774==    definitely lost: 0 bytes in 0 blocks.
==6774==      possibly lost: 800 bytes in 20 blocks.
==6774==    still reachable: 12,068 bytes in 289 blocks.
==6774==         suppressed: 0 bytes in 0 blocks.

```
 2. libglib-2.0-dbg was installed

```
==6610== LEAK SUMMARY:
==6610==    definitely lost: 0 bytes in 0 blocks.
==6610==      possibly lost: 0 bytes in 0 blocks.
==6610==    still reachable: 11,068 bytes in 264 blocks.
==6610==         suppressed: 1,800 bytes in 45 blocks.
```

---

