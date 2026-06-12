---
title: "Question re. make include directive"
date: 2008-10-25
forum: Programming Talk
---

### Post by FooSoft on 2008-10-25
I've just started playing around with makefiles (have been using IDEs all the time up till now), and I threw together a makefile that does indeed work. However there is one part of it that I just don't understand and it's really bothering me: (keep in mind the .d files contain the dependencies for their respective .cpp files):

```

TARGET = moonfall
PCHFILE = apple.h
OFILES = \
	main.o \
	apple.o

GCHFILE = $(PCHFILE:.h=.h.gch)
COMPILER = g++
CPPFLAGS = -Wall

-include $(OFILES:.o=.d)

all: $(TARGET)

$(TARGET): $(OFILES)
	$(COMPILER) $(OFILES) -o $(TARGET)

%.o: %.cpp $(GCHFILE)
	$(COMPILER) $(CPPFLAGS) -c $*.cpp -o $*.o
	$(COMPILER) $(CPPFLAGS) -MM -MF $*.d $*.cpp

$(GCHFILE): $(PCHFILE)
	$(COMPILER) $(CPPFLAGS) -c $(PCHFILE) -o $(GCHFILE)

clean:
	rm -f $(TARGET) *.o *.d *.gch

```

The "include" directive on the last line has to have a "-" in front of it to work (since the .d may not already exist). However ... all of the dependencies do get applied correctly. So I guess my question is, how does make manage to get dependencies if "-include $(OFILES:.o=.d)" fails? To me it would seem you'd need to run this makefile twice to get the desired result, but that's not the case!

What's the trick here? :confused:

---

### Post by dwhitney67 on 2008-10-25
There are probably several available solutions to the -include directive and to get it to work properly when the Makefile is launched.

Btw, what is the "gch" file?  Why are you compiling header files separately?  Presumably the header file is included in a .cpp file, and hence gets compiled along with the .cpp file.  Do as you please, but this is not a necessary step.

Here's a Makefile you could use, and pick apart for your application:
```

APPS        = moonfall
SRCS        = apple.cpp main.cpp

OBJS        = $(SRCS:.cpp=.o)
CXXFLAGS    = -Wall -pedantic
INCLUDES    = -I./
LIBS        =
LIBPATH     =
DEP_FILE    = .depend


# Typically there is nothing below this line that requires editing.

.PHONY: all clean distclean


all: depend $(APPS)

$(APPS): $(OBJS)
	@echo Makefile - linking $@
	@$(CXX) $(LIBPATH) $(LIBS) $^ -o $@

.cpp.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) $(OBJS)

distclean: clean
	$(RM) $(APPS)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(CXXFLAGS) $(INCLUDES) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

Note that the dependencies are stored within one file (called .depend).  I made it a hidden file because I did not care to see it when listing the contents of the directory containing the source code and Makefile.

The dependency file is set up, if needed, each time the Makefile is invoked, excluding cases where the 'clean' or 'distclean' entry points are explicitly called.

Anyhow, I hope the Makefile listed above can help you with the issue you wrote about.

Let me know if you have additional questions.

---

### Post by FooSoft on 2008-10-25
Interesting, I'll play around with that makefile :) It's remarkably difficult to find realistic makefiles (with automatic dependency generation). 

I actually only compile one header file (this is a pretty bad example, I just made a sample batch of a few files, so the filenames aren't that meaningful) - anyway in this case apple.h is the precompiled header. From my understanding you have to generate a [header filename].gch file for G++ to use it as such.

---

### Post by dwhitney67 on 2008-10-25
> **FooSoft said:**
> ...From my understanding you have to generate a [header filename].gch file for G++ to use it as such.
This is news to me.  I have never heard of such a requirement.  As I stated earlier, the header file is picked up by the compiler when the .cpp file(s) which include the header file is compiled.

Perhaps you are doing something unique; but it is not common practice to compile header files, and this is probably because it is not a requirement when building a project (whether in C or C++).

---

### Post by FooSoft on 2008-10-25
Right, you usually wouldn't compile header files (and in fact, the program will compile just fine w/o it, because as you said, the header files do get included). However, explicitly creating a precompiled header makes compilation a bit faster.

This is what I'm talking about: [http://gcc.gnu.org/onlinedocs/gcc-4.0.4/gcc/Precompiled-Headers.html](http://gcc.gnu.org/onlinedocs/gcc-4.0.4/gcc/Precompiled-Headers.html)

Specifically

> 
To create a precompiled header file, simply compile it as you would any other file, if necessary using the -x option to make the driver treat it as a C or C++ header file. You will probably want to use a tool like make to keep the precompiled header up-to-date when the headers it contains change.

A precompiled header file will be searched for when #include is seen in the compilation. As it searches for the included file (see Search Path) the compiler looks for a precompiled header in each directory just before it looks for the include file in that directory. The name searched for is the name specified in the #include with `.gch' appended. If the precompiled header file can't be used, it is ignored. 


*Edit: Wouldn't there also be a problem with that makefile if you include a new header file in your source file? Any subsequent changes to the newly included .h file won't trigger a rebuild of the .cpp file until the dependency file is rebuilt after a clean.*

---

### Post by dwhitney67 on 2008-10-26
> **FooSoft said:**
> Right, you usually wouldn't compile header files (and in fact, the program will compile just fine w/o it, because as you said, the header files do get included). However, explicitly creating a precompiled header makes compilation a bit faster.

This is what I'm talking about: [http://gcc.gnu.org/onlinedocs/gcc-4.0.4/gcc/Precompiled-Headers.html](http://gcc.gnu.org/onlinedocs/gcc-4.0.4/gcc/Precompiled-Headers.html)

Specifically



*Edit: Wouldn't there also be a problem with that makefile if you include a new header file in your source file? Any subsequent changes to the newly included .h file won't trigger a rebuild of the .cpp file until the dependency file is rebuilt after a clean.*

The Makefile I supplied is sufficient for small applications (10K SLOC or less).  I do not know if you are working on something larger.

If you are working on something larger, then common sense/practice dictates that you would divide the project into libraries.  Thus a change in one library need not necessarily impact another; of course a relinking of the main program would be necessary.

Concerning your post-edit, adding header files to a project is rare, unless of course you are also adding a .cpp (or .c) file that corresponds with it.  If an existing .cpp file requires this new header file, then you would EDIT this existing .cpp file, which hence implies that you need to recompile it.

The bottom line is that your post-edit worries need not be concerns.

Concerning compiling your application faster, I would question whether there is indeed substantial time-savings for your particular needs by precompiling the header files.  As I stated earlier, it is not common practice to do this.

In the link you provided, this statement was made:
```

Often large projects have many header files that are included in every source file.
...

```

I would have written that statement to read:
```

Some large projects may have some header files that are included in many source files.

```
See the difference in the "language" of the statement?  Which do you think is more concise?

I have worked on many projects, none ever exceeding 100K SLOC; definitely small compared to some projects.  Only once have I dealt with an application (in C++) where every class object included a common header file.

When I had to rebuild the application, I did so over the lunch period, or after hours.  The common header file emulated the "Object" class that is auto-magically available in Java.

Don't wind yourself up with trying to save a few minutes or two compiling applications.  The applications that take the longest to compile/link are the ones that are "potentially" poorly designed and/or are coupled too much with other modules.  Avoid this at all cost!

Anyhow, do as you please with your application.  Do not concern yourself with adding new header files; undoubtedly you will also be adding a .cpp file, AND at least in one instance, editing another .cpp file.

---

