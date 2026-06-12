---
title: "how to compile the sorcecode of the offical ls.c source code ?"
date: 2017-11-13
forum: New to Ubuntu
---

### Post by goodlookingnerd on 2017-11-13
Hey guys, 
this is the offical ls.c code :
[http://git.savannah.gnu.org/cgit/coreutils.git/plain/src/ls.c](http://git.savannah.gnu.org/cgit/coreutils.git/plain/src/ls.c)

i downloaded it and i tried to compile this source code with gcc.
The problem was that the gcc showed me a lot of errors.


```

$ gcc ls.c -o ls
ls.c:38:20: fatal error: config.h: 
```

i did fix a lot of those errors by searching with the find command into my dictonarys

```
$ find /usr/src/ -name "nameofthelibary" 2> /dev/null 
```

for some libarys i found the correct path, so for example i could place them into the #include <config.h> => #include </usr/src/linuxheader.../config.h>
as i mentioned this method worked for some libarys but not for the header for example #include "die.h"


so my question is now: is there any way to compile this ls.c ? cz i want to learn how it works by modifying it :)

sry for the bad english btw :)

---

### Post by Impavidus on 2017-11-13
You can tell gcc in which directories to look for those header files (use the -I (capital i) option), but the default location for header files (/usr/include) is used automatically, so you don't have to add that. Whenever the source code says```
#include <foo.h>
```gcc will search the include directories for foo.h. To make sure you have foo.h, the header file for libfoo, installed on your system, you have to install the development version of libfoo:```
sudo apt install libfoo-dev
```Whenever the source code says```
#include "bar.h"
```gcc will search for bar.h in the same directory as the source code.

---

