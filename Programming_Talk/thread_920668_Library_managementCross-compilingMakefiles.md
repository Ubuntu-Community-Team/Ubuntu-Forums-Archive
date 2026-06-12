---
title: "Library management/Cross-compiling/Makefiles"
date: 2008-09-15
forum: Programming Talk
---

### Post by Svenstaro on 2008-09-15
Hey everybody,

I decided to create one thread for all my questions as opposed to splitting them up, hopefully that works out. Please keep in mind that I did a decent amount of Google-fu before asking here but I simply lack the understanding of the context and Google doesn't help much there. So here we go, my main three issues that I'd like to know more about:

1. 
I'm curious: How do I PROPERLY manage libraries and headers in Linux/Ubuntu?
From what some Google-fu got me, there's something called pkg-config that keeps track of all that for me. 

Now let's suppose that I have a project that needs a certain library to compile and I want to compile the project using GCC, what would I do?

If I manually compile a library, how do I properly register it (and its header files of course) for usage in GCC/Make/an IDE like Code::Blocks? Can I also use a checkinstall here to make tracking of installed lib versions easier?

Does Ubuntu manage it the way most other Distro's do or does it use its own special way of handling libs and headers?

2.
Recently I ran into an issue where I had to cross compile a project. More specifically, I had a project in Code::Blocks in Windows which was supposed to compile with MinGW which worked fine. It then got ported to Ubuntu (still with Code::Blocks) and it still works fine with GCC. 
Now my question is: How do I compile this project without using an IDE? I guess this brings us to the last question.

3.
How do I properly set up makefiles considering the position I'm in (project already set up in Code::Blocks)? Can Cmake help me here? Can the autotools help me?


As you can see, all my problems are kind of related and I really hope you can give me some pointers in at least one aspect of my trouble so I can get started solving the rest.
It really isn't like I didn't Google enough :D

So yeah, any help would be highly appreciated.

---

### Post by kknd on 2008-09-15
Hi,

The starndard way to compile your application is to provide a build script (can be a plain Makefile, an autotools combo, a python script, whatever).

Some libraries installs *.pc files, for use with pkg-config. This is the case of gtk, so, to build a C program, you usually use pkg-config --cflags --libs gtk+-2.0 (usually you compile all the objects using cflags only, and only on linking you use the libs).

If you build a library and you want other people to link against it, then install the headers in /usr/include and the {static,shared} object in /usr/lib.

This is a just very simple overview, and there IS documentation on the web about this.

---

### Post by Svenstaro on 2008-09-16
Hey there, thanks for the answer.

I know that there is info on the web about most of my questions, I also studied most of it. I didn't really ask for an explanation of what the particular things are but how I can make them play together. The overall idea, if you will.

I'd appreciate it if my remaining questions could also be answered.

---

### Post by kknd on 2008-09-16
A short list of steps to make a common project (not ordered and not true =) )

* Write some code =)
* Create a build script (theres a lot of alternatives to prevent yo from requiring an specific IDE)
* On installation of libraries (in case of C/C++ etc. Python / Lua / Java have other ways), place your public headers on /usr/include (projects with more than one or two usually create a subfolder like /usr/include/myproject. That way, it can be included in any
program by doing a #include <myproject/main_header.h>.
* On installation of libraries, place your lib in /usr/lib (without subfolders). The name must be unique, and some people like to name the libraries with a version identifier (like libMYLIBNAME.sp.17) and using softlinks.
* For increased portability and some other things, a lot of projects use autotools. I don't like all the complexity of autotools.

Ubuntu manages libraries in the "standart" way (like Arch Linux, Debian, etc), ie, PATH contains /usr/bin, pkg-config searches for .pc in /usr/lib/pkgconfig, and etc.

I hope it helps.

---

