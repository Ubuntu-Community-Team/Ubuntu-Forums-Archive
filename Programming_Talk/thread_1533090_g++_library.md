---
title: "g++ library"
date: 2010-07-17
forum: Programming Talk
---

### Post by bigrockcrasher on 2010-07-17
I am writing some .h files. it has come to the point that i would like to have them in one spot so that I can call them when ever i want. is there a place in the Ubuntu system where i can put my .h files in and treat them like iostream or cmath libraries.

---

### Post by pbrane on 2010-07-17
*/usr/include* is a good place. Usually you'll want to create your own directory in */usr/include*, i.e. */usr/include/myincludes*. But that's not required.
Then you include them in source files
```

#include <myincludes/something.h>

```

---

### Post by bigrockcrasher on 2010-07-17
that sounds cool. thank you

---

### Post by bigrockcrasher on 2010-07-17
Do I just put my .h files there. what do I do with the complimentary files.

---

### Post by dwhitney67 on 2010-07-17
Do NOT put your header files in /usr/include; put them in /usr/local/include.  That is why this directory exists.

As for your other question, your .cpp files should be bundled together into a library, which can either be a shared-object type and/or a static type.  This should be placed in /usr/local/lib.

The most basic of commands to build a shared-object and a static library are:
```

# Form object files from source files
#
g++ -Wall -fPIC -c One.cpp
g++ -Wall -fPIC -c Two.cpp
g++ -Wall -fPIC -c Etc.cpp

# For shared-object library
#
g++ -shared -o libMyStuff.so One.o Two.o Etc.o

# For static library
#
ar -r libMyStuff.a One.o Two.o Etc.o

```

Use /usr/bin/install, as root (ie. sudo) to install your header file(s) to /usr/local/include:
```

sudo mkdir -p /usr/local/include/mystuff
sudo install -m 644 *.h /usr/local/include/mystuff

```
Similarly for the shared-object and static library files:
```

sudo install -m 644 libMyStuff.a /usr/local/lib
sudo install -m 755 libMyStuff.so /usr/local/lib

```

---

