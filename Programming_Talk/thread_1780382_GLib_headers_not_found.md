---
title: "GLib headers not found"
date: 2011-06-11
forum: Programming Talk
---

### Post by carlos21 on 2011-06-11
I am a bit new to Ubuntu still and didin't know where else to post my problem.

So I've been trying to build my project in Qt that uses GLib and everytime I try and build it I get the error:

/usr/include/glib-2.0/glib.h:32: error: glib/galloca.h: No such file or directory

The problem is that I have all the dev files installed but for some reason it isn't finding them. I know I got them in the directory /glib-2.0/ but for some reason it tells me to specify /glib-2.0/glib/headerfile.h/ in the actual glib.h file. I can't change them because it requires permissions and anyways all the files would do the same thing.

How do I specify the path the compiler needs to look in for the header files? I know this is probably basic but I could use the help ;)

---

### Post by NovaAesa on 2011-06-11
Try something like this:

```

#include <glib.h>

int main()
{
	return 0;
}

```

Compile with:
```

gcc glibtest.c `pkg-config --cflags --libs glib-2.0`

```

---

### Post by carlos21 on 2011-06-12
Thanks but for some reason Qt still can't recognise the path.

Meh it's been solved now, I figured it out. Apparently just edit a bit of the code of the actual headers and it automatically recognises it.

---

### Post by NovaAesa on 2011-06-13
Cool, I'm glad you got it sorted out :)

---

