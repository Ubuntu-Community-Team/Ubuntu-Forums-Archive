---
title: "C programming headers"
date: 2012-02-07
forum: Programming Talk
---

### Post by conradin on 2012-02-07
Hi everyone!
I have a question about C headers.
When I have headers that have a slash in them, does that indicate a folder in the /usr/lib folder?
the following headers are missing on my system and Im not sure where to find them. ```
#include <linux/module.h>
#include <linux/config.h>
#include <linux/console_struct.h>
#include <linux/init.h>
```

Im tooling around in the /usr/src files but there are alot of kernel folders there and Im not sure which ones to use, and or where to put the headers if I find them. If I touch a file named linux/config.h, touch reports there is no directory... Should I create a linux directory in /usr/lib?:confused:

---

### Post by schauerlich on 2012-02-07
That means that the program assumes there's a folder somewhere in your include path called "linux" and inside that folder are the files "module.h", "config.h", etc. There are standard places to find them (/usr/include, /usr/share/include, etc), or you can specify it manually from the command line (with gcc, -I/path/to/dir) or with environment variables (C_INCLUDE_PATH). Similarly you will have to provide a path to the compiled code with -L/path/to/lib or setting LIBRARY_PATH.

---

### Post by doobrie on 2012-02-07
If you include a header with <header.h>, then it will look for the header file in your headers path (/usr/include is the most common).

If however, you include with "header.h", then the compiler will look for the file in your current directory for the project (most likely where all your source is).

To get moving forward, you probably need to install the relevant source package for the work you want to do.

---

