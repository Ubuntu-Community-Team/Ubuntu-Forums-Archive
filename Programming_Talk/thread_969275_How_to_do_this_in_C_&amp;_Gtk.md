---
title: "How to do this in C &amp; Gtk"
date: 2008-11-03
forum: Programming Talk
---

### Post by cl333r on 2008-11-03
hi folks,
in Java I can pack all my stuff into a single .jar file (including images) and run the program as a single executable file and when needed I can access the images from the .jar file itself.
Is it's possible in C & Gtk using native Linux format? if so please drop a link.

---

### Post by snova on 2008-11-03
There's no easy way to do this. On Windows there is the resource framework, there's something or other built in on Mac OS X, but I know of no comparable Linux alternative.

There are tools that convert files to binary data and include them in the executable, but then it takes a bit more effort to *use* the data.

C is a fairly low level language. Java can afford to provide more functional formats, but JAR files are really just archives...

In Qt at least, there is a program that converts files to source code, which can then be compiled. Then they can be accessed from normal pathnames like ":/resource.png" (note the colon). But I have no idea whether GTK provides anything.

---

### Post by nvteighen on 2008-11-03
What images? Toolbar icons and such? If are those, GTK+ programming usually deals with the so-called "Stock" of images, which is Theme-dependent.

If it's some image or whatever, I doubt you can do something against this. GTK+ is written in C and it's a low-level language as you've been told, so it's very improbable you can get some trivial way to do this.

Have you looked after a library that can do this?

---

### Post by samjh on 2008-11-03
You can make a self-extracting tar.gz file, which can be run as a shell script.

See: [http://megastep.org/makeself/](http://megastep.org/makeself/)

If might be able to modify it to run your executable, instead of just extracting the files.

---

### Post by hessiess on 2008-11-03
you could convert the images into 2d arrays and compile them directly into your application(as is done on the GBA/DS/outher week hardwere) but this makes the binery verry large, and you have to add the extra step of converting the images to your workflow.

---

