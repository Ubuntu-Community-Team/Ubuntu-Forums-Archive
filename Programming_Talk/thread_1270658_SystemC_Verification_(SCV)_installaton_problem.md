---
title: "SystemC Verification (SCV) installaton problem"
date: 2009-09-19
forum: Programming Talk
---

### Post by asm_cr on 2009-09-19
I've been trying to install the SCV library in Ubuntu 8.04 
I follow the instructions  in the INSTALL file step by step: 

 > To install SCV on a UNIX system, do the following steps:

  1. Change to the top level directory (scv)

  2. Create a temporary directory, e.g.,

        > mkdir objdir

  2a.For gcc 3.4.x and 4.x.x. minor changes are required to the configure file:
     Line 5642:  replace "#include <strstream.h>" with "#include <sstream>"
     Line 5654:  replace "ostrstream outString(buf,STRING_SIZE);" with
                 "std:: ostringstream outString;"
  
  3. Change to the temporary directory, e.g.,

        > cd objdir

  4. Set the following environment variable(s):

     For gcc on Solaris:

        > setenv CXX g++
        > setenv CC gcc

     For gcc on Linux (csh):

        > setenv CXX g++
        > setenv CC gcc

     For gcc on Linux (bash):

        > export CXX=g++
        > export CC=gcc

     For aCC on HP-UX:

        > setenv CXX aCC
        > setenv CC cc

     You can also specify an absolute path to the compiler of your choice.
     

  5. Configure the package for your system, e.g.,
     (The configure script is explained below.)

        > ../configure --with-systemc=<path_to_SystemC>

     While the 'configure' script is running, which takes a few moments, 
     it prints messages to inform you of the features it is checking.
     It also detects the platform.

     If you do not specify the path to a SystemC installation, 
     configure will look in ../systemc. So, if your SystemC and SCV
     packages are located at the same root directory, you do not need
     to specify the --with-systemc option.

     If you do specify the path to a SystemC installation, use an absolute 
     path (one starting with "/"), and do not use wildcards.

     Do not put spaces in around the "=" in the "--with-systemc=" option or
     in other configure options.

     If you want to install SCV using a compiler other than the ones we have 
     fully tested, you will need to specify the --disable-compiler-check 
     option.

     The command above instructs configure to install SCV in the same directory 
     as the SystemC installation.  If you want to install the package elsewhere,
     use the --prefix option, e.g. as follows:

        > ../configure --prefix=/usr/local/scv --with-systemc=/usr/local/systemc-2.2.0

     Note: make sure you have created the target directory before installing
           the package. Do _not_ use /usr/local as a prefix.

     Note for System V users: 
     If you are using `csh' on an older version of System V, you might 
     need to use the `sh ../configure' command instead of '../configure'.
     Otherwise, `csh' will attempt to `configure' itself.

  5a.For gcc 3.4.x and 4.x.x. an edit is required to the generated config.h file:
     Line 44: comment-out line, i.e. change to "//#define _USE_HASH_MAP
  
  [B]6. Compile the package.

        > gmake   (or gmake debug to build debug version of library)[/B]

     Some Solaris systems are unable to compile SCV with optimization
     enabled (which it is by default).  If you run into trouble, try
     configuring again with the "--disable-opt" option specified on
     the configure command line.

  7. Install the package.

        > gmake install

     This command will copy the SCV libraries, header files, documentation, and 
     examples directories into your SCV installation directory (this will be 
     your SystemC installation directory unless you used --prefix, as mentioned
     in #5 above).   This means that you must have write permissions into the 
     SCV installation area. Once this step is successfully completed you will have 
     a complete SCV installation.

  8. You can now remove the temporary directory, .e.g,

        > cd ..
        > rm -rf objdir

     Alternatively, you can keep the temporary directory to later uninstall
     the package. To clean up the temporary directory, enter:

        > gmake clean

     To uninstall the package, enter:

        > gmake uninstall



Then when I was doing step 6 I get this error:

> ranlib libcudd.a
gmake[6]: se sale del directorio `/home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir/src/cudd/2.3.0/cudd'
../../../../scripts/copyFiles.sh -s . /home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir/lib libcudd.a 
/bin/sh: Illegal option -h
gmake[5]: *** [all] Error 2
gmake[5]: se sale del directorio `/home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir/src/cudd/2.3.0/cudd'
gmake[4]: *** [all-recursive] Error 1
gmake[4]: se sale del directorio `/home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir/src/cudd/2.3.0'
gmake[3]: *** [all-recursive] Error 1
gmake[3]: se sale del directorio `/home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir/src/cudd'
gmake[2]: *** [all-recursive] Error 1
gmake[2]: se sale del directorio `/home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir/src'
gmake[1]: *** [all-recursive] Error 1
gmake[1]: se sale del directorio `/home/adolfo/Documentos/Verificacion/scv-1.0p2-sysc2.2/objdir'
gmake: *** [all] Error 2


When you read
se sale del directorio = leaving directory.

I think the problem is this line that the gmake creates in all the scripts files.
/bin/sh: Illegal option -h

But I'm not sure.

By the way I made a simbolyc link to gmake to make

I hope you can help me and sorry for my bad English.

---

### Post by asm_cr on 2009-09-21
I asked about this issue in the OSCI Help Forum

They told me that the problem was that in Ubuntu the symlink /bin/sh pointed to /bin/dash instead of /bin/bash.
So I replaced /bin/sh by /bin/bash in the Makefiles  and I was able to compile the library.

---

