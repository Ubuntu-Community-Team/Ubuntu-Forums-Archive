---
title: "Setting the ACEDB_MACHINE variable? argument?"
date: 2006-05-30
forum: Programming Talk
---

### Post by frogotronic on 2006-05-30
Hello,

  Trying to compile a programme called FPC [http://www.agcol.arizona.edu/software/fpc/]("http://www.agcol.arizona.edu/software/fpc/") on Ubuntu Breezy Badger 5.10.  I've downloaded all the required libraries.  When I run the "make" command, I get the following errors from the makefile:

```
makefile:52: Extraneous text after `ifeq' directive
makefile:68: w/wmake/_DEF: No such file or directory
make: *** No rule to make target `w/wmake/_DEF'.  Stop.
```


Here's the code from the makefile.  I figure I have to substitute "ifeq" arguments to be UBUNTU specific.  

```
########### LINUX STUFF ##############
ifndef USE_IMLIB
Xt_LIBS = -lXaw -lXt -lXmu -lXext -lX11 -L./GTK -L/usr/X11/lib -L/usr/X11R6/lib \
         `gtk-config --libs` 
else
Xt_LIBS = -lXaw -lXt -lXmu -lXext -lX11 -L./GTK -L/usr/X11/lib -L/usr/X11R6/lib \
         `gtk-config --libs` `imlib-config --libs-gdk`
endif

GRAPH_DIR= w/bin.$(ACEDB_MACHINE)/
ACE_LIBS = $(GRAPH_DIR)/libgex.a $(GRAPH_DIR)/libgraph.a $(GRAPH_DIR)/libgif.a $(GRAPH_DIR)/libfree.a

FPC_LIBS=$(ACE_LIBS) $(Xt_LIBS) -lpthread -lposix4

ifeq ($(ACEDB_MACHINE),LINUX_4)
FPC_LIBS=$(ACE_LIBS) $(Xt_LIBS) -lpthread -lgdbm
endif

ifeq ($(ACEDB_MACHINE),DARWIN))
FPC_LIBS=$(ACE_LIBS) $(Xt_LIBS) -lpthread 
endif


ARCHIVES=clam/clam.a fpp/fpp.a file/file.a mtp/mtp.a bss/bss.a


FPC_OBJS=bin/fpp3main.o
FPCD_OBJS=clam/parallel/fpp3nomain.o clam/parallel/fpcd.o


#################################################################
########## Machine dependent compiler modification ##############
#################################################################

include w/wmake/$(ACEDB_MACHINE)_DEF


```

Here's the excerpt from the README file for the installation:

[B]To Install:

If the machine you are compiling on is running SOLARIS, execute
setenv ACEDB_MACHINE SOLARIS_4
or
setenv ACEDB_MACHINE SOLARIS_5 
for SOLARIS 5.8

Otherwise, see w/wmake and use one of the definitions, without the _DEF suffix.
For example, for linux, execute setenv ACEDB_MACHINE LINUX_4.

Execute 'make'.

Note:
Older machines may not have the GTK libraries installed on them.  
If you wish to run your FPC executable on such machines, you must 
link these libraries statically.
To do this, create a directory called 'GTK' in the FPC directory, 
and copy the library archives libgdk.a, libglib.a, libgmodule.a, and 
libgtk.a to this directory.  These libraries are usually found in 
/usr/local/lib.  The makefile will automatically detect
these libraries and use them instead of the dynamically linked ones.[/B]

(I have downloaded the GTK libraries, and installed them as well as copied the archives (specified in the README file) to a GTK folder in the FPC folder).

Is the ACEDB_MACHINE a variable definition?  If so, would something along the lines of:

```
setenv ACEDB_MACHINE LINUX_4
```

as specificied in the README file solve the problem?  What would be the specific variable setting for ACEDB_MACHINE in Ubuntu 5.10 BB?  Is it LINUX 4?

Thanks,
CH

---

