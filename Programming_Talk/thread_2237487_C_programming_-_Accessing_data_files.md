---
title: "C programming - Accessing data files"
date: 2014-08-02
forum: Programming Talk
---

### Post by neoxxx23 on 2014-08-02
Hi,

I'm a beginner in C programming and recently I've started using autotools for my tiny projects, because I wanted to know, how most sources made on the internet.
With autotools, I could compile and install my project, along with some data files, which go to /usr/local/share/<myprogram> directory. It's maybe a dumb question, but how do I need to code to access the data files from that folder, from any working directory? What if the user installs the program somewhere else?
```
gtk_builder_add_from_file(builder, "what/directory/here/ui.glade", NULL);
```
 So, regardless where I install my project to, and what directory I'm currently working in, I would like to be able to run my program from /usr/local/bin.
I also would like to be able to run the program accessing the files without installing it, to test the program from the source directory.

My configure.ac:
```
AC_INIT([Something-GTK], 0.1)
AM_INIT_AUTOMAKE
AC_CONFIG_FILES([Makefile])
AC_PROG_CC
PKG_CHECK_MODULES([GTK], [gtk+-3.0])
AC_OUTPUT
```
My Makefile.am:
```
bin_PROGRAMS = Something-GTK
Something_GTK_SOURCES = main.c
Something_GTK_CFLAGS = $(GTK_CFLAGS)
Something_GTK_LDADD = $(GTK_LIBS)
dist_pkgdata_DATA = ui.glade
```

Thank you for your help in advice!

---

### Post by TheFu on 2014-08-02
I've never used autotools for my projects - don't think this is specific to that.
What most projects do is create a config file with parameters which control where different parts of the program are located.
In the old days, we'd use 1 environment variable - PROJECT_HOME - as the setting, then assume that 
bin/
lib/
etc/
doc/
contrib/
db/
directories existed below that level. Relative.

Then the geniuses who did package management decided that programs should be installed in 1 place, settings in another and data still elsewhere - none of these under the same main directory, so having 1 setting per program wasn't possible anymore.  One of my first GNU contributions was to lookup were the ODBC settings file was on a system.
0) use command line option, if provided
1) check for an environment variable
2) look in the current user's HOME for .odbc
3) look in /etc/odbc.ini
4) go with defaults or die

So .... you could do the same sort of checking for where the data files are located, based on where they are most likely to be stored, until you decide to let the user place those anywhere and be controlled by a setting ... BTW - you should follow the order of where the config file is located above. It is the accepted standard way.

To me, where files are installed is purely a package management issue, not a build-tool choice. Does that make sense?

---

### Post by neoxxx23 on 2014-08-02
Thank you for the quick answer and for the idea!
I try to use the standards, but I would like to calculate with all cases and make my program more portable.

My problem is that I couldn't locate the executable itself, only the working directory. **Now I've found a solution for that**:
```
char self_location[300];
realpath("/proc/self/exe", self_location);
```
I can determine this way the program's directory so I can try a few directories relative to my program, and not my current working directory. This way I can continue editing my source without installing it (I can add another directory to try) and my program keeps being ready for weird configuration prefixes (I hope).

I mark the problem solved, thank you for your help!

---

### Post by TheFu on 2014-08-02
It is best to NOT code this into your C program. Do it in a startup script and use **basename** and **whence** to figure out where the program is installed. There are 100K example program startup scripts out there.  Heck, firefox uses one still.

BTW, never allocate a string with a fixed size that may not be big enough. 300 characters is NOT enough. There is a max file path limit for every installed kernel - it can be changed.  Best to use dynamic allocation based on the actual value returned.  strlen() will help you get the size.

---

### Post by ofnuts on 2014-08-02
This is Linux. The split of the configuration between /etc or /usr/share and the user's own directory is legitimate. 

Given he availability of links, it is also simpler to decide that things will always be in /usr/share/ and use links if they are placed elsewhere. This removes the need to write complex logic to support specific (and rare) setups.

---

### Post by neoxxx23 on 2014-08-05
> Do it in a startup script and use **basename** and **whence** to figure out where the program is installed.
Thank you, it sounds also useful! Next time I'll try to do the script thing. :)

---

