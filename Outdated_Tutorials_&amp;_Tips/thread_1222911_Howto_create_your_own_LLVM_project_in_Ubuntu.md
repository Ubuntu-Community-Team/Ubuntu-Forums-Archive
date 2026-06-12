---
title: "Howto: create your own LLVM project in Ubuntu"
date: 2009-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by manualqr on 2009-07-25
LLVM has great documentation, but there are a couple issues with creating your own project if you're on *buntu. I hope you'll avoid the same traps I got into by following this guide!

The first thing you should do is get, configure, and build LLVM. This should be easy enough (just be sure to enable the options you need and make binaries only for your platform!). You will need to install flex, bison, and build-essential beforehand.

>  sudo apt-get install bison flex build-essential 

To create your own project, copy llvm/projects/sample to any directory you own. Copy Makefile.common, Makefile.common.in, configure, and config.status from the LLVM source root into the top of your project directory. Modify autoconf/configure.ac to your needs. Here is mine:
```

# <snip>

AC_INIT([FOO_PROJECT],[0.01],[obfuscated@gmail.com])

dnl Identify where LLVM source tree is
LLVM_SRC_ROOT="/home/vk/Projects/llvm-2.5"
LLVM_OBJ_ROOT="/home/vk/Projects/llvm-2.5"
dnl Tell autoconf that the auxilliary files are actually located in
dnl the LLVM autoconf directory, not here.
AC_CONFIG_AUX_DIR($LLVM_SRC_ROOT/autoconf)

dnl Tell autoconf that this is an LLVM project being configured
dnl This provides the --with-llvmsrc and --with-llvmobj options
LLVM_CONFIG_PROJECT($LLVM_SRC_ROOT,$LLVM_OBJ_ROOT)

dnl Verify that the source directory is valid
AC_CONFIG_SRCDIR(["Makefile.common.in"])

dnl Configure a common Makefile
AC_CONFIG_FILES(Makefile.common)

dnl Configure project makefiles
dnl List every Makefile that exists within your source tree
AC_CONFIG_MAKEFILE(Makefile)
AC_CONFIG_MAKEFILE(tools/Makefile)
AC_CONFIG_MAKEFILE(tools/fookl/Makefile)
AC_CONFIG_MAKEFILE(tests/Makefile)

# <snip>

```

Next, modify your top-level Makefile. Here is mine:
```

LEVEL = .
DIRS = tests tools
EXTRA_DIST = include

# flags
ENABLE_OPTIMIZED = 1
DISABLE_ASSERTIONS = 1

include $(LEVEL)/Makefile.common

```

Now you'll need to tweak Makefile.common. Here's mine:
```

# Set the name of the project here
PROJECT_NAME := foo
PROJ_VERSION := 0.01
 
# Set this variable to the top of the LLVM source tree.
LLVM_SRC_ROOT = /home/vk/Projects/llvm-2.5

# Set this variable to the top level directory where LLVM was built
# (this is *not* the same as OBJ_ROOT as defined in LLVM's Makefile.config).
LLVM_OBJ_ROOT = /home/vk/Projects/llvm-2.5

# Set the directory root of this project's source files
PROJ_SRC_ROOT := $(subst //,/,/home/vk/Projects/foo)

# Set the root directory of this project's object files
PROJ_OBJ_ROOT := $(subst //,/,@abs_top_objdir@)

# Set the root directory of this project's install prefix
PROJ_INSTALL_ROOT := /usr/local

# Include LLVM's Master Makefile.
include $(LLVM_OBJ_ROOT)/Makefile.common

```

Now you'll need to regenerate the configure scripts for your project. The script doesn't work AT ALL on Ubuntu.. so we'll hack it! First, do this:
> 
sudo apt-get install automake autoconf2.59


Now, open autoconf/AutoRegen.sh with an editor (anything but emacs will do nicely). After the "die" function declaration, add this:
```

alias autoconf='autoconf2.59'
alias aclocal='aclocal-1.9'

```

Now, delete everything after the line "cwd=`pwd`" until the line "# Patch the LLVM_ROOT in configure.ac, if it needs it". Add this in its place:
```

llvm_src_root="/home/vk/Projects/llvm-2.5" # replace with wherever it is
llvm_m4="$llvm_src_root/autoconf/m4"
llvm_obj_root=$llvm_src_root

```

Now you can run this script.

At this point, you can lookup flags you need for the various makefiles you will have. If everything went well, you should be able to say "make" at your project root and have everything compile.

Here are some useful documents:
1) [http://llvm.org/docs/MakefileGuide.html](http://llvm.org/docs/MakefileGuide.html)
2) [http://llvm.org/docs/Projects.html](http://llvm.org/docs/Projects.html)
3) [http://llvm.org/docs/GettingStarted.html](http://llvm.org/docs/GettingStarted.html)

edit:
this guide should still apply for the svn version of llvm.

---

### Post by DubbaEwwTeeEff on 2009-10-18
I hate to bump a months-old thread as my first post, but this is the only place I've found a decent guide on LLVM projects, and I have a few questions about it.

First off, you say to copy Makefile.common, Makefile.common.in, configure, and config.status from the LLVM source root to my project directory.  Do you mean I should put them in the copied sample folder?  Or do you mean the folder that I copied the sample folder into?  Also, I can't seem to find all the files in the source root - Makefile.common, configure, and config.status are all in my LLVM folder but I can't find a Makefile.common.in; the closest in that folder is a Makefile.config.in.  And I can't find anything in the LLVM documentation that says to copy those files - is it something you had to figure out for yourself to get it working, or what?

Second - your configure.ac is confusing me slightly. Is "/home/**/Projects/llvm-2.5" your LLVM source directory, or where you're putting your projects?  I thought you were supposed to point it to the source directory but your path is confusing me.

Third - I made some guesses about the previous two questions and tried to run the makefile to compile the sample program.  It worked most of the way through, but it couldn't find the sample.h file.  I included one of the headers from the LLVM source and that went through find, but it can't seem to locate anything in the project's include folder.  How do I get it to check both the LLVM include folder and the project include folder?

As an aside: For anybody else trying to compile the sample project, rename "main.c" to "main.cpp" to save yourself a lot of trouble.  There's probably some other way to do it, but I couldn't get it to interpret the file as C++ without the suffix change.  That took care of a bunch of compile warnings and errors.


EDIT: After reviewing the makefile a bit more, my third question no longer applies - it's actually finding the sample.h file.  The actual error I'm getting is "main.cpp:(.text+0xa): undefined reference to `compute_sample(int)'".  I assumed it wasn't finding it because the header wasn't being included, but there's no corresponding error for not being able to find it.  Anyone have any ideas why it still wouldn't find the function?

---

### Post by manualqr on 2009-11-05
Firstly, sorry for the late reply.

I've completely given up on trying to get this thing working completely. It's .. a strange beast, and I can't tame all of its quirks. Progress happens too fast on llvm.

My best suggestion to you is to use llvm-config. It's not pretty, but neither is this.

```

# stolen from here: http://llvm.org/docs/tutorial/LangImpl7.html

# Compile
g++ -g toy.cpp `llvm-config --cppflags --ldflags --libs core jit native` -O3 -o toy
# Run
./toy

```

When I last tried compiling Chris Lattner's toy, it segfaulted every time I ran a command. To be fair, I was using svn code and had to tweak toy.cpp in unhealthy ways to get it to compile. And that was a few months ago.

edit:
oh, and good luck with whatever it is you're trying to do :)

---

### Post by ukblacknight on 2010-08-25
I hate to ask stupid questions, but where is llvm/projects/sample ?

---

### Post by LoveDub on 2011-05-13
> **ukblacknight said:**
> I hate to ask stupid questions, but where is llvm/projects/sample ?

In case you're tracking this, the answer is:

```

apt-get install llvm-2.8-source
cd /usr/src/llvm-2.8/
sudo tar xJf llvm-2.8.tar.xz
cd llvm-2.8/
ls projects/sample/

```

YMMV... but you get the idea. :)

---

