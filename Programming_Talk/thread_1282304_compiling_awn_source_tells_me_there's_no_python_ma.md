---
title: "compiling awn source tells me there's no python main lib?"
date: 2009-10-04
forum: Programming Talk
---

### Post by artheus on 2009-10-04
I've been trying to compile the source-code of the avant-window-navigator that is being developed now.. But when I try to use the ./configure that prepare the files for "make" it stops, when it's checking the python main library.

Output:
```
checking for the distutils Python package... yes
checking for Python include path... -I/usr/include/python2.6
checking for Python library path... -L/usr/lib -lpython2.6
checking python extra libraries... -L/usr/lib -lz -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic -Wl,-O1 -Wl,-Bsymbolic-functions
checking consistency of all components of python development environment... no
configure: error: in `/home/artheus/Desktop/avn-src':
configure: error:
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================

```

I am newb at compiling and developing in Linux, so if there is a really simple solution to this, please take it easy on me ^^

Cheers,
Artheus

---

### Post by unutbu on 2009-10-04
> **artheus said:**
> ```

  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================

```


Try installing the python2.6-dev package.

---

### Post by artheus on 2009-10-04
ah... Thank's a lot!

*awkward*

---

### Post by spiralciric on 2010-05-11
I installed python2.6-dev, but that did not help. I also get this error message.

---

### Post by artheus on 2012-08-15
Just to clarify. Installing python-dev solved this for me.

---

