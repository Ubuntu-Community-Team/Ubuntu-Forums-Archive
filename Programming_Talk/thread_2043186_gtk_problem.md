---
title: "gtk problem"
date: 2012-08-16
forum: Programming Talk
---

### Post by andy007007007 on 2012-08-16
I am new to gtk gui programming.i install gtk from update  manager.
when i compiled codes GTK+ [hello-world]("http://en.wikipedia.org/wiki/Hello_world_program") program 
#include <gtk/gtk.h> int main (int argc, char *argv[]) {
}

$ gcc -Wall helloworld.c -o helloworld $(pkg-config --cflags --libs gtk+-3.0)
I got an error that
Package gtk+-3.0 was not found in the pkg-config search path.
And i can't find package gtk3 in package manager

---

### Post by DarkAmbient on 2012-08-16
In a terminal, try this:

```
sudo apt-get install libgtk-3-0
```

Might do the trick, no guarantees.

---

### Post by ofnuts on 2012-08-16
Old Ubuntu releases (at least up to 10.04 Lucid) don't support GTK3. Installing GTK3 on these may be an uphill battle, and it may be easier to migrate to a more recent version of Ubuntu

---

### Post by SledgeHammer_999 on 2012-08-16
> **andy007007007 said:**
> I am new to gtk gui programming.i install gtk from update  manager.
when i compiled codes GTK+ [hello-world]("http://en.wikipedia.org/wiki/Hello_world_program") program 
#include <gtk/gtk.h> int main (int argc, char *argv[]) {
}

$ gcc -Wall helloworld.c -o helloworld $(pkg-config --cflags --libs gtk+-3.0)
I got an error that
Package gtk+-3.0 was not found in the pkg-config search path.
And i can't find package gtk3 in package manager

I think you installed the gtk+-2.0 version. Just compile with this:
```
gcc -Wall helloworld.c -o helloworld $(pkg-config --cflags --libs gtk+-2.0)
```

---

