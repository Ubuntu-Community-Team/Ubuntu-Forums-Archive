---
title: "Problem installing from source..."
date: 2012-05-04
forum: Packaging and Compiling Programs
---

### Post by Nixarter on 2012-05-04
I'm trying to install Luminance HDR.

I've downloaded the source tar.gz file.  I navigate to the folder and type qmake (in terminal)... and nothing. it gives me what looks like the man page for qmake.  What am I doing wrong?  

I followed instructions here: [http://www.jonespcrepair.com/site4/2011/11/04/install-luminance-hdr-on-ubuntu-11-10/](http://www.jonespcrepair.com/site4/2011/11/04/install-luminance-hdr-on-ubuntu-11-10/)

please help!

---

### Post by beboylips on 2012-05-04
Post the commands you're typing and the output that is given

---

### Post by Rodney9 on 2012-05-04
You can get easily with Get Deb - 

[http://www.getdeb.net/software/Luminance](http://www.getdeb.net/software/Luminance)

Rodney

---

### Post by Nixarter on 2012-05-04
getdeb loaded USC and USC said it wasn't found.

as for the terminal:

```
ubuntu@ubuntu:~/Desktop/luminance-hdr-2.3.0.beta1$ qmake
Usage: qmake [mode] [options] [files]

QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
  -project       Put qmake into project file generation mode
                 In this mode qmake interprets files as files to
                 be built,
                 defaults to *.c; *.ui; *.y; *.l; *.ts; *.xlf; *.qrc; *.h; *.hpp; *.hh; *.hxx; *.H; *.cpp; *.cc; *.cxx; *.C
                 Note: The created .pro file probably will 
                 need to be edited. For example add the QT variable to 
                 specify what modules are required.
  -makefile      Put qmake into makefile generation mode (default)
                 In this mode qmake interprets files as project files to
                 be processed, if skipped qmake will try to find a project
                 file in your current working directory

Warnings Options:
  -Wnone         Turn off all warnings; specific ones may be re-enabled by
                 later -W options
  -Wall          Turn on all warnings
  -Wparser       Turn on parser warnings
  -Wlogic        Turn on logic warnings (on by default)
  -Wdeprecated   Turn on deprecation warnings (on by default)

Options:
   * You can place any variable assignment in options and it will be     *
   * processed as if it was in [files]. These assignments will be parsed *
   * before [files].                                                     *
  -o file        Write output to file
  -d             Increase debug level
  -t templ       Overrides TEMPLATE as templ
  -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
  -help          This help
  -v             Version information
  -after         All variable assignments after this will be
                 parsed after [files]
  -norecursive   Don't do a recursive search
  -recursive     Do a recursive search
  -set <prop> <value> Set persistent property
  -query <prop>  Query persistent property. Show all if <prop> is empty.
  -cache file    Use file as cache           [makefile mode only]
  -spec spec     Use spec as QMAKESPEC       [makefile mode only]
  -nocache       Don't use a cache file      [makefile mode only]
  -nodepend      Don't generate dependencies [makefile mode only]
  -nomoc         Don't generate moc targets  [makefile mode only]
  -nopwd         Don't look for files in pwd [project mode only]
ubuntu@ubuntu:~/Desktop/luminance-hdr-2.3.0.beta1$ 
```

before that:
```
ubuntu@ubuntu:~/Desktop/luminance-hdr-2.3.0.beta1$ sudo apt-get install qt4-qmake libexiv2-dev libopenexr-dev fftw3-dev libtiff4-dev libqt4-dev g++ libgsl0-dev libraw-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libfftw3-dev' instead of 'fftw3-dev'
g++ is already the newest version.
libexiv2-dev is already the newest version.
libfftw3-dev is already the newest version.
libgsl0-dev is already the newest version.
libopenexr-dev is already the newest version.
libqt4-dev is already the newest version.
libtiff4-dev is already the newest version.
qt4-qmake is already the newest version.
The following extra packages will be installed:
  liblcms1-dev
The following NEW packages will be installed:
  liblcms1-dev libraw-dev
0 upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
Need to get 554 kB of archives.
After this operation, 2,028 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main liblcms1-dev i386 1.19.dfsg-1ubuntu2 [201 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libraw-dev i386 0.13.8-0ubuntu1 [352 kB]
Fetched 554 kB in 1s (308 kB/s)     
Selecting previously deselected package liblcms1-dev.
(Reading database ... 286557 files and directories currently installed.)
Unpacking liblcms1-dev (from .../liblcms1-dev_1.19.dfsg-1ubuntu2_i386.deb) ...
Selecting previously deselected package libraw-dev.
Unpacking libraw-dev (from .../libraw-dev_0.13.8-0ubuntu1_i386.deb) ...
Setting up liblcms1-dev (1.19.dfsg-1ubuntu2) ...
Setting up libraw-dev (0.13.8-0ubuntu1) ...

```

So, once dependencies are installed, the next step is to type qmake, right?  What did I miss?

---

### Post by oldos2er on 2012-05-04
Moved to Packaging and Compiling Programs.

---

### Post by dckirba on 2012-05-31
Facing the same problem. I don't know what the right qmake options to use are. 

However, I did look at the INSTALL file included with the source files and it says to use cmake:

> 1. Basic compilation
------------------------------------------------------------------- 
To compile from source, first execute from an EMPTY folder the command:
> cmake <luminance source code directory>
to generate the Makefile. We strongly suggest to use an EMPTY folder OUTSIDE of the source directory.

It is also possible to generate specific project files for well known IDE (Visual Studio, Xcode and so on). Please, refer to CMake's manual for all the available options.
CMake will also check whether all the dependecies are available or not, and it will show a message accordingly.

Then execute the command:
> make
to compile the source code.

Finally execute (as root) the command:
> make install
to install the luminance executable in /usr/local/bin (if not differently specified during the configuration command).
This last step also installs the icon, the desktop file, the html documentation and the "qm" translation files. This last step is usually required in order for Luminance HDR to locate the "qm" files used for internationalization.


I tried this but I get a cmake error:
```
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
```

This is followed by the variable LCMS_INCLUDE_DIR (ADVANCED) and a long list of directories.

I'm not a programmer and I'm a bit clueless about my next step too :) Let me know if you figured it out.

UPDATE:
The folks on the Luminance Facebook page were helpful. Here's what you need to do:

1. You've already installed most of the dependencies. You now need to install cmake, liblcms1-dev and libpng12-dev

The following instructions are from the INSTALL file in the source directory:

1. Create an empty directory and point your terminal to it
2. Then type:
```
cmake <luminance source code directory>
```
3. Type make
4. Type sudo make install
5. reboot your machine

Should work fine on Ubuntu 12.04

---

