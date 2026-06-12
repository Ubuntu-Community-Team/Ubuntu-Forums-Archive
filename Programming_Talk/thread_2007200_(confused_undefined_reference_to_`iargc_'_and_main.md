---
title: ":(:confused: undefined reference to `iargc_' and main!"
date: 2012-06-20
forum: Programming Talk
---

### Post by nigel332 on 2012-06-20
hi,all
   I have got some problems with the compile of my code.
I type "./configure" to get makefile for the program,then I type "make",
But I got the message:

qingjie@qingjie-P5Q-DELUXE:~/study/try/pegasus5.1k3/tools$ make
cc  -lm  peg_diag.s   -o peg_diag
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld return 1
make: *** [peg_diag] mistake 1


First: I use gfortran-4.4 as the compiler,but, why the message shows cc instead of gfortran?
Then: what could i do to solve the problem?

More: when I type "make" in the directory named "tools"  I got some massage as follows:
qingjie@qingjie-P5Q-DELUXE:~/study/try/pegasus5.1k3/tools$ make
cc  -lm  peg_diag.s   -o peg_diag
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld return 1
make: *** [peg_diag] mistake 1

I  am puzzled about this, and donot know what can I do~~

help me with the problem please!:eek:

fOLLOWS ARE THE MAKEFILE I USED:
```

F90 = 		gfortran-4.4
F90FLAGS = 	-O2
CPP = 		gcc-4.4 -E
CPPFLAGS = 	-DLINUX -DD_PRECISION
LDFLAGS = 	-lm
LIBS = 		
CMPLFLAGS = 	linux


```

---

### Post by Arndt on 2012-06-20
> **nigel332 said:**
> hi,all
   I have got some problems with the compile of my code.
I type "./configure" to get makefile for the program,then I type "make",
But I got the message:

qingjie@qingjie-P5Q-DELUXE:~/study/try/pegasus5.1k3/tools$ make
cc  -lm  peg_diag.s   -o peg_diag
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld return 1
make: *** [peg_diag] mistake 1


First: I use gfortran-4.4 as the compiler,but, why the message shows cc instead of gfortran?
Then: what could i do to solve the problem?

More: when I type "make" in the directory named "tools"  I got some massage as follows:
qingjie@qingjie-P5Q-DELUXE:~/study/try/pegasus5.1k3/tools$ make
cc  -lm  peg_diag.s   -o peg_diag
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld return 1
make: *** [peg_diag] mistake 1

I  am puzzled about this, and donot know what can I do~~

help me with the problem please!:eek:

fOLLOWS ARE THE MAKEFILE I USED:
```

F90 = 		gfortran-4.4
F90FLAGS = 	-O2
CPP = 		gcc-4.4 -E
CPPFLAGS = 	-DLINUX -DD_PRECISION
LDFLAGS = 	-lm
LIBS = 		
CMPLFLAGS = 	linux
#
#    Where executables will be installed
#
INSTALLDIR =	/home/XD/study/try

.SUFFIXES:	.F90 .f90 .F .f

CMD = 		update

SRCDIR  =	.

INCLUDES =      ../include

RM =		/bin/rm -f

SHELL=		/bin/sh

#
PGM =		cmpxint		\
		p3d2peg		\
                mesh_lister	\
		peg_diag	\
		peg_hole	\
		peg_hole_surf	\
                peg_iboverd	\
                peg_in		\
                peg_mem		\
		peg_orph	\
		peg_plot	\
		peg_proj        \
		peg_setup       \
                XINtegrity	\
                XIN2sp

#
# List of scripts for installation
#
SCRIPTS = 	clean_holes \
		make_WORK

all:		$(CMD)

help:
		@echo
		@echo "Usage:"
		@echo "  type 'make [CMD=<COMMAND>] [PGM=<PROGRAM>]'"
		@echo
		@echo "  where <COMMAND> (optional) is one of the following:"
		@echo "	update (Default) compile everything that needs updating"
		@echo "	install		 compile, try to create $(INSTALLDIR) then put"
		@echo "			 executables there"
		@echo "	deinstall	 remove executables from $(INSTALLDIR)"
		@echo "	clean		 remove intermediate files"
		@echo "	clobber		 remove intermediate files, executables"
		@echo "                  and compiled libraries"
		@echo " "
		@echo "  where <PROGRAM> (optional) restricts compilation to"
		@echo "  any of the following:"
		@echo "	$(PGM) (Default is all)"
		@echo

bin:
		if(test -d $(INSTALLDIR)) then (:) else (mkdir $(INSTALLDIR)) fi

clean:		
		-for FILE in $(PGM) ; do $(RM) $(SRCDIR)/$$FILE.f90 \
		$(SRCDIR)/$$FILE.o ; done
		-($(RM) *.o *.f90 *.mod)

clobber:	clean
		-for FILE in $(PGM) ; do $(RM) $(SRCDIR)/$$FILE ; done
		-($(RM) peg_setup)

deinstall:
		-(cd $(INSTALLDIR);     $(RM) $(PGM))
		-(cd $(INSTALLDIR);	$(RM) $(SCRIPTS))

install:	update bin move

move:
		@echo ""
		@echo "Installing peg tools in $(INSTALLDIR) directory."
		@echo ""
		-for FILE in $(PGM) ; \
			do mv -f $(SRCDIR)/$$FILE $(INSTALLDIR) ; done
		-for FILE in $(SCRIPTS) ; \
			do cp -f $(SRCDIR)/$$FILE $(INSTALLDIR) ; done

update:		$(PGM)

peg_hole_surf:	mod_load_x.o mod_input.o mod_bc.o mod_hcut.o peg_hole_surf.o 
	$(F90) $(F90FLAGS) -o peg_hole_surf peg_hole_surf.o \
	mod_input.o mod_load_x.o mod_bc.o mod_hcut.o $(LDFLAGS) $(LIBS)

peg_mem:	mod_load_x.o mod_input.o mod_hcut.o peg_mem.o
	$(F90) $(F90FLAGS) -o peg_mem peg_mem.o mod_input.o mod_load_x.o \
	mod_hcut.o $(LDFLAGS) $(LIBS)

peg_plot:	mod_load_x.o peg_plot.o
	$(F90) $(F90FLAGS) -o peg_plot peg_plot.o mod_load_x.o \
	$(LDFLAGS) $(LIBS)

peg_hole:	mod_load_x.o peg_hole.o
	$(F90) $(F90FLAGS) -o peg_hole peg_hole.o mod_load_x.o \
	$(LDFLAGS) $(LIBS)

peg_proj:	mod_project.o mod_load_x.o peg_proj.o
	$(F90) $(F90FLAGS) -o peg_proj peg_proj.o mod_load_x.o \
	mod_project.o $(LDFLAGS) $(LIBS)

peg_iboverd:	mod_load_x.o peg_iboverd.o
	$(F90) $(F90FLAGS) -o peg_iboverd peg_iboverd.o mod_load_x.o \
	$(LDFLAGS) $(LIBS)

peg_in:	mod_input.o peg_in.o
	$(F90) $(F90FLAGS) -o peg_in peg_in.o mod_input.o \
	$(LDFLAGS) $(LIBS)

mesh_lister:	mod_input.o mesh_lister.o
	$(F90) $(F90FLAGS) -o mesh_lister mesh_lister.o mod_input.o \
	$(LDFLAGS) $(LIBS)

XINtegrity:	mod_project.o mod_load_x.o XINtegrity.o 
	$(F90) $(F90FLAGS) -o XINtegrity XINtegrity.o mod_load_x.o \
	mod_project.o $(LDFLAGS) $(LIBS)

peg_setup:	peg_setup.org
	@echo "Editing peg_setup to use $(INSTALLDIR)"
	echo "%s,@PEGINSTALLDIR@,$(INSTALLDIR)" > tmp.ex
	echo "w! peg_setup" >> tmp.ex
	echo "q" >> tmp.ex
	ex peg_setup.org < tmp.ex
	chmod +x peg_setup
	$(RM) tmp.ex


.F90.f90:
	$(CPP) $(CPPFLAGS) -I$(INCLUDES) -P -C	$*.F90	>	$*.f90

.F90.o:
	$(CPP) $(CPPFLAGS) -I$(INCLUDES) -P -C	$*.F90	>	$*.f90
	$(F90) $(F90FLAGS) -c	$*.f90
#	$(RM) $*.f90

.f90.o:
	$(F90) $(F90FLAGS) -c	$*.f90

.F90:
	$(CPP) $(CPPFLAGS) -I$(INCLUDES) -P -C	$*.F90	>	$*.f90
	$(F90) $(F90FLAGS)	-o $*	$*.f90 $(LDFLAGS) $(LIBS)
#	$(RM) $*.f90

.f90:
	$(F90) $(F90FLAGS)	-o $*	$*.f90 $(LDFLAGS) $(LIBS)

#
.F.f:
	$(CPP) $(CPPFLAGS) -I$(INCLUDES) -P -C  $*.F    >       $*.f

.F.o:
	$(CPP) $(CPPFLAGS) -I$(INCLUDES) -P -C  $*.F    >       $*.f
	$(F90) $(F90FLAGS) -c   $*.f
#	$(RM) $*.f

.f.o:
	$(F90) $(F90FLAGS) -c   $*.f

.F:
	$(CPP) $(CPPFLAGS) -I$(INCLUDES) -P -C  $*.F    >       $*.f
	$(F90) $(F90FLAGS)      -o $*   $*.f $(LDFLAGS) $(LIBS)
#	$(RM) $*.f

.f:
	$(F90) $(F90FLAGS)      -o $*   $*.f $(LDFLAGS) $(LIBS)


```

Fortran doesn't seem to be involved so far. .s is assembly code. What does peg_diag.s contain?

---

### Post by MadCow108 on 2012-06-20
-lm belongs into LIBS not LDFLAGS (but thats not related to this issue)

if that .s file does not contain a main it must be compiled with -c or -shared

---

