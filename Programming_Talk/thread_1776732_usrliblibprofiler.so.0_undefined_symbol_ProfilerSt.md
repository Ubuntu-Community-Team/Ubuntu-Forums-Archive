---
title: "/usr/lib/libprofiler.so.0: undefined symbol: ProfilerStart"
date: 2011-06-06
forum: Programming Talk
---

### Post by simeon87 on 2011-06-06
I'm trying to use [google-perftools](http://code.google.com/p/google-perftools/) to profile a C extension of a Python program. For some reason I keep getting this error so I can't use the ProfilerStart and ProfilerStop functions to profile the code.

I suspect it has to do with my 64 bits system and the way it's compiled. I installed with ./configure, make, sudo make install.

Here's what I know:

- I have a 64 bits AMD CPU.
- /usr/lib/libprofiler.so.0 indeed exists
- I try to run it from Python using:

```
import ctypes.util
google_profiler = ctypes.util.find_library('profiler')
libprofiler = ctypes.CDLL(google_profiler)
# libprofiler is not None at this point and it points to libprofiler.so.0
status = libprofiler.ProfilerStart("test.prof")
```

- I have also tried compiling and linking the C extension with -lprofiler but still the same. What could it be?

---

### Post by simeon87 on 2011-06-07
Bump.

---

