---
title: "Eclipse c++"
date: 2014-10-14
forum: Programming Talk
---

### Post by kielyk on 2014-10-14
Every time I try to build Hello World I'm getting these errors. Building target: HelloWorldInvoking: Cross G++ Linker
g++  -o "HelloWorld"  ./src/HelloWorld.o   -lgl -lglu -lglut
/usr/bin/ld: cannot find -lgl
/usr/bin/ld: cannot find -lglu
collect2: error: ld returned 1 exit status
make: *** [HelloWorld] Error 1

Any help would be really appreciated.
Thanks.

---

### Post by sandyd on 2014-10-14
> **kielyk said:**
> Every time I try to build Hello World I'm getting these errors. Building target: HelloWorldInvoking: Cross G++ Linker
g++  -o "HelloWorld"  ./src/HelloWorld.o   -lgl -lglu -lglut
/usr/bin/ld: cannot find -lgl
/usr/bin/ld: cannot find -lglu
collect2: error: ld returned 1 exit status
make: *** [HelloWorld] Error 1

Any help would be really appreciated.
Thanks.
You are missing the libgl and libglu development libraries

Running
```

sudo apt-get install libgl-dev libglu-dev

```
should install them.

---

### Post by kielyk on 2014-10-14
Thank's for the reply but unfortunately that's not the problem.
Here's the output.
libglu1-mesa-dev is already the newest version.
libgl1-mesa-dev is already the newest version.

---

### Post by sandyd on 2014-10-17
> **kielyk said:**
> Thank's for the reply but unfortunately that's not the problem.
Here's the output.
libglu1-mesa-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
Whats the output of
```

ls /usr/lib/libGL.so
```

---

### Post by spjackson on 2014-10-17
> **kielyk said:**
> 
g++  -o "HelloWorld"  ./src/HelloWorld.o   -lgl -lglu -lglut

I think that should be
```

g++ -o "HelloWorld" ./src/HelloWorld.o -lGL -lGLU -lglut

```

---

### Post by slickymaster on 2014-10-17
*Moved to the ***Programming Talk*** sub-forum*

---

