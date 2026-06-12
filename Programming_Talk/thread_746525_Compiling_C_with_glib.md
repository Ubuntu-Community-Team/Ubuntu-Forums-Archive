---
title: "Compiling C with glib"
date: 2008-04-05
forum: Programming Talk
---

### Post by mike_g on 2008-04-05
I just installed GTK+ development libs using:
```
sudo aptitude install gnome-core-devel build-essential
```
Now I try and compile a simple file includeing glib:
```
#include <glib-2.0/glib.h>
int main()
{
	return 0;
}
```
When I compile gcc gives me errors that it cannot find any of the header files included by glib.h. So i had a peek inside glib.h, but it seems as if it should be including the files correctly. IE: #include <glib/someinclude.h>

I'm guessing that I have to link glib somehow. I compiled like:
```
gcc test.c -Wall
```
I tried adding: -lglib, lglib-2.0, and lglib2.0. None of these seemed to work. Anyone know what I should be doing here?

---

### Post by mike_g on 2008-04-05
Ok, I guess it will work if I compile as:
```
gcc test.c `pkg-config gtk+-2.0 --cflags --libs`
```
Sorry about that.

---

