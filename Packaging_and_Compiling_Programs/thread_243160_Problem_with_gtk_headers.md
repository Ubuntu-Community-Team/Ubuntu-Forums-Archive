---
title: "Problem with gtk headers"
date: 2006-08-24
forum: Packaging and Compiling Programs
---

### Post by arnaldo on 2006-08-24
On a fully updated Dapper, I have tried to compile a couple of gtk enabled programs:
gnash (both cvs and 0.7.1) and gtubeclock (which I had successfuly compiled in July/2005, on a then current Ubuntu).  In all cases, after successfully running configure (had to install several auxiliary packages, all of them ubuntu debs), a lot of messages of this sort appeared during compilation:

/usr/include/gtk-2.0/gtk/gtkobject.h:210: error: expected initializer before 'G_GNUC_NULL_TERMINATED'
/usr/include/gtk-2.0/gtk/gtkwidget.h:447: error: expected initializer before 'G_GNUC_NULL_TERMINATED'

Any hints?

---

### Post by mlind on 2006-08-25
Do you have **libglib2.0-dev** package installed ?

---

### Post by arnaldo on 2006-08-25
Yes,
libglib2.0-dev is already the newest version.

By the way, I tested the same on another slightly differently configured system and got those same error messages.

---

### Post by mlind on 2006-08-25
> **arnaldo said:**
> Yes,
libglib2.0-dev is already the newest version.

By the way, I tested the same on another slightly differently configured system and got those same error messages.

You should post the full log where the errors begin. You are missing some development libraryn needed for compiling the package.

---

### Post by arnaldo on 2006-08-25
If you say so; I thought configure would detect such a problem.
Anyway, I have package a compilation log plus some additional info I believe can help the diagnostics and put it on
[http://kofer.kicks-***.org/bad-gtk.tgz]("http://kofer.kicks-***.org/bad-gtk.tgz")

Thanks for minding this problem.

---

### Post by arnaldo on 2006-08-25
Oh-oh, I noticed that the forum software has bowdlerized my domain name.  I am pretty sure you can gess the missing word, but here is an alternative URL:
[URL="http://kofer.ime.usp.br/bad-gtk.tgz"]
[/URL]
Take care.

---

### Post by arnaldo on 2006-08-25
I am starting to feel silly, now.  Trying the alternative URL again:

[http://kofer.ime.usp.br/bad-gtk.tgz]("http://kofer.ime.usp.br/bad-gtk.tgz")

---

### Post by mlind on 2006-08-25
Okay, I tried compiling this in a clean minimal chroot and it went without errors.

Here are the packages (+dependencies) you need to install
```

sudo aptitude install pkg-config libgnomeui-dev

```

You'll need **build-essential** package too.

Then configure --prefix=$HOME, make and make install or similar.

---

### Post by arnaldo on 2006-08-25
Sorry, but it does not work.  All three packages were already installed and current.

---

### Post by mlind on 2006-08-26
> **arnaldo said:**
> Sorry, but it does not work.  All three packages were already installed and current.

I dunno what's wrong.. Try reinstalling the dependencies or configuring clean source tree.

---

