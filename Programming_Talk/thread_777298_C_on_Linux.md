---
title: "C on Linux"
date: 2008-05-01
forum: Programming Talk
---

### Post by uzusan on 2008-05-01
Does anyone know of any tutorials that focus specifically on c programming on linux? I know the language itself, from previous experience on dos / windows but i would like a tutorial on the linux / unix way of doing things.

For example, i know next to nothings about makefiles (creating them i mean, i know how to use them) and other things, like the practice of using a src folder for your source files.

---

### Post by dwhitney67 on 2008-05-01
Programming in C on both MS-Windows and Linux should be relatively the same --- that's the beauty of the ISO standards for the C programming language.

Concerning Makefiles, this is an unrelated topic to C, however to learn more about writing your own Makefiles, go here:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

Developing software projects in folders (directories), other than the home directory, is not a requisite, however it is convenient as a means to keep things organized on one's system.

---

### Post by uzusan on 2008-05-01
> **dwhitney67 said:**
> Programming in C on both MS-Windows and Linux should be relatively the same --- that's the beauty of the ISO standards for the C programming language.

Concerning Makefiles, this is an unrelated topic to C, however to learn more about writing your own Makefiles, go here:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

Developing software projects in folders (directories), other than the home directory, is not a requisite, however it is convenient as a means to keep things organized on one's system.

Thanks for that link, it was that sort of thing i was aiming for. I suppose what im looking for is details on how to create programs so i can use the tools in the build-essentials package, so that they will compile with the standard ./configure, make and make install commands.

I'll have a look through the documentation on makefiles and see if i can get them working.

---

### Post by dwhitney67 on 2008-05-01
In addition, I would also recommend that you become familiar with interfacing with the gnome-terminal and writing your code there, either using something like vim or gedit, or whatever.

A simple program:
[PHP]#include <stdio.h>

int main()
{
  printf( "Hello World\n" );
  return 0;
}[/PHP]

To compile:
```
$ gcc hello.c -o hello
```

To run:
```
$ ./hello
```

---

### Post by uzusan on 2008-05-01
> **dwhitney67 said:**
> In addition, I would also recommend that you become familiar with interfacing with the gnome-terminal and writing your code there, either using something like vim or gedit, or whatever.

A simple program:
[PHP]#include <stdio.h>

int main()
{
  printf( "Hello World\n" );
  return 0;
}[/PHP]

To compile:
```
$ gcc hello.c -o hello
```

To run:
```
$ ./hello
```

I do use the terminal for a lot of things and i have had some experience programming in python and some bash scripts. I have touched on using the gcc compiler years ago when i was using DJGPP and the Allegro games library but i've not used it much since.

---

### Post by dwhitney67 on 2008-05-01
I have never had to deal with configure, other than using it to build packages I downloaded from GNU.  Here's a link for further reading:  [http://www.airs.com/ian/configure/](http://www.airs.com/ian/configure/)

As for 'make' and 'make install', these both invoke the Makefile with the latter statement specifically referencing the "install" entry point.  Here's a typical Makefile that could build the hello.c program I provided earlier.

```

SRCS     := $(wildcard *.c)
APP      := hello

CFLAGS   := -g
INCPATH  := -I./

OBJS     := $(SRCS:.c=.o)
LIBPATH  :=
LIBS     :=
DEP_FILE := .depend

.PHONY: all install test clean distclean


all install test: depend $(APP)

$(APP): $(OBJS)
	@echo Makefile - linking $@
	@$(CXX) $^ $(LIBPATH) $(LIBS) -o $@

clean:
	$(RM) *.o core*

distclean: clean
	$(RM) $(APP)
	$(RM) $(DEP_FILE)

.c.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CFLAGS) $(INCPATH) -c $< -o $@

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@$(CXX) -E -MM $(INCPATH) $(SRCS) >> $(DEP_FILE)
	@echo Makefile - dependencies created for: $(SRCS)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by rplantz on 2008-05-01
A reasonably good book is the O'Reilly one, "Programming with GNU Software." It's a bit old.

When I did a search, I came up with [http://www.lrde.epita.fr/~akim/compil/doc/gnuprog2/](http://www.lrde.epita.fr/~akim/compil/doc/gnuprog2/), or in pdf format [http://www.lrde.epita.fr/~akim/gnuprog2.pdf](http://www.lrde.epita.fr/~akim/gnuprog2.pdf). It's not the same book. From a quick glance, it looks pretty good.

Just as a note, what you are really interested in is gnu programming tools. The kernel is linux. Almost all linux distributions use the gnu programming tools, and almost everyone thinks of them as linux programming tools. (I hope this remark doesn't come across with a "tsk, tsk" attitude, but I wanted to give the gnu people credit for their hard work.)

---

### Post by tw3k on 2008-05-01
Two of my favorites; [The GNU C Programming Tutorial]("http://www.crasseux.com/books/ctutorial/") and [URL="http://www.cs.cf.ac.uk/Dave/C/"]Programming in C
UNIX System Calls and Subroutines using C.[/URL]. You might like the [Autoconf manual]("http://www.gnu.org/software/autoconf/manual/autoconf-2.57/html_mono/autoconf.html") as well.

---

### Post by JupiterV2 on 2008-05-01
Once you're familiar with makefiles, its probably useful to take the next step and learn GNU auto-tools. I don't have a link handy but a quick google search on the following topics will get you want you want:

autotools: automake, autoconf, autoheader, aclocal...

I think [autotut]("http://www.seul.org/docs/autotut/") (auto-tutorial) was a good beginner site if I recall. Ultimately, you'll want to read the GNU docs.

---

### Post by Kadrus on 2008-05-01
Writing and compiling C programs under Linux
[http://flame.cs.dal.ca/~subbu/CBook/c%20languange/Writing%20and%20Compiling%20C%20programs%20on%20Linux.htm](http://flame.cs.dal.ca/~subbu/CBook/c%20languange/Writing%20and%20Compiling%20C%20programs%20on%20Linux.htm)
Its a short tutorial..read the stickies for more information..

---

