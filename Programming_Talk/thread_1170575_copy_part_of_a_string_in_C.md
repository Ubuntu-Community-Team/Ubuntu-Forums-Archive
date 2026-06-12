---
title: "copy part of a string in C"
date: 2009-05-26
forum: Programming Talk
---

### Post by J05HYYY on 2009-05-26
hello, i am writing a program to read file extensions in C
here's my problem:

say if i had a file called "hello.dat" and i already know the length of the string (9), i already know the position of the "." (6) and i know how many characters i want to read (9-6=3).

what i don't know is how to put the characters "dat" into a new variable.

any help, much appreciated.

---

### Post by monkeyking on 2009-05-26
I would use strncpy
[http://www.cplusplus.com/reference/clibrary/cstring/strncpy/](http://www.cplusplus.com/reference/clibrary/cstring/strncpy/)

---

### Post by crdlb on 2009-05-26
For this specific scenario, you could simply use ```
char *ext = name + 6;
``` avoiding any allocation, but this only works because you want the end of the string. If you want it allocated, you can wrap it in something like strdup. 

If you wanted a more general solution and could not mutate the string (to add a \0 in the right place), you would have to use strndup, which is a GNU extension, or malloc + strncpy (yuck) for portibility.

Keep in mind, however, that GLib has portable and safe g_ versions of all these functions, and many more that might be useful, e.g. g_strsplit.

---

### Post by J05HYYY on 2009-05-26
i managed to do it using strncpy ... was difficult and took some time to work out how, but its all good now.

cheers

---

