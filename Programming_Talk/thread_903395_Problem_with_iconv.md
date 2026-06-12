---
title: "Problem with iconv"
date: 2008-08-28
forum: Programming Talk
---

### Post by mrsheep on 2008-08-28
Hi, I'm trying to do some format conversions using iconv to deal with
international characters:
echo 'españa' | iconv -f 'utf-8' -t 'ascii//translit//IGNORE'
This works fine on my machine (Ubuntu 7.10, iconv glibc 2.6.1)
returning "espana".
However when I try it on a different machine (Ubuntu 6.06.2, iconv
glibc 2.3.6) the same command returns 'espa?a'.
I wonder if this could be related with the locales installed on the
machine or could be fixed by upgrading glibc. I would appreciate any
help.

---

