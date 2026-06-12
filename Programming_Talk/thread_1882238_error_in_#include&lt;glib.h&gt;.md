---
title: "error in #include&lt;glib.h&gt;"
date: 2011-11-17
forum: Programming Talk
---

### Post by avee137 on 2011-11-17
hi,

I need to use glib.h for my program. When i compile a sample code like this.
```

#include<glib.h>
#include<dbus/dbus-glib.h>


int main(){

return 0;
}

```

I get following error :

```

sccc@ubuntu:~/poc/dbus/glibSend$ gcc demo.c -o demo
demo.c:1:17: fatal error: glib.h: No such file or directory
compilation terminated.

```

Any clue about how to proceed ?? 

Any relevant help would be greatly appreciated.

---

### Post by crdlb on 2011-11-17
You need to use pkg-config to provide the compile and link flags:```
gcc -o demo $(pkg-config --cflags glib-2.0 dbus-glib-1) demo.c $(pkg-config --libs glib-2.0 dbus-glib-1)
``` 

When compiling and linking separately, use --cflags for the compile stage and --libs for the link stage.

---

### Post by avee137 on 2011-11-17
> **crdlb said:**
> You need to use pkg-config to provide the compile and link flags:```
gcc -o demo $(pkg-config --cflags glib-2.0 dbus-glib-1) demo.c $(pkg-config --libs glib-2.0 dbus-glib-1)
``` 

When compiling and linking separately, use --cflags for the compile stage and --libs for the link stage.

thanks, it worked.

---

