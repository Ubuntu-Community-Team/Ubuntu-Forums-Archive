---
title: "How to debug library?"
date: 2008-10-22
forum: Programming Talk
---

### Post by men28 on 2008-10-22
I am trying to debug library libgtkspell. I have libgtkspell-dev library installed too. I can see this in synaptic.

I use gdb:

```
(gdb) break gtkspell_set_language
Function "gtkspell_set_language" not defined.
Make breakpoint pending on future shared library load? (y or [n]) y

Breakpoint 1 (gtkspell_set_language) pending.
(gdb) run
Starting program: /usr/local/bin/pidgin 
[Thread debugging using libthread_db enabled]
[New Thread 0xb6fea720 (LWP 9734)]
[New Thread 0xb66b7b90 (LWP 9738)]
[Switching to Thread 0xb6fea720 (LWP 9734)]

Breakpoint 1, 0xb7e43e86 in gtkspell_set_language ()
   from /usr/lib/libgtkspell.so.0
(gdb) n
Single stepping until exit from function gtkspell_set_language, 
which has no line number information.
0xb7e41ff7 in ?? () from /usr/lib/libgtkspell.so.0

```

There is no line number information.
I can use a l command of gdb but I can not execute the code step by step. I do not see the code itself.

What's wrong?

---

### Post by dwhitney67 on 2008-10-22
I cannot answer your question specifically, but there are instances when libraries (and this is common) are NOT compiled with symbolic information.  Otherwise, the libraries would require more storage space on your HDD (and if I remember correctly, require you to have the actual source code of the library).

Libraries can, and occasionally do (but rarely), have bugs.  If you feel that you have found one, you should report it to the maintainers of the library.  Trying to debug it is worthy, but hoping to traverse the library code line-by-line may not be achievable in your particular case.

---

### Post by men28 on 2008-10-22
I am interesting in this specific library because I think I can develop some additional functionality for this library and it's simpler to understand how it works throw step by step debugging.
Does libgtkspell-dev have symbolic information? How do I compile the project with -dev libraries? Is there some way?

---

### Post by dwhitney67 on 2008-10-22
> **men28 said:**
> I am interesting in this specific library because I think I can develop some additional functionality for this library and it's simpler to understand how it works throw step by step debugging.
Does libgtkspell-dev have symbolic information? How do I compile the project with -dev libraries? Is there some way?
I do not have any notion/clue about the library you wish to use; I have never used it.

However, if you want to debug it, or any other library, I would suggest that you download the source code, and modify the Makefile to build each module with the "-g" compiler option.  This will include the symbolic information to each module.

---

### Post by boz on 2008-10-22
> **men28 said:**
> I am interesting in this specific library because I think I can develop some additional functionality for this library and it's simpler to understand how it works throw step by step debugging.
Does libgtkspell-dev have symbolic information? How do I compile the project with -dev libraries? Is there some way?

You'd have to get the source for that library, compile it with debug symbols (-g), and make your program link to it.

---

### Post by rnodal on 2008-10-22
Some ubuntu libraries come with an -dbg package but it is not the case for libgtkspell in ubuntu 8.04 so you will have to do what the previous posters have mentioned.

-r

---

### Post by men28 on 2008-10-22
I have downloaded sources of the library. When I try to run a make command this is an output:

```
make: *** No targets specified and no makefile found.  Stop.
```

There are five files in the directory:

```
deprecated.c  gtkspell.c  gtkspell.h  Makefile.am  Makefile.in
```

How to make this library with debugging information?

---

### Post by rnodal on 2008-10-22
you may have to run "./configure" first. Could you try this please?

-r

---

### Post by men28 on 2008-10-22
I had to install some additional -dev package with synaptic and then the configure command was succeed and have created a new Makefile.

---

### Post by men28 on 2008-10-23
When I try to run a make command it didn't create an .so file - the library which I am trying to compile.

How to build an .so file?

---

### Post by dwhitney67 on 2008-10-23
Did the "make" succeed?  If so, what did it produce?

If you are not sure, just post the tail-end of the output from "make".

Also, if you can, attach to your reply the Makefile itself.

---

### Post by men28 on 2008-10-23
Make files (there are two in different directories) are too big and it's impossible to attach them in this forum.

In gtkspell subfolder there are new .lo files and one .la file:

```
deprecated.c   gtkspell.c   gtkspell.o      Makefile.am
deprecated.lo  gtkspell.h   libgtkspell.la  Makefile.in
deprecated.o   gtkspell.lo  Makefile

```

---

### Post by men28 on 2008-10-23
When I run make in this subfolder this is an output:

```
make: Nothing to be done for `all'.
```

---

### Post by dwhitney67 on 2008-10-23
Makes copies of the Makefiles and rename to Makefile1.txt and Makefile2.txt, respectively.  Then attach each of these text files to your reply.

Run the following:
```

make clean
make

```
Capture the output (say the last 10-20 lines) and post that in your reply as well.

---

### Post by men28 on 2008-10-23
When I try to upload the Makefiles I receive next error:

```
 Makefile1.txt:
Your file of 27.0 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.
Makefile2.txt:
Your file of 21.8 KB bytes exceeds the forum's limit of 19.5 KB for this filetype. 
```

Make command in 'gtkspell' subdirectory produces output:
```

/bin/bash ../libtool --tag=CC   --mode=link gcc -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/enchant   -DG_LOG_DOMAIN=\"gtkspell\" -DLOCALEDIR=\""/usr/local/share/locale"\" -g -O2   -o libgtkspell.la -rpath /usr/local/lib gtkspell.lo deprecated.lo -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lenchant -lgmodule-2.0 -ldl -lglib-2.0   -lenchant 
gcc -shared  .libs/gtkspell.o .libs/deprecated.o  /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so /usr/lib/libenchant.so  -Wl,--export-dynamic -Wl,-soname -Wl,libgtkspell.so.0 -o .libs/libgtkspell.so.0.0.0
(cd .libs && rm -f libgtkspell.so.0 && ln -s libgtkspell.so.0.0.0 libgtkspell.so.0)
(cd .libs && rm -f libgtkspell.so && ln -s libgtkspell.so.0.0.0 libgtkspell.so)
ar cru .libs/libgtkspell.a  gtkspell.o deprecated.o
ranlib .libs/libgtkspell.a
creating libgtkspell.la
(cd .libs && rm -f libgtkspell.la && ln -s ../libgtkspell.la libgtkspell.la)

```

And make command in parent directory produces:

```
/bin/bash ../libtool --tag=CC   --mode=link gcc -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/enchant   -I.. -g -O2   -o advanced advanced.o -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lenchant -lgmodule-2.0 -ldl -lglib-2.0   ../gtkspell/libgtkspell.la 
gcc -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/enchant -I.. -g -O2 -o .libs/advanced advanced.o -Wl,--export-dynamic  /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libenchant.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../gtkspell/.libs/libgtkspell.so 
creating advanced
make[2]: Leaving directory `/home/alex/development/gtkspell-2.0.14/examples'
Making all in docs
make[2]: Entering directory `/home/alex/development/gtkspell-2.0.14/docs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/development/gtkspell-2.0.14/docs'
Making all in po
make[2]: Entering directory `/home/alex/development/gtkspell-2.0.14/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/development/gtkspell-2.0.14/po'
make[2]: Entering directory `/home/alex/development/gtkspell-2.0.14'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/alex/development/gtkspell-2.0.14'
make[1]: Leaving directory `/home/alex/development/gtkspell-2.0.14'

```

---

### Post by dwhitney67 on 2008-10-23
It would appear that the shared-library you seek is in:
```
.libs/libgtkspell.so.0.0.0
```
which is relative to the gtkspell directory where you performed the 'make'.

The developers of gtkspell (and whatever else you have) thought they were probably doing you a service by placing the resulting shared library in a hidden folder.  (Not very thoughtful if you ask me).  The resulting shared library probably won't be installed into the root-privileged areas until you run a 'sudo make install', which I do NOT recommend, for this will overwrite your version of the library that was installed via synaptic.

Anyhow, knowing where the shared-library located is sufficient.  When you build your application, just specify the location with the -L option.

For example,
```
gcc -L/home/alex/development/gtkspell-2.0.14/.lib ...
```

It seems odd though, that the library in .lib has a version of 0.0.0, yet the directory where the source code is located has a version number of 2.0.14.  Oh well... I guess the developers of gtkspell had a brain-fart or two.

P.S.  I bet with the information provided above you will still have trouble.  Here's a start on remedying the situation:
```

cd /home/alex/development/gtkspell-2.0.14/.lib
ln -s libgtkspell.so.0.0.0 libgtkspell.so
```

---

### Post by men28 on 2008-10-23
Thank you. I found this hidden folder too. It is quite strange idea to put library files in hidden folder.
Now I have to think how I compile my program where this library is used. It is library too.

---

### Post by men28 on 2008-10-23
A program which I do all this to develop it is a pidgins plugin named 'switchspell'.
I have only one file: switchspell.c 
And I compile it with command: make switchspell.so
It is enough to make plugin for pidgin.

About pidgin plugins it is possible read there:
[http://developer.pidgin.im/wiki/CHowTo/BasicPluginHowto]("http://developer.pidgin.im/wiki/CHowTo/BasicPluginHowto")

And how I compile this with my new library?

---

### Post by dwhitney67 on 2008-10-23
> **men28 said:**
> A program which I do all this to develop it is a pidgins plugin named 'switchspell'.
I have only one file: switchspell.c 
And I compile it with command: make switchspell.so
It is enough to make plugin for pidgin.

About pidgin plugins it is possible read there:
[http://developer.pidgin.im/wiki/CHowTo/BasicPluginHowto]("http://developer.pidgin.im/wiki/CHowTo/BasicPluginHowto")

And how I compile this with my new library?
You are compiling your module (switchspell.c) with a Makefile?  Who wrote the Makefile?

Sorry if the following offends you... but I have gathered that you do not have much experience developing s/w... much less Makefiles.

You are trying to prove something... perhaps that there is a fault in a library (gtkspell or whatever), but you have not demonstrated that your code may be the one at fault.

Please spend more time learning about C (or C++) programming, Makefiles, _and_ GCC before posting again.  I feel that you do not have a clue what you are doing and must have your hand held at every step.

I am not being harsh... ok, I am... but seriously, you need to take a step back to understand the fundamentals of C/C++ programming and linking to libraries before you attempt to "plug-in" to someone's library.

The way this thread is headed, there is no way to solve the problem unless someone were to have all of the s/w that you have on your system.  In other words, you are not asking generic questions, but specific ones.  In such case, it would be hard/impossible for me to help you.

---

### Post by bruce89 on 2008-10-23
Inceidentally, GtkSpell shouldn't be used any more.

---

### Post by dwhitney67 on 2008-10-23
> **bruce89 said:**
> Inceidentally, GtkSpell shouldn't be used any more.
Ok.  Nice follow-thru...  can you elaborate some more so as to help the OP.  Or is this asking too much?

---

### Post by nvteighen on 2008-10-23
> **dwhitney67 said:**
> Ok.  Nice follow-thru...  can you elaborate some more so as to help the OP.  Or is this asking too much?
Usually, that means too much... *sighs*

---

### Post by bruce89 on 2008-10-23
> **dwhitney67 said:**
> Ok.  Nice follow-thru...  can you elaborate some more so as to help the OP.  Or is this asking too much?

I think people now use Enchant directly.

---

### Post by men28 on 2009-02-25
The solution was quite simple:

1. Download sources from gtkspell site;
2. Unpack the sources (right click->Extract Here);
3. Run Terminal and change directory to projects directory;
4. ./configure
5. make
6. Now there are examples in "examples" subdirectory;
7. bash -x <example-name>
8. Last line of previous command output is an executable;
9. Run gdb on the executable.

Thanks :p

---

