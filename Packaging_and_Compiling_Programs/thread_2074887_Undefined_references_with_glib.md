---
title: "Undefined references with glib"
date: 2012-10-22
forum: Packaging and Compiling Programs
---

### Post by ShadowDragon on 2012-10-22
I'm trying to compile some code against glib-2.0 (it's even some code I have written about a year ago), but for each method I use from glib, I get an undefined reference error during compiling / linking...

Even this basic example:
```
#include <glib.h>
int main(int argc, char * argv[]) {
	if(glib_check_version(2,32,0) == NULL) {
		return 0;
	} else {
		return 1;
	}
}
```

Doesn't want to compile.
```
$ gcc `pkg-config --cflags --libs glib-2.0` main.c
/tmp/ccEso0kl.o: In function `main':
main.c:(.text+0x1f): undefined reference to `glib_check_version'
collect2: ld returned 1 exit status
```

And as far as I can see, glib-2.0 is installed:
```
$ pkg-config --cflags --libs glib-2.0 
-I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include  -lglib-2.0
```

```
$ aptitude show libglib2.0-dev 
Package: libglib2.0-dev                  
State: installed
Automatically installed: no
Version: 2.32.3-0ubuntu1
Priority: optional
Section: libdevel
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 8,646 k
...
```

```
$ cat /usr/include/glib-2.0/glib/gversion.h | grep -C 2 glib_check_version
GLIB_VAR const guint glib_binary_age;

const gchar * glib_check_version (guint required_major,
                                  guint required_minor,
                                  guint required_micro);
```

Anyone an idea why I can't compile against glib-2.0? Probably something obvious, but I can't seem to find it. :)

---

### Post by MadCow108 on 2012-10-23
libraries need to go after the objects on the compile command line

```
gcc `pkg-config --cflags glib-2.0` main.c `pkg-config --libs glib-2.0`
```

---

### Post by ShadowDragon on 2012-10-23
Ah, look at that. Exactly the answer I needed.
Thank you very much!

---

