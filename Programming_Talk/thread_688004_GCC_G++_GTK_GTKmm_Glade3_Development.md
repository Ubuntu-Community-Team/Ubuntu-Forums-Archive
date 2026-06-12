---
title: "GCC G++ GTK GTKmm Glade3 Development"
date: 2008-02-04
forum: Programming Talk
---

### Post by DugDra on 2008-02-04
Hi All
I am trying to setup a development system on Ubuntu 7.10.
I think I would like to use G++, GTKmm, Glade3 and possibly Anjuta.  Is there a list somewhere that tells what versions and libraries are needed to accomplish this with out conflicts? What are others using for similar projects?

I started this about a month ago and after much searching found one thing at a time to get GCC, Anjuta, GTK++2, and Glade3 installed. I found most of the tutorials old but they appear simple enough I would think they would work. 

At this point the compiler is not finding the include file and having some other problems.  I am trying to, at this point, to write programs with an editor and compile with a terminal.  The programs are mostly examples so I would expect some of them to compile. I think that some of my installed programs have conflicts or I installed the wrong versions.

Any advice how to get back to a starting point and reinstall.  I am not a programer but have writen programs for many years, mostly with Borland Builder C++ and previously on an Amiga in C and C++ from scratch.

Doug Drader

---

### Post by daniel6 on 2008-02-09
I have been trying to get GTK loaded on Dapper with absolutely no success. Had to reload the whole system once due to dependancy hell. To get your compiler up and running you will need to install the kernel headers that match the version of the kernel you are running. Took me a while to figure that one out. I too have used Borland products under Windows for many years and find this Linux absolutely ridiculous. I went for an older version of GTK that was just earlier than the release of Dapper thinking I might have some success. Making your software dependant on libraries and not providing at least a link to a working version is just lame! Maybe these folks should quit trying to reinvent the wheel every six months and try for some long term stability if they expect the rest of the world to take them seriously! Obviously I am a little hot under the colar right now but I have spent days trying to get things loaded and could have had an app running on the Windows side of this box. I am retired and do this for fun. I just can't imagine a professional programmer dealing with this nightmare. Good luck to you and your efforts!
Dan

---

### Post by mb108 on 2008-02-10
_[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-installation.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-installation.html)_

Under Hardy it looks something like this:

build-essential
libgtkmm-2.4-1c2a
libgtkmm-2.4-dev
libglade2-0
libglade2-dev
libglademm-2.4-1c2a
libglademm-2.4-dev
glade-3
glade-gnome-3
... + some other stuff

Version numbers may be slightly different for Dapper, if you're not sure, go into Synaptic, search by name, and install the matching packages which are marked with the Ubuntu icon.

The easy way:
** If you install the libglademm-2.4-dev package, it will pull in pretty much all the libraries you need as dependencies.**

Then just get the Glade application, Anjuta, and whatever else you want to work with.

Try [_this example_]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html"). Works for me.

DugDra, I wouldn't worry too much about un-/re-installing. At this point you probably have some extra packages laying about, but nothing from the official repositories should break your system. It's okay even to have different versions of the same libraries installed, they will coexist peacefully. You will specify which version to use when you compile anyway.

My guess is that you've installed the runtime packages and not the ones for development. You need both.

Library packages usually have a runtime package, then another package for development headers/includes (*-dev), and additionally a package for documentation (*-doc).

This has been standard in Ubuntu since inception. In fact, the entire package management system (and that naming convention) is inherited from Debian, and has been stable for 10+ years.

I realize you are both coming from an non-Linux background, but please recognize:

unfamiliar != unstable

---

### Post by DugDra on 2008-02-10
Thanks MB108
I have all the versions you listed.
I think I have things working OK now,  Most of what I ran into were actually bugs with work a rounds found here and other places on google. The gtkmm library instructions are clear. It looks like the C++ library might be better than libglade but that could be because there are clear examples.

I haven't figured out how to run make successfully from command line. I think I did this years ago with Unix programing but don't have my notes anymore.

Is there something like a path command that tells the compiler where to look for the libraries and includes?  the examples look like this all comes from entries in the command line or make file when you compile.

I normally use C++ but started with C because what I read on several forums said GTK worked best with C or Python.  I haven't written any Python is several years but have used C++ regularly. though mostly with easy access to the functions and classes in Borland Builder C++ and Visual Studio.

Anjuta seems to work OK now though, I haven't got back to it since trying to do the examples with gedit and a terminal.

What is this code used to compile called?
G++ filename.cpp main.cpp -o filename `pkg-config gtkmm-2.4 --cflags --libs`

I was going to google to find more information but don't know what to google.

Doug Drader

---

### Post by DugDra on 2008-02-10
Thanks MB108
I think I have things working OK now,  Most of what I ran into were actually bugs with work a rounds found here and other places on google. The gtkmm library instructions are clear. It looks like the C++ library might be better than libglade but that could be because there are clear examples.

I haven't figured out how to run make successfully from command line. I think I did this years ago with Unix programing but don't have my notes anymore.

Is there something like a path command that tells the compiler where to look for the libraries and includes?  the examples look like this all comes from entries in the command line or make file when you compile.

I normally use C++ but started with C because what I read on several forums said GTK worked best with C or Python.  I haven't written any Python is several years but have used C++ regularly. though mostly with easy access to the functions and classes in Borland Builder C++ and Visual Studio.

Anjuta seems to work OK now though, I haven't got back to it since trying to do the examples with gedit and a terminal.

What is this code used to compile called?
G++ filename.cpp main.cpp -o filename `pkg-config gtkmm-2.4 --cflags --libs`

I was going to google to find more information but don't know what to google.

Doug Drader

---

### Post by mb108 on 2008-02-10
> **DugDra said:**
> 
I haven't figured out how to run make successfully from command line. I think I did this years ago with Unix programing but don't have my notes anymore.

Is there something like a path command that tells the compiler where to look for the libraries and includes?  the examples look like this all comes from entries in the command line or make file when you compile.

(snip)

What is this code used to compile called?
G++ filename.cpp main.cpp -o filename `pkg-config gtkmm-2.4 --cflags --libs`

I might not understand your question completely, but here goes...

That "code used to compile" is what you type in at the command line prompt to compile. The part that is back-ticked:

`pkg-config gtkmm-2.4 --cflags --libs`

Will invoke another tool that will take care of finding everything and generating the correct flags. When I open a terminal and type that pkg-config command (no backticks), I get this:
```

-DPNG_NO_MMX_CODE -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0  -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 
```

All that is the list of flags that will get appended to my g++ command.

Anyway, if you're doing the simple example from the gtkmm site (_[here]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html")_), all you need to do is open a terminal and type:

g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`

This is pretty much the general form for command-line compiling that you will use for simple gtkmm programs. Note that this is case-sensitive (you used a capital 'G' in your post).

Re: Make
I wouldn't worry about this for now, just get some examples going using g++ from the command line. Make has been sort of replaced by automake/autoconf, which automagically generate Makefiles from config files. Anjuta will generate these config files for you when you create a new project, plus it has an option specifically for gtkmm/glademm projects.

---

### Post by Zdravko on 2008-02-10
[mb108]("http://ubuntuforums.org/member.php?u=167819"), this is a very useful information you wrote here! Can you explain further more why is automake/autoconf better than make?
So far, I have used a universal Makefile, that would just compile every C++ program in a directory full of .cpp and .hpp files.:
> 
# define a sample name for the application's name
target := app

# define build options
# compiler name
CXX := g++
# compile options
CXXFLAGS := -ansi -std='c++98' -pedantic -Wall -Weffc++ -Wold-style-cast \
-Wextra -Wunknown-pragmas -Wshadow -Wwrite-strings -Wconversion -Winline \
-Wdisabled-optimization -O3 -march=prescott -mfpmath=sse -mmmx -msse -msse2 \
-msse3
# link options
LDFLAGS := -s
# link libraries
LDLIBS :=

# construct lists of .cpp and their corresponding .o files
sources := $(wildcard *.cpp)
objects := $(sources:.cpp=.o)
dependency := Makefile.dep

# main goal for 'make' is the first target, here 'all'
# 'all' is always assumed to be a target, and not a file
# file disambiguity is achieved via the '.PHONY' directive
# usage: 'make all' or simply 'make', since this is the first target
.PHONY : all clean
all : $(target)
    @echo done.
    @echo 

# rule for 'target'
# the automatic variable '$^' expands to all prerequisites (objects)
# the automatic variable '$@' expands to the target's name
# the actual action done is the linking of all .o files into the executable
$(target) : $(objects)
    @echo linking...
    @$(CXX) $(LDFLAGS) $^ $(LDLIBS) -o $@

# rule for creating an .o file out of a corresponding .cpp file
# the automatic variable '$<' expands to the first prerequisite (%.cpp)
.cpp.o :
    @echo compiling $<...
    @$(CXX) -c $(CXXFLAGS) $< -o $@

# include the dependency file only when 'make clean' is not specified
# this is done to prevent recreating it when the clean target is specified
# if no dependency exist, on the other hand, no warning will be issued:'-' key
ifneq ($(MAKECMDGOALS), clean)
-include $(dependency)
endif

# rule for creating a dependency file
# the preprocessor is used to find out all header-dependencies and store them
# in a dependency file, later to be analyzed by the 'make' utility
$(dependency) :
    @echo 
    @echo generating dependencies...
    @$(RM) $(dependency)
    @$(CXX) -E -MM $(sources) >> $(dependency)

# even if there exists a file 'clean', 'make clean' will execute its commands
# and won't ever assume 'clean' is an up-to-date file
# the 'clean' target will remove all intermediate files - .o, .dep respectively
# usage: 'make clean'
clean :
    @$(RM) $(target) $(dependency) $(objects)
    @echo target, dependencies and objects were removed


I should be able to easily modify this makefile to compile also gtkmm applications. Not sure, however, whether this automake tool is better.

---

### Post by mb108 on 2008-02-11
I don't have time for a full reply, but wanted to follow up.

As with a lot of things, it's in great part a matter of choice. Make is still a great tool, and if you're comfortable with it and it does what you need, then there's no reason to change. For gtkmm, you'll probably just add the `pkg-tools ...` command to that Makefile's CXXFLAGS variable and be good to go. ("probably" because I haven't looked at the whole Makefile closely).

My understanding is that Autotools (automake, autoconf, and libtool) come in handy when managing large projects, with many libraries and in the case where there's multiple source directories or modules. It makes it much easier to change project-wide build settings without having to go into each Makefile, because those are generated from smaller (and supposedly more simple) configuration files. 

You can read more here:
[http://www.openismus.com/documents/linux/automake/automake.shtml](http://www.openismus.com/documents/linux/automake/automake.shtml) (somewhat out of date)
[http://www.lrde.epita.fr/~adl/autotools.html](http://www.lrde.epita.fr/~adl/autotools.html)

... and of course, the definitive Automake manual, straight from the Gnu's mouth:

[http://www.gnu.org/software/automake/manual/](http://www.gnu.org/software/automake/manual/)
Especially: [http://www.gnu.org/software/automake/manual/html_node/GNU-Build-System.html#GNU-Build-System](http://www.gnu.org/software/automake/manual/html_node/GNU-Build-System.html#GNU-Build-System)


Another thing to add is that many people find Autotools (and Makefiles, for that matter) pretty cryptic, and there's significant migration to systems like SCons and CMake, especially for cross-platform projects which include WIndows and OS X targets.

However, Autotools is still the de facto standard in the open-source world, so it may be worth it to you to have at least a basic understanding. If you're joining an existing project then there's a good chance you can get away with letting other people handle it, but I still like knowing how things work.

Whoops, longer than I thought!

---

### Post by Zdravko on 2008-02-13
I managed to build a test gtkmm application with my Makefile. I had to place `pkg-config gtkmm-2.4 --cflags` in the CXXFLAGS and `pkg-config gtkmm-2.4 --libs` in the LDLIBS variable. Then - it worked!
Now I will give cmake a try. It is said to be much better than plain make.

---

### Post by DugDra on 2008-02-17
> **DugDra said:**
> Thanks MB108

What is this code used to compile called?
G++ filename.cpp main.cpp -o filename `pkg-config gtkmm-2.4 --cflags --libs`

I was going to google to find more information but don't know what to google.

Doug Drader

Hi
I guess too many questions in one post!
What I wanted to know is if there is a name for the command line that is used to compile and link the g++ program. If I knew the name I could find out more about it with google.
Thanks again
Doug Drader

---

### Post by mb108 on 2008-02-17
Is this what you're looking for?
[http://gcc.gnu.org/](http://gcc.gnu.org/)

---

