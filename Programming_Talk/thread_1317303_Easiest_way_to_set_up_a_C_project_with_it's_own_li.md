---
title: "Easiest way to set up a C project with it's own library"
date: 2009-11-06
forum: Programming Talk
---

### Post by hofsmo on 2009-11-06
I want to create an application which uses it's own library, like anjuta, gimp and probably many other projects. After some trial and error, and some help [http://ubuntuforums.org/showthread.php?t=1310146](http://ubuntuforums.org/showthread.php?t=1310146), I had it working in anjuta. Sadly it stopped working today, does anyone know how to accomplish this in anjuta? Or is it easier to just learn Autotools?

Many Thanks

---

### Post by dwhitney67 on 2009-11-06
> **hofsmo said:**
> I want to create an application which uses it's own library, like anjuta, gimp and probably many other projects. After some trial and error, and some help [http://ubuntuforums.org/showthread.php?t=1310146](http://ubuntuforums.org/showthread.php?t=1310146), I had it working in anjuta. Sadly it stopped working today, does anyone know how to accomplish this in anjuta? Or is it easier to just learn Autotools?

Many Thanks

Have you ever tried using a terminal and a simple editor like vim?  IMO, skip the IDE until you earn an appreciation for what it takes to compile a simple program.

As for the application you want to create, what is it that you want?  If you define a function in a header file, implement it in a .c (or .cpp) file, then you are on your way to possibly creating a library.  You merely need to decide if you want a shared-object library or a static library... or both!

Once you have the library built, then you write a program with a main() function in it that calls the function within the library.  Voila!

Of course, you will need to link this library with your application.  Do you know how to do this?

---

### Post by matmatmat on 2009-11-07
Eg:
```

//header.h
void donothing();

```

```

//header.c
void donothing(){

}

```

```

//main.c
#include "header.h"

int main(){
    donothing();
    return (1);
}

```
you can compile the above with:
```

gcc main.c -o main header.c

```
for a shared-object libary [this]("http://www.ibm.com/developerworks/library/l-shobj/") may help.

---

### Post by nvteighen on 2009-11-07
Well, technically speaking, each module in a project acts like a library for the rest of the modules... if you're doing things well.

For static and shared libraries, the guide I like most is this: [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

---

### Post by hofsmo on 2009-11-07
Thanks for the response.

I see that I were a bit unclear, I'm able to create a shared library, compile it with gcc and use it with an app, without the help of ajuta. However my dependencies are currently gtk, cairo and gmodule. The gcc command for compiling this is pretty long, and each time I create a new object with it's own header and source file the command grows, and if I in the future needed more dependencies the command would grow even bigger. That's why I moved to anjuta which sets up autotools for me, and all my worries where gone, untill I wanted to create a shared library. Sadly anjuta doesn't do this automatically for me so it's either back to the terminal, learn how to do it in anjuta, learn to use autotools, or maybe another way.

I'm kinda lazy that's why I skipped directly from the terminal to anjuta without learning autotools. One of the goals with anjuta is to let developers develope without having to worry about what goes on behind the scene, however it seems I've reached a dead end, as anjuta doesn't help me anymore. So I'm wandering what's the best approach?

---

### Post by dwhitney67 on 2009-11-07
> **hofsmo said:**
> Thanks for the response.

I see that I were a bit unclear, I'm able to create a shared library, compile it with gcc and use it with an app, without the help of ajuta. However my dependencies are currently gtk, cairo and gmodule. The gcc command for compiling this is pretty long, and each time I create a new object with it's own header and source file the command grows, and if I in the future needed more dependencies the command would grow even bigger. That's why I moved to anjuta which sets up autotools for me, and all my worries where gone, untill I wanted to create a shared library. Sadly anjuta doesn't do this automatically for me so it's either back to the terminal, learn how to do it in anjuta, learn to use autotools, or maybe another way.

I'm kinda lazy that's why I skipped directly from the terminal to anjuta without learning autotools. One of the goals with anjuta is to let developers develope without having to worry about what goes on behind the scene, however it seems I've reached a dead end, as anjuta doesn't help me anymore. So I'm wandering what's the best approach?

Perhaps learn how to create a Makefile?

If you are just a programming hobbyist, then read the docs on Anjuta.  Otherwise, it is in your best interest to learn how things work "under the hood" in case you are faced with a development environment where Anjuta, Eclipse, or some other IDE is unavailable.

P.S.  A typical Makefile would look something like:
```

APP     = myapp

OBJDIR  = .srcobjs
SRCS    = $(shell find . -name '*.c')
SRCDIRS = $(shell find . -name '*.c' -exec dirname {} \; | uniq)
OBJS    = $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))
DEPS    = $(patsubst %.c,$(OBJDIR)/%.d,$(SRCS))

CFLAGS  = -Wall -pedantic -ansi -c
CFLAGS += `pkg-config --cflags gtk+-2.0`
LFLAGS  = `pkg-config --libs gtk+-2.0`

.PHONY: all clean distclean

all: buildrepo $(APP)

$(APP): $(OBJS)
        @echo Linking $@
        @$(CC) $^ $(LFLAGS) -o $@

$(OBJDIR)/%.o: %.c
        @echo Generating dependencies for $^
        @$(call make-depend, $<, $@, $(subst .o,.d,$@))
        @echo Compiling $^
        @$(CC) $(CFLAGS) $< -o $@

clean:
        $(RM) -r $(OBJDIR)

distclean: clean
        $(RM) $(APP)

buildrepo:
        @$(call make-repo)

# Functions
#
define make-repo
   for dir in $(SRCDIRS); \
   do \
        mkdir -p $(OBJDIR)/$$dir; \
   done
endef

# usage: $(call make-depend, SourceFile, ObjectFile, DependFile)
define make-depend
  $(CC) -MM -MF $3 -MP -MT $2 $(CFLAGS) $1
endef


# Include dependencies
#
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

```
Modify the CFLAGS and LFLAGS to adjust for your particular project.

---

### Post by hofsmo on 2009-11-07
Thanks, I think I'll learn how to use makefiles, however should I move on to autotools after a while, or will I be just fine using makefiles?

---

### Post by dwhitney67 on 2009-11-07
> **hofsmo said:**
> Thanks, I think I'll learn how to use makefiles, however should I move on to autotools after a while, or will I be just fine using makefiles?

The more you can learn, the better.  But never limit your abilities to just one tool.

---

