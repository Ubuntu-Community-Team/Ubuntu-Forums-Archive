---
title: "using a makefile"
date: 2012-10-26
forum: Programming Talk
---

### Post by orrymr on 2012-10-26
Hi,

I just downloaded the codebase for a MUD (an old mutliplayer text based game) and I'm trying to get it to work. 

There's a readme which says that I must do the following: 
```

(3) Go into the 'src' directory.  Choose the Makefile for your operating
    system and copy it into 'Makefile':

	Makefile	Most machines with 'gcc'
	Makefile.aix	AIX
	Makefile.hp	Hp/UX
	Makefile.isc	Interactive Systems Unix
	Makefile.mip	Mips Risc/OS
	Makefile.nex	NeXT
	Makefile.sol	SunSoft Solaris 2.1
	Makefile.tra	Traditional C (see 'trad.txt')

    Merc.exe, a pre-built MsDos executable, is included in the release.
    See 'port.txt' for more information on porting, including the
    single-user MsDos and Macintosh versions.

(4) Run 'make' with the following options:

	make -k >&! make.out

```

I have no idea what point (3) means, as there is only one file called "Makefile" in the src directory.. When I do run the command, a file named ! is created with the following contents: 
make: *** No rule to make target `make.out'.

Any help would be greatly appreciated :)

---

### Post by MG&amp;TL on 2012-10-26
Point 3: I imagine you should just ignore it. Often coders will forget about READMEs when they update stuff.

Point 4: They've somehow managed to muck up the bash script for that: they mean to redirect all output to a file *make.out* and fail miserably. Just run *make* and be done with it. :) EDIT: My bad, this is what csh jokingly calls redirection. :P

---

### Post by orrymr on 2012-10-26
when I do that I get a torrent of errors:
```

gcc -c -Wall -O -g  act_comm.c
In file included from act_comm.c:46:0:
tables.h:36:31: error: array type has incomplete element type
tables.h:37:35: error: array type has incomplete element type
tables.h:38:30: error: array type has incomplete element type
tables.h:39:31: error: array type has incomplete element type
tables.h:42:31: error: array type has incomplete element type
tables.h:43:31: error: array type has incomplete element type
tables.h:44:31: error: array type has incomplete element type
tables.h:45:31: error: array type has incomplete element type
tables.h:46:31: error: array type has incomplete element type
tables.h:47:31: error: array type has incomplete element type
tables.h:48:31: error: array type has incomplete element type
tables.h:49:31: error: array type has incomplete element type
tables.h:50:31: error: array type has incomplete element type
tables.h:51:31: error: array type has incomplete element type
tables.h:52:31: error: array type has incomplete element type
tables.h:53:31: error: array type has incomplete element type
tables.h:54:31: error: array type has incomplete element type
tables.h:55:31: error: array type has incomplete element type
tables.h:56:31: error: array type has incomplete element type
tables.h:57:31: error: array type has incomplete element type
tables.h:58:31: error: array type has incomplete element type
tables.h:59:31: error: array type has incomplete element type
tables.h:60:31: error: array type has incomplete element type
tables.h:61:31: error: array type has incomplete element type
act_comm.c: In function ‘do_grats’:
act_comm.c:672:10: warning: variable ‘bufz’ set but not used [-Wunused-but-set-variable]
act_comm.c:671:10: warning: variable ‘bufy’ set but not used [-Wunused-but-set-variable]
make: *** [act_comm.o] Error 1

```

---

### Post by dwhitney67 on 2012-10-26
> **orrymr said:**
> when I do that I get a torrent of errors:


You indicated in your opening post that you are attempting to get the MUD application to work.
> 
I just downloaded the codebase for a MUD (an old mutliplayer text based game) and I'm trying to get it to work. 


It appears that the source code contains syntax errors, which means that you are going to have to edit the source code (I suggest that you start with tables.h at line 36) to fix any/all errors indicated by the compiler.

If you do not know C (or C++), then you may have problems performing this task.

---

### Post by spjackson on 2012-10-26
> **dwhitney67 said:**
> 
It appears that the source code contains syntax errors, which means that you are going to have to edit the source code (I suggest that you start with tables.h at line 36) to fix any/all errors indicated by the compiler.

If you do not know C (or C++), then you may have problems performing this task.
Indeed. [Someone's already encountered this error]("http://www.gammon.com.au/forum/?id=9463"), fixed it and gone on to find further errors.

> 
make -k >&! make.out

That's csh syntax. csh was quite popular among programmers until bash came along and bashed up all the other shells.

---

