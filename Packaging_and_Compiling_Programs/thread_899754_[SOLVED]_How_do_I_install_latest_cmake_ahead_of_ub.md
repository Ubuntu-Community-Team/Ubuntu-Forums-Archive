---
title: "[SOLVED] How do I install latest cmake ahead of ubuntu?"
date: 2008-08-24
forum: Packaging and Compiling Programs
---

### Post by seaworthy4life on 2008-08-24
I end up extracting all of these files which certainly do not belong in my personal directory, unless maybe I move the cmake file into the /usr/bin/? and add it to some registry?  

> Building LMMS got quite simple since 0.4.0 as everything is managed
by cmake now. Therefore make sure you have CMake (>= 2.6.0 recommended) and
then run


mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install

It looks like I may only have to do this one thing, unless cmake will require access to its parent directory.

Will this work?

---

### Post by seaworthy4life on 2008-08-24
I tried that but now it is asking me to make a cmake root.  It is also asking for a modules directory in usr/bin which is easy, but ...:lolflag:

---

### Post by seaworthy4life on 2008-08-24
According to qmake, I can probably do one of two things.  

1.  Download an .sh file, run it with /bin/sh and follow the instructions.  (What kind of command line would you use to run this and what directory would the sh file have to be in?)

2.  Untare a regular tar file, but in which directory, as it won't work in the personal directory and the untarred package gives you four parent directories - bin, share, man, and doc.

---

### Post by seaworthy4life on 2008-08-24
Ok. I copied the .sh file to the root. Then, I thought this would work when I ran this line.

justin@justin-desktop:~$ sudo chmod +x /cmake-2.6.1-Linux-i386.sh

Next thing is that I am supposed to get this shell or something like ./cmake-2.6.1-Linux-i386.sh , but it is not happening. Not sure where to go from here.

I think that maybe the script is missing the proper "shebang line" at the beginning.

---

### Post by seaworthy4life on 2008-08-24
voila, the shebang line, justin@justin-desktop:~$ sudo sh /cmake-2.6.1-Linux-i386.sh , and it ends up putting it in your personal box.

---

### Post by seaworthy4life on 2008-08-24
... but it did not register cmake correctly, so I would need to figure out how to utilize these 4 directories of qmake LOCKED in my personal box for the qmake lmms to work properly.

This is the wall that I am at.

> justin@justin-desktop:~/Desktop/LMMS/lmms-0.4.0-beta2/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
CMake Error: Could not find CMAKE_ROOT !!!
CMake has most likely not been installed correctly.
Modules directory not found in
/usr/bin
CMake Error: Error executing cmake::LoadCache(). Aborting.


---

### Post by seaworthy4life on 2008-08-25
Success.

So I moved cmake-2.6.1-Linux-i386.sh into /usr/ .  Then I performed sh /usr/cmake-2.6.1-Linux-i386.sh , if I remember right.  

Now it's there and installed correctly.  When I type cmake and hit enter, I get an about cmake listing.  At the very first of the listing, it calls version 2.6.1 a patch and when I go to Synaptic, the installed version is still listed as version 2.47.  Looks like it should work to compile the latest LMMS once all of the dependencies are downloaded.


> 
justin@justin-desktop:~$ cmake


cmake version 2.6-patch 1
Usage

  cmake [options] <path-to-source>
  cmake [options] <path-to-existing-build>

Options
  -C <initial-cache>          = Pre-load a script to populate the cache.
  -D <var>:<type>=<value>     = Create a cmake cache entry.
  -U <globbing_expr>          = Remove matching entries from CMake cache.
  -G <generator-name>         = Specify a makefile generator.
  -Wno-dev                    = Suppress developer warnings.
  -Wdev                       = Enable developer warnings.
  -E                          = CMake command mode.
  -i                          = Run in wizard mode.
  -L[A][H]                    = List non-advanced cached variables.
  -N                          = View mode only.
  -P <file>                   = Process script mode.
  --graphviz=[file]           = Generate graphviz of dependencies.
  --system-information [file] = Dump information about this system.
  --debug-trycompile          = Do not delete the try compile directories..
  --debug-output              = Put cmake in a debug mode.
  --help-command cmd [file]   = Print help for a single command and exit.
  --help-command-list [file]  = List available listfile commands and exit.
  --help-commands [file]      = Print help for all commands and exit.
  --help-compatcommands [file]= Print help for compatibility commands.
  --help-module module [file] = Print help for a single module and exit.
  --help-module-list [file]   = List available modules and exit.
  --help-modules [file]       = Print help for all modules and exit.
  --help-custom-modules [file]= Print help for all custom modules and exit.
  --help-policy cmp [file]    = Print help for a single policy and exit.
  --help-policies [file]      = Print help for all policies and exit.
  --help-property prop [file] = Print help for a single property and exit.
  --help-property-list [file] = List available properties and exit.
  --help-properties [file]    = Print help for all properties and exit.
  --help-variable var [file]  = Print help for a single variable and exit.
  --help-variable-list [file] = List documented variables and exit.
  --help-variables [file]     = Print help for all variables and exit.
  --copyright [file]          = Print the CMake copyright and exit.
  --help                      = Print usage information and exit.
  --help-full [file]          = Print full help and exit.
  --help-html [file]          = Print full help in HTML format.
  --help-man [file]           = Print full help as a UNIX man page and exit.
  --version [file]            = Show program name/version banner and exit.

Generators

The following generators are available on this platform:
  Unix Makefiles              = Generates standard UNIX makefiles.
  CodeBlocks - Unix Makefiles = Generates CodeBlocks project files.
  Eclipse CDT4 - Unix Makefiles
                              = Generates Eclipse CDT 4.0 project files.
  KDevelop3                   = Generates KDevelop 3 project files.
  KDevelop3 - Unix Makefiles  = Generates KDevelop 3 project files.

justin@justin-desktop:~$                                               

---

### Post by seaworthy4life on 2008-08-25
It's also possible that by installing a bunch of QT, QT3, and QT4 develop files, I somehow got cmake updated to its current version, somehow without Synaptic being aware of it.

---

