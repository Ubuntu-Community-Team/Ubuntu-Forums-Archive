---
title: "Issues with a universal Makefile for C++"
date: 2008-01-25
forum: Programming Talk
---

### Post by Zdravko on 2008-01-25
I am trying to write a universal Makefile for all of my C++ programs. Here is what I came up to:
```

# define a sample name for the application's name 
target := app 
 
# define build options 
# compiler name 
CXX := g++ 
# compile options 
CXXFLAGS := 
# link options 
LDFLAGS := 
# link libraries 
LDLIBS := 
 
# construct list of .cpp and their corresponding .o and .d files 
sources := $(wildcard *.cpp) 
objects := $(sources:.cpp =.o) 
dependencies := $(sources:.cpp=.d) 
 
# include all .d files only when 'make clean' is not specified 
# this is done to prevent recreating .d files when the clean target is specified 
# if no dependencies exist, on the other hand, no warning will be issued:'-' key 
ifneq ($(MAKECMDGOALS), clean) 
-include $(dependencies) 
endif 
 
# main goal for 'make' is the first target, here 'all' 
# 'all' is always assumed to be a target, and not a file 
# file disambiguity is achieved via the '.PHONY' directive 
# usage: 'make all' or simply 'make', since this is the first target 
.PHONY : all 
all : $(target) 
 
# rule for 'target' 
# the automatic variable '$<' expands to the first prerequisite (objects) 
# the automatic variable '$@' expands to the target's name 
# the actual action done is the linking of all .o files into the executable 
$(target) : $(objects) $(dependencies) 
    $(CXX) $(LDFLAGS) $< $(LDLIBS) -o $@ 
 
# rule for creating .o files out of a corresponding .cpp and .d file 
%.o : %.cpp %.d 
    $(CXX) -c $(CXXFLAGS) $< -o $@ 
 
# rule for creating .d files out of a corresponding .cpp file 
%.d : %.cpp 
    $(CXX) -E -MM $< -o $@ 
 
# even if there exists a file 'clean', 'make clean' will execute its commands 
# and won't ever assume 'clean' is an up-to-date file 
# the 'clean' target will remove all intermediate files - .o and .d respectively 
# usage: 'make clean' 
.PHONY : clean 
clean : 
    rm -f $(target) $(dependencies) $(objects)

```

It doesn't work as expected. An .o and .d file is created, but no app. make clean purges even the .cpp file. Why is that? Can anyone explain me?

---

### Post by dwhitney67 on 2008-01-25
Your .cpp files are being deleted when performing a 'make clean' because you have a white-space just before the equal sign in the statement:

```
objects := $(sources:.cpp =.o)
```

Fix that, by removing the white-space and that issue of source files being deleted will go away.

As for the other issues you are having, I couldn't relate too much to how you were setting up the dependencies, so I re-did in a way I was more comfortable of doing it.  I also corrected (?) the entry point for converting .cpp files to .o files.

Here's a listing of the Makefile I tested with:
```

# define a sample name for the application's name 
target := app 
 
# define build options 
# compile options 
CXXFLAGS :=
# link options 
LDFLAGS := -L../../../library
# link libraries 
LDLIBS := -lTCP -lboost_thread
 
# construct list of .cpp and their corresponding .o and .d files 
sources  := $(wildcard *.cpp) 
includes := -I../../../library
objects  := $(sources:.cpp=.o) 
dep_file := Makefile.dep
 

# file disambiguity is achieved via the '.PHONY' directive 
.PHONY : all clean 


# main goal for 'make' is the first target, here 'all' 
# 'all' is always assumed to be a target, and not a file 
# usage: 'make all' or simply 'make', since this is the first target 
#
all : $(target) 
 

# rule for 'target' 
# the automatic variable '$<' expands to the first prerequisite (objects) 
# the automatic variable '$@' expands to the target's name 
# the actual action done is the linking of all .o files into the executable 
#
$(target) : $(objects)
	$(CXX) $(LDFLAGS) $^ $(LDLIBS) -o $@ 


# even if there exists a file 'clean', 'make clean' will execute its commands 
# and won't ever assume 'clean' is an up-to-date file 
# usage: 'make clean' 
#
clean : 
	$(RM) $(target) $(dep_file) $(objects)
 

# rule for creating .o files
#
.cpp.o :
	$(CXX) $(CXXFLAGS) $(includes) -c $< -o $@ 
 

# rule to make dependencies within one file
#
depend $(dep_file):
	@echo Makefile - creating dependencies for: $(sources)
	@$(RM) $(dep_file)
	@$(CXX) -E -MM $(includes) $(sources) >> $(dep_file)


# include dependency file only when 'make clean' is not specified 
# this is done to prevent recreating the dependency file when the clean target is specified 
# if no dependencies exist, on the other hand, no warning will be issued:'-' key 
#
ifeq (,$(findstring clean,$(MAKECMDGOALS)))
-include $(dep_file)
endif
```

Enjoy!

---

### Post by Zdravko on 2008-01-25
Thanks! Your version works!
I have however a few more questions.
Why do you use the '>>' operator for saving the dependency file, and not the preprocessor option -o?
The 'depend' rule doesn't have any prerequisites. It is always executed. Why?
After including the fresh generated dep file, the make utility switches to it. Do you know a way to tell it use the same compiler options? Else, it would rely on the default implicit rules for creating .o out of .cpp files?

---

### Post by dwhitney67 on 2008-01-25
Why do you use the '>>' operator for saving the dependency file, and not the preprocessor option -o?
**Answer:**  Because I did; the -o option works too.

The 'depend' rule doesn't have any prerequisites. It is always executed. Why?
**Answer:**  No, it is not always executed.  See the comments you provided with the section dealing with MAKECMDGOALS.  Btw, you may want to add another conditional for 'depend' (or just remove the label for such so that it is not a valid entry point).

After including the fresh generated dep file, the make utility switches to it. Do you know a way to tell it use the same compiler options? Else, it would rely on the default implicit rules for creating .o out of .cpp files?
**Answer:**  I really haven't clue what you are asking.  The make utility references the dependency file, it does not switch to it.  Compiler options... do mean does in CXXFLAGS?

---

### Post by Zdravko on 2008-01-25
Yes, I mean CXXFLAGS etc. The make manual says that include does exactly this. Hmm, lemme check... :)

---

### Post by Zdravko on 2008-01-25
It works. Thanks again.

---

### Post by Zdravko on 2008-08-09
Do you know how can I place all .o files and the .dep file in a separate directory? And the executable of the program to be placed in another directory?
Thanks in advance!

---

### Post by dwhitney67 on 2008-08-09
You can try something like the following:
```

SRCS    := $(wildcard *.cpp)
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -pedantic -O2
INCLUDES = -I./

LDFLAGS  =
LDLIBS   = -lpthread

DEPFILE  = Make.depend
DEPDIR   = dep
OBJDIR   = obj

TARGET   = MyApp
DESTDIR  = $(HOME)

.PHONY: clean distclean


all: depend $(TARGET)
	@echo Installing $(TARGET) into $(DESTDIR)
	@install -m 0755 $(TARGET) $(DESTDIR)

$(TARGET) : $(OBJS)
	@echo Linking $(TARGET)...
	@$(CXX) $(LDFLAGS) $(OBJDIR)/*.o $(LDLIBS) -o $@

.cpp.o :
	@echo Compiling $<...
	@mkdir -p $(OBJDIR)
	@$(CXX) $(CXXFLAGS) $(includes) -c $< -o $(OBJDIR)/$@

clean : 
	$(RM) -r $(OBJDIR)
	$(RM) -r $(DEPDIR)
	$(RM) $(TARGET)

distclean: clean
	$(RM) $(DESTDIR)/$(TARGET)

depend: $(DEPDIR)/$(DEPFILE)
	@touch $(DEPDIR)/$(DEPFILE)

$(DEPDIR)/$(DEPFILE):
	@echo Makefile - building dependencies in: $@
	@mkdir -p $(DEPDIR)
	@$(CXX) -E -MM $(CXXFLAGS) $(INCLUDES) $(SRCS) >> $@

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEPFILE)
endif
endif

```

---

### Post by Zdravko on 2008-08-09
Thanks. I will give it a try! :)

---

### Post by dwhitney67 on 2008-08-09
I've been testing it myself, and I believe the dependencies will be a problem.

The dependency file is set up to look for the object files in the current working directory.  If you insist in placing the object files into a separate directory, then the dependency file will need to be made aware of this.  Right now, I do not have any idea on how to indicate that the .o files are in a sub-directory.

Maybe someone else can help you.  IMO, I would leave the .o in the current directory with the source code.  The dependency file, if you wish can be set up to be a hidden file; just precede the name with a dot (e.g. DEPFILE = .depend).

---

### Post by Zdravko on 2008-08-09
The depend file could be placed in the the directory together with the object files. But I need the separation from source code and object files - for clarity.

---

### Post by dwhitney67 on 2008-08-09
> **Zdravko said:**
> The depend file could be placed in the the directory together with the object files.

That won't work either, but you can try.
> **Zdravko said:**
> But I need the separation from source code and object files - for clarity.
'need', or 'want'??

If after you finish installing your application at the location specified by DESTDIR, just run 'make clean' to clean up the working directory.  The application will remain in place until you run 'make distclean'.

---

### Post by Zdravko on 2008-08-09
Ok, I want it to be like this. 
I just want to keep things simple. While make is processing the source the whole directory gets full of these .o files. I just wanted to separate them in another subdir so that they don't bother me.
But I can live with the old way also.
Thanks anyway for the effort! make is an antique machinery but at least it is working.

---

### Post by Zdravko on 2009-02-08
I think this is a pretty stable version of the universal makefile for C++:
```

# This is a universal makefile for compiling and linking C++ applications
# Creation date: 05.09.2008
# Last update: 08.02.2009

# Usage:
# 1. Place a copy of this makefile in the source code directory
# 2. Invoke 'make' in that directory
# 3. Dependencies are resolved recursively for the compiler and linker
# 4. Launch your application (name is as specified in the makefile).

# define a name for the application's name
target := app

# define build options - adjust the lists according to your needs:

# include directories for custom header files:
INCL_DIRS :=

# link options:
LDFLAGS :=

# link libraries - preceeded with 'l':
LDLIBS :=

# compile options:
CXXFLAGS := \
-ansi \
-pedantic \
-fdiagnostics-show-option \
-Wall \
-Wextra \
-Weffc++ \
-Wctor-dtor-privacy \
-Wold-style-cast \
-Woverloaded-virtual \
-Wmissing-include-dirs \
-Wswitch-default \
-Wswitch-enum \
-Wunused-parameter \
-Wunknown-pragmas \
-Wundef \
-Wshadow \
-Wcast-qual \
-Wredundant-decls \
-Wdisabled-optimization \
-Winline \
-Wunreachable-code
# -O3
#-w //inhibit all warnings
#-time // dump building time

# Below follows the actual makefile section where commands are performed.
# There will be rarely need to change something there.

# construct a list of .cpp (source) files
sources := $(wildcard *.cpp)

# construct a list of the corresponding .o (object) files
objects := $(sources:.cpp=.o)

# name of the dependency file - no need to touch it
dependency := Makefile.dep

# main goal for 'make' is the first target, here - all
# all is always assumed to be a target, and not a file
# file disambiguity is achieved via the .PHONY directive
# usage: make all or simply make, since this is the first target
.PHONY : all clean
all : $(target)

# the automatic variable $^ expands to all prerequisites (objects)
# the automatic variable $@ expands to the targets name
# the actual action done is the linking of all .o files into the executable
# a preceeding @ symbol before a non-make command doesn't print the command
$(target) : $(objects)
    @echo linking...
    @g++ $(LDFLAGS) $^ $(LDLIBS) -o $@
    @echo done.

# rule for creating an .o file out of a corresponding .cpp file
# the automatic variable $< expands to the first prerequisite (.cpp)
.cpp.o :
    @echo compiling $<...
    @g++ $(CXXFLAGS) $(INCL_DIRS) -c $< -o $@

# even if there exists a file clean, make clean will execute its commands
# and will not ever assume clean is an up-to-date file
# the clean target will remove all intermediate files -
# .o, .dep respectively
# usage: make clean
clean :
    @$(RM) $(objects)
    @$(RM) $(target)
    @$(RM) $(dependency)
    @echo target, dependencies and objects were removed

$(dependency):
    @echo generating dependencies...
    @g++ -E -MM $(sources) -o $@

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
-include $(dependency)
endif

```

I will gladly appreciate any comments or bug issues if you notice any.

---

### Post by dwhitney67 on 2009-02-08
It looks good, although I would recommend that you use make's alias for g++, which is $(CXX).

There are instances where one needs to build their application using a cross-compiler (or an older compiler), thus this person could override CXX with their own definition.

Anyhow, for now, in your "universal" Makefile, wherever you see a 'g++', replace it with a '$(CXX)'.

P.S.  You also should create a Makefile that can be used to create a library that consists of an archive of object files, and another Makefile that can be used to create a shared-object library.

---

### Post by Zdravko on 2009-02-08
Yes, I know about the CXX variable. I may fix it.
But how do I make a shared library? What do you mean under archive of object files? Elaborate, when you have time...

---

### Post by dwhitney67 on 2009-02-08
> **Zdravko said:**
> Yes, I know about the CXX variable. I may fix it.
But how do I make a shared library? What do you mean under archive of object files? Elaborate, when you have time...

I do not recall using the word "under".

An archive of object files is merely another term used to indicate that the object files, which are produced using the GCC option -c, are collected into a file using the ar(chive) command.  In a Makefile, this step would look something like:

```

...

$(LIBNAME) : $(LIB_OBJS)
        $(AR) $(ARFLAGS) $@ $^

...

```
$(AR) is understood by the Makefile to be /usr/bin/ar, and typically the $(ARFLAGS) includes at a minimum the -r option.  The $(LIBNAME) is generally associated with a filename with the "libSomeName.a" format.

When linking an archive library into an application, the objects within the library (at least those that are necessary), are included in the footprint of the application.  Thus the application is portable to other similar platforms without worry about missing dependencies.

In regards to a shared-object library, think of the DLL under the Windoze OS.  These libraries are loaded at run-time, and thus an application's footprint is smaller, and potentially less portable.

Building shared-object libraries require a whole slew of different GCC options.  Here's an example usage:
```

...

CXXFLAGS = -Wall -ansi -pedantic -fPIC

...

$(LIBNAME): $(LIBOBJS)
        $(CXX) -shared -W1,-soname,$@.1 -o $(LIBREL) $^

...

```
Typically there is also a section in the Makefile that installs the shared-object file (using /usr/bin/install).  The $(LIBREL) has a format similar to libSomeName.so.VersionNumber.  It is up to the Makefile to setup the symbolic link for libSomeName.so.to point to the aforementioned library with the version number in its name.

If either the archive library or an shared-object library are installed in the system folders (e.g. /usr/lib or /usr/local/lib), then it is wise to run 'ldconfig' so that these can be easily referenced by applications that require them.

P.S.  My knowledge on building shared-object libraries is limited, having done it only once before.

---

### Post by Zdravko on 2009-02-08
Interesting. I wish I knew more about this.
In fact, the object archive is a kind of a ready-to-link part of the application, right? This means I can compile my cpp files to .o files, archive them in a single archive and then give them to a potential user? Then he or she will just link them to its own app, is that ok?

I think that the idea of a shared library is much more interesting. It gives the developer freedom to maintain small sized applications, each of them using a shared part, right? Then, this must be much better, than the damned object archive?

---

### Post by dwhitney67 on 2009-02-08
> **Zdravko said:**
> Interesting. I wish I knew more about this.
In fact, the object archive is a kind of a ready-to-link part of the application, right? This means I can compile my cpp files to .o files, archive them in a single archive and then give them to a potential user? Then he or she will just link them to its own app, is that ok?

I think that the idea of a shared library is much more interesting. It gives the developer freedom to maintain small sized applications, each of them using a shared part, right? Then, this must be much better, than the damned object archive?

Answer to Q1: Yes.
Answer to Q2: Maybe.

Please understand that if your target audience does not have the shared-library installed on their system, then they cannot run an application that depends upon it.

If you are interested in developing libraries that other developers can use, it is wise to provide BOTH an archive library and a shared-object library.  Let the application developer decide what is best for their needs.

P.S.  Don't forget that a "library" is not complete unless you also furnish the application developers the header files that include class/function declarations that are in your library.  Also documentation (which may include man-pages).

---

### Post by Zdravko on 2009-02-08
[dwhitney67]("http://ubuntuforums.org/member.php?u=322753"), this is so inspiring! Where can I learn the principles of shared/archive libraries?

---

### Post by dwhitney67 on 2009-02-08
Google or use other search engine.  I learned by necessity and through the help of others.  I had no particular guide or tutorial to rely upon.

---

