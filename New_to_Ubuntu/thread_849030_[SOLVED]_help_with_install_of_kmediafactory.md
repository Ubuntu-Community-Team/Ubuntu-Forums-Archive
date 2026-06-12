---
title: "[SOLVED] help with install of kmediafactory"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-07-04
I want to use a GUI for ffmpeg but kmediafactory is having some problems when I try and configure it so I can install it.
Here's the error message I get
```
checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```
and the end of the config.log ...
```
#define HAVE_RES_INIT_PROTO 1
#define SIZEOF_INT 4
#define SIZEOF_SHORT 2
#define SIZEOF_LONG 4
#define SIZEOF_CHAR_P 4
#define SIZEOF_SIZE_T 4
#define SIZEOF_UNSIGNED_LONG 4
#define HAVE_VSNPRINTF 1
#define HAVE_SNPRINTF 1
#define HAVE_LIBZ 1
#define HAVE_LIBPNG 1
#define HAVE_LIBJPEG 1
#define HAVE_LIBPTHREAD 1

configure: exit 1
```
yeah not incredibly helpful
anyway, if anyone knows how to correct this that would be greatly appreciated.

---

### Post by bumanie on 2008-07-04
It's in the repositories>  sudo apt-get install kmediafactory

---

### Post by fontenot_1031 on 2008-07-04
> **bumanie said:**
> It's in the repositories

woah uhh made that harder than it needed to be
thanks man

---

