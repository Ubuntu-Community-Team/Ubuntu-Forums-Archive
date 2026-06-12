---
title: "Error locating gdu headers"
date: 2010-08-10
forum: Packaging and Compiling Programs
---

### Post by trevorsv on 2010-08-10
I have just started writing my first "proper" C application and want to use libgdu (the gnome-disk-utility lib). My code looks like:

```
#include <stdio.h>
#define GDU_API_IS_SUBJECT_TO_CHANGE
#include <gnome-disk-utility/gdu/gdu.h>

int main( int argc, *char[] )
{
    GduPool *pool;
    GduList *dev;

    pool = gdu_pool_new();
    dev = gdu_pool_get_devices( pool );

    g_list_foreach( dev, (GFunc)g_print, NULL );

    g_object_unref( pool );
    g_list_free( dev );

    return 0;
}

```

When I run ```
gcc -Wall -std=c99 `pkg-config gdu --lib` -o main main.c
```

I get the following mess of an output:

```
In file included from main.c:3:
/usr/include/gnome-disk-utility/gdu/gdu.h:31:27: error: gdu/gdu-types.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:32:36: error: gdu/gdu-linux-md-drive.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:33:45: error: gdu/gdu-linux-lvm2-volume-group.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:34:39: error: gdu/gdu-linux-lvm2-volume.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:35:44: error: gdu/gdu-linux-lvm2-volume-hole.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:36:28: error: gdu/gdu-device.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:37:29: error: gdu/gdu-adapter.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:38:30: error: gdu/gdu-expander.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:39:26: error: gdu/gdu-port.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:40:27: error: gdu/gdu-drive.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:41:27: error: gdu/gdu-error.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:42:38: error: gdu/gdu-known-filesystem.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:43:26: error: gdu/gdu-pool.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:44:33: error: gdu/gdu-presentable.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:45:29: error: gdu/gdu-process.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:46:26: error: gdu/gdu-util.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:47:28: error: gdu/gdu-volume.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:48:33: error: gdu/gdu-volume-hole.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:49:25: error: gdu/gdu-hub.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:50:29: error: gdu/gdu-machine.h: No such file or directory
/usr/include/gnome-disk-utility/gdu/gdu.h:51:31: error: gdu/gdu-callbacks.h: No such file or directory
main.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
make: *** [main.o] Error 1
```

I thought it looked odd that it's installed in gnome-disk-utility/gdu/gdu.h rather than simply gdu/gdu.h but maybe that's fine.

What am I doing wrong here?

---

### Post by SevenMachines on 2010-08-10
The pkg-config call is wrong. ie,
> $ pkg-config gdu --lib

--lib: unknown option
you want the --cflags and --libs options, 
> $ pkg-config gdu --cflags --libs

-pthread -I/usr/include/gnome-disk-utility -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lgdu -lgio-2.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  


---

### Post by SevenMachines on 2010-08-10
just on a quick look, a few things also.

*main function should be something like,
int main (int argc, char *argv[])

* GList not GduList, see [http://library.gnome.org/devel/gnome-disk-utility/stable/GduPool.html](http://library.gnome.org/devel/gnome-disk-utility/stable/GduPool.html)

* You'll probably need to call g_type_init(); before using GList(?) I dont know much about that though

---

### Post by trevorsv on 2010-08-10
Thanks, the --lib was a typo in the post but --cflags sorted it. Just noticed how many stupid mistakes there were in the C, too. Whoops...

---

### Post by SevenMachines on 2010-08-10
> **trevorsv said:**
> Just noticed how many stupid mistakes there were in the C, too. Whoops...
I find I program stupid mistakes into everything I do, thankfully the compiler likes to point them all out to me :)

---

