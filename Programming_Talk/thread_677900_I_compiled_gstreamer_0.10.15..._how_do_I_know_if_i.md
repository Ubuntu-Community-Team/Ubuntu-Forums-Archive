---
title: "I compiled gstreamer 0.10.15... how do I know if it worked..."
date: 2008-01-25
forum: Programming Talk
---

### Post by joesmith1234 on 2008-01-25
I can still compile with the old version... a la:
```

gcc -Wall $(pkg-config --cflags --libs gstreamer-0.10) helloworld.c -o helloworld

```

But if I change it to -0.10.15... I get:
```
 gcc -Wall $(pkg-config --cflags --libs gstreamer-0.10.15) first_init.c -o first_init
Package gstreamer-0.10.15 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gstreamer-0.10.15.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gstreamer-0.10.15' found
gcc: first_init.c: No such file or directory
gcc: no input files
```


How do I know if my gstreamer install worked?

How do I know if I am compiling correctly?
(by the way, I found the compile command randomly on the web)

---

### Post by slavik on 2008-01-26
I am guessing that there is no -dev package installed. :)

---

### Post by po0f on 2008-01-26
joesmith1234,

Compile a binary from a test file as normal, and run `ldd` on it.  The output should list what libraries - and where they are located - the binary uses.

Dunno if gcc checks /usr/local (I'm assuming this is where you installed your custom compiled library?) before /usr, another thing you could check.

---

### Post by bruce89 on 2008-01-27
The pkg-config file isn't gstreamer-0.10.15, it's still gstreamer-0.10.

---

