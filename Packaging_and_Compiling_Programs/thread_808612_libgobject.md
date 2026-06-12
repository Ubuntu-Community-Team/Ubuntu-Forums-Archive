---
title: "libgobject?"
date: 2008-05-26
forum: Packaging and Compiling Programs
---

### Post by virgil_disgr4ce on 2008-05-26
Hi all!  Not (very) new to linux but new to compiling.  I'm trying to recompile mpdscribble with a minor fix but I'm getting the following error:

checking for libgobject... configure: error: libgobject-2.0 not found

I can mlocate the following:

/usr/lib/libgobject-2.0.so.0
/usr/lib/libgobject-2.0.so.0.1600.3

But beyond that I'm a bit lost. I've tried to research this diligently as I always do but haven't found any information about this.  It's been a long time since I compiled C, and I've never done it on linux :)  Thanks in advance!!

--Ted

---

### Post by Compyx on 2008-05-28
You need to install the headers for libgobject, this will probably do:
```

sudo apt-get install libglib2.0-dev

```

But since you may need headers for other libraries as well, you might as well do:
```

sudo apt-get build-dep mpdscribble

```
Which will try and pull in all packages needed to compile mpdscribble from source.

---

