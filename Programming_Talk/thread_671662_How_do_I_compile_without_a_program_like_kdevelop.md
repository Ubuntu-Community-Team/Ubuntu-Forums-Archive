---
title: "How do I compile without a program like kdevelop?"
date: 2008-01-18
forum: Programming Talk
---

### Post by speedingbullet on 2008-01-18
I keep hearing that using kdevelop is not a wise decision.... but how on earth am I supposed to compile the rest? I know G++ is involved, but it wont work unless you have files such as configure...

What program do I use to make the other files that G++ needs to compile with a program? If your supposed to make them manually... where can I find tutorials for this?

---

### Post by Wybiral on 2008-01-18
You don't need any magic files to use gcc, just read the manual:
```

man gcc

```

Maybe you're talking about makefiles, in that case [hit the manual]("http://www.gnu.org/software/make/manual/make.html") (you're probably better off looking at examples, that thing is huge, but you might want to read the first few sections).

---

### Post by olejorgen on 2008-01-18
Numerous build systems are available: (short list)
make: very basic, you essentially write the commands neccessary to compile/build 
autotools: automatic makefile generation
jam: not sue
icomplie: claims to figure out dependency automatically

You might want to look at pkg-config too

---

### Post by speedingbullet on 2008-01-18
thanks, both of you

---

### Post by stevescripts on 2008-01-18
Just in case we have overlooked the obvious ...

Have you installed build-essential ? 

if not:
```

sudo apt-get build-essential

```

You can build a lot of stuff from the command line using gcc,
but at some point your going to need to deal with configure,
make, etc ...

Steve

---

### Post by speedingbullet on 2008-01-18
Thats my problem though... the program I am making is divided  into individual files. Its a text game, so I think this is very necessary so I don't get lost trying to program it.

Don't programs like that need files that link the files together?


I'll probably be experimenting with GTKMM before too long... Id rather take steps before trying to learn opengl... its just that I don't think my game is suited for UNIX/MSDOS.

---

### Post by stevescripts on 2008-01-18
> **speedingbullet said:**
> Thats my problem though... the program I am making is divided  into individual files. Its a text game, so I think this is very necessary so I don't get lost trying to program it.


I understand, in general modular programming is a good thing ;)

> Don't programs like that need files that link the files together?

makefiles - which aren't as daunting as the first seem...

> I'll probably be experimenting with GTKMM before too long... Id rather take steps before trying to learn opengl... its just that I don't think my game is suited for UNIX/MSDOS.


The choice of GUI programming tools, is a thing of personal
preference.  Getting the text version worked out first, is the
right thing to do.

HTH

Steve

---

### Post by Wybiral on 2008-01-18
If you don't want to mess with makefiles yet, you can do this using just GCC. A shell script could easily be used to keep it all together. For a simple build...

Compile each "cpp" file using:
```

g++ -c source.cpp -o source.o

```
Which will generate your object files.

Then, link them all using:
```

g++ source1.o source2.o source3.o -o program

```
During the linking process, you may have to link to any external libraries you use. Naturally, "source" is just an example.

---

### Post by jblebrun on 2008-01-19
Or, just throw it all together into 1 step:

g++ source1.cpp source2.cpp source3.cpp -o myprogram

For simple projects with just 3-4 files, this works fine.

---

### Post by dwhitney67 on 2008-01-19
As stevescripts pointed out, Makefiles are not a big deal.  Here's a sample Makefile that you can copy and modify to fit your C++ project:

[PHP]SRCS     = SourceFile1.cpp SourceFile2.cpp SourceFile3.cpp SourceFileN.cpp

APP      = myProgramName

CXXFLAGS = -g
INCPATH  = -I../include

OBJS     = $(SRCS:.cpp=.o)
LIBPATH  = -L../lib
LIBS     = -lTCP -lboost_thread-mt
DEP_FILE = .depend

.PHONY: clean cleanall

# Note that from here on down, indented lines commence with a tab-space!
#
$(APP): $(OBJS)
	@echo Makefile - linking $<
	@$(CXX) $^ $(LIBPATH) $(LIBS) -o $@

clean:
	$(RM) *.o core*

distclean: clean
	$(RM) $(APP)
	$(RM) $(DEP_FILE)

.cpp.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CXXFLAGS) $(INCPATH) -c $< -o $@

depend:
	@$(RM) $(DEP_FILE)
	@for i in $(SRCS) ; do \
		$(CXX) -E -MM $(INCPATH) $$i >> $(DEP_FILE); \
	done

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif[/PHP]

P.S.  Important thing to know... to invoke a Makefile, run this command:
```
$ make
```

---

### Post by DMills on 2008-01-19
The only thing I would add to the example Makefile above is that CXXFLAGS should probably be:

CXXFLAGS = -g -Wall -W -O 

to increase the  chances of the compiler generating useful warnings. 

Also, in a Makefile <tab> and <set of spaces> are NOT equivalent, and if it cries about a "Missing separator" then you have spaces where you need tabs. 

Regards, Dan.

---

