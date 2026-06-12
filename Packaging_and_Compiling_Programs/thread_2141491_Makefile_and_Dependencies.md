---
title: "Makefile and Dependencies"
date: 2013-05-02
forum: Packaging and Compiling Programs
---

### Post by jerecb on 2013-05-02
Hi, 

I'm a bit new to makefiles, and I'm trying to get to grips with them. I think I've got the basics, but I've run into a behavior which I don't understand. 

Here's my makefile (borrowed from various tutorials and examples): 

```

CFLAGS  =-Wall
OBJDIR  =./obj/Debug/
BINDIR  =./bin/Debug/

OBJECTS = main.o \
          Daemon.o \
          DemonConfig.o


all: mkdirs getobj $(EXECUTABLE) putobj


$(EXECUTABLE): $(OBJECTS)
	-@echo Build For: $(target)
	$(CC) $(CFLAGS) -o $@ $^


# Check dependency info for existing .o files:
-include $(OBJECTS:.o=.d)


%.o: %.c
	$(CC) $(CFLAGS) -o $@ -c $<
	$(CC) -MM $(CFLAGS) $< > $*.d 


clean:
	-rm -f $(EXECUTABLE) $(OBJDIR)*.o *.d


mkdirs:
	-@mkdir -p $(OBJDIR)
	-@mkdir -p $(BINDIR)


getobj:
	-@mv $(OBJDIR)*.o .  2>/dev/null


putobj:
	-@mv *.o $(OBJDIR)   2>/dev/null



```

This is all working well. I use the -MM flag on the compiler to output dependency information which is saved to a .d file for each input .c that is processed. This works nicely to detect changes to any of the headers, c files, etc, and cause them to be rebuilt if required. 

PROBLEM: I'd like to place the .d files somewhere (e.g. ./obj) so they don't clutter my source. I added the appropriate 'mv' commands to the getobj and putobj targets, which moved the files as required. 

HOWEVER, with the .d files moved to ./obj, the dependency no longer works (i.e. changes to .h files don't trigger a rebuild). Obviously, they will only work when in the source directory. However, I put 'echo' lines in getobj and putobj and they are definitely getting called even when there is nothing to do. SO, it looks like it is moving the files to the source directory, doing nothing, then moving them back. If I remove 'putobj' and change a .h file, no build will occur on the first 'make', but the build WILL occur on the second 'make' - so the .d files need to already be there sometime BEFORE my getobj target is called - but I thought it should be called FIRST (since it's the first thing under the 'all' target). 

Am I missing something about how make works? Thanks!

---

### Post by flashmanblack on 2013-05-03
makefile is not easy to master indeed when i first get started with it

---

### Post by flashmanblack on 2013-05-03
i suggest that you should copy a well-written makefile  and customize it to meet your demand and i am new to makefile.

---

### Post by schragge on 2013-05-05
Just wondering, have you tried
```

-include $(OBJDIR)dependencies.d

%.o: %.c
        $(CC) $(CFLAGS) -o $@ -c $<
        $(CC) -MM $(CFLAGS) $< >>$(OBJDIR)dependencies.d

```

---

### Post by jerecb on 2013-05-13
> **schragge said:**
> Just wondering, have you tried

```

-include $(OBJDIR)dependencies.d

%.o: %.c
        $(CC) $(CFLAGS) -o $@ -c $<
        $(CC) -MM $(CFLAGS) $< >>$(OBJDIR)dependencies.d

```


It's a nice idea, and I did consider it. However, note the use of APPEND: ">>$(OBJDIR)dependencies.d". Hence the dependency file would keep growing and old data wouldn't be removed. 

We can't use "rm $(OBJDIR)dependencies.d" (I don't think) because we need to update each part (i.e. dependencies for the current C file) as we process it. If we deleted the whole file before we started, that would defeat the purpose...

---

