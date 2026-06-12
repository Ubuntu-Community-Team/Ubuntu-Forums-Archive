---
title: "Easy reading/writing XML files"
date: 2008-11-30
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-30
It's C, as always. :)

I want an easy-to use, noob proof XML parser for C.

I tried libxml2 but it said:
[quote="Gnome Terminal"]
error: libxml/encoding.h: No such file or directory
error: libxml/xmlwriter.h: No such file or directory
[/quote]

---

### Post by nvteighen on 2008-11-30
Try using the **-I/usr/include/libxml2** flag (caution: uppercase i, not lowercase l) when compiling.

---

### Post by crazyfuturamanoob on 2008-11-30
I just found this from libxml2 home site:
> gcc -o example `xml2-config --cflags` example.c `xml2-config --libs`
I tried it and it works.

---

### Post by nvteighen on 2008-11-30
Well, that's just a way to automatically do what I told you :)

---

