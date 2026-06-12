---
title: "Help, firefox 3 wont compile"
date: 2008-07-02
forum: Packaging and Compiling Programs
---

### Post by TheOne...more on 2008-07-02
hi

trying to compile firefox 3 i always get this error;

```

/usr/include/pango-1.0/pango/pangocairo.h:71: error: ‘cairo_font_type_t’ was not declared in this scope
/usr/include/pango-1.0/pango/pangocairo.h:73: error: ‘cairo_font_type_t’ does not name a type
```

i use these commands;

```
./configure --enable-application=suite --enable-system-cairo

make

```
i'm compiling on a 64-bit intel/gutsy machine

thanx

---

