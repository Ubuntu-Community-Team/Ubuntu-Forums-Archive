---
title: "having trouble installing"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by fignig on 2008-05-24
so i'm trying to install thru the terminal. ran into a couple of problems.
it tells me to do the ./configure then sudo make, then sudo make install.

but every time i tried the sudo make, or the sudo make install command it keeps telling me it's a bad one. i looked in the install txt in the folder of the application and it says to do the same things i've already tried. i'm trying to install qtella, the p2p for linux, b/c for some reasons limewire pro will not work. so can anyone point out a good p2p or help me install this one?

---

### Post by TeoBigusGeekus on 2008-05-24
Post us the contents of the install txt to have a butcher's. 

The most popular p2p software in Ubuntu is amule, available in the repositories. But, have you ever tried using torrents?

---

### Post by fignig on 2008-05-24
> **TeoBigusGeekus said:**
> Post us the contents of the install txt to have a butcher's. 

The most popular p2p software in Ubuntu is amule, available in the repositories. But, have you ever tried using torrents?

Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  You can give `configure'
initial values for variables by setting them in the environment.  Using
a Bourne-compatible shell, you can do that on the command line like
this:
     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure

Or on systems that have the `env' program, you can do it like this:
     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not supports the `VPATH'
variable, you have to compile the package for one architecture at a time
in the source code directory.  After you have installed the package for
one architecture, use `make distclean' before reconfiguring for another
architecture.

Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PATH', the package will use
PATH as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=PATH' to specify different values for particular
kinds of files.  Run `configure --help' for a list of the directories
you can set and what kinds of files go in them.

   If the package supports it, you can cause programs to be installed
with an extra prefix or suffix on their names by giving `configure' the
option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.

Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

Specifying the System Type
==========================

   There may be some features `configure' can not figure out
automatically, but needs to determine by the type of host the package
will run on.  Usually `configure' can figure that out, but if it prints
a message saying it can not guess the host type, give it the
`--host=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name with three fields:
     CPU-COMPANY-SYSTEM

See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the host type.

   If you are building compiler tools for cross-compiling, you can also
use the `--target=TYPE' option to select the type of system they will
produce code for and the `--build=TYPE' option to select the type of
system on which you are compiling the package.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Operation Controls
==================

   `configure' recognizes the following options to control how it
operates.

`--cache-file=FILE'
     Use and save the results of the tests in FILE instead of
     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for
     debugging `configure'.

`--help'
     Print a summary of the options to `configure', and exit.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`--version'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`configure' also accepts some other, not widely useful, options.


there it is.

---

### Post by TeoBigusGeekus on 2008-05-24
> **fignig said:**
> 
but every time i tried the sudo make, or the sudo make install command it keeps telling me it's a bad one. 

Would you share with us the exact messages? Cause from what I read in the installation instructions it is a standard case of compilation.

---

### Post by fignig on 2008-05-24
> **TeoBigusGeekus said:**
> Would you share with us the exact messages? Cause from what I read in the installation instructions it is a standard case of compilation.

pete@pete:~/Desktop/qtella-0.7.0$ make
make: *** No targets specified and no makefile found.  Stop.
pete@pete:~/Desktop/qtella-0.7.0$ sudo make
[sudo] password for pete: 
make: *** No targets specified and no makefile found.  Stop.
pete@pete:~/Desktop/qtella-0.7.0$ sudo make install
make: *** No rule to make target `install'.  Stop.

---

### Post by TeoBigusGeekus on 2008-05-24
I suppose you do have the gcc and gcc-4.2 packages installed? You can check through synaptic.

EDIT:
If you don't
```
sudo apt-get install build-essential
```
and almost everything you need for programming will be installed

---

### Post by fignig on 2008-05-25
> **TeoBigusGeekus said:**
> I suppose you do have the gcc and gcc-4.2 packages installed? You can check through synaptic.

EDIT:
If you don't
```
sudo apt-get install build-essential
```
and almost everything you need for programming will be installed

pete@pete:~$ sudo apt-get install build-essential
[sudo] password for pete: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by fignig on 2008-05-27
does anyone actually know what to do? other than just lead me into nowhere....????????

---

### Post by fignig on 2008-05-30
anyone. plz?

---

### Post by rockerphil on 2008-05-30
i personally use FrostWire. it's not available through the reops, but you can download the .deb file from [http://www.frostwire.com](http://www.frostwire.com) then just open up your terminal and run this code


sudo dpkg -i frostwire-4.13.5.i586.deb

and just so you know FrostWire works exactly like LimeWire Pro and is based on a branch of LimeWire Pro's source code and is completely free. hope this helps

---

### Post by unutbu on 2008-05-30
I agree with 
rockerphil and TeoBigusGeekus that the easiest way out of this problem is to use a different p2p program which you can install using apt-get. However, if you want to enjoy the experience of compiling your own program, here are some tips that might help.

Ubuntu comes shipped with a symbolic link from /bin/sh to /bin/dash instead of /bin/bash.
Some scripts die because they use special bash commands even though they say they call /bin/sh.

The script fails, and it is the script-writer's fault, but Ubuntu's configuration causes the script-writer's problem to terrorize Ubuntu users who want to compile things. 

To avoid the problem, link sh to bash:
```
sudo ln -sf /bin/bash /bin/sh
``` 

This may or may not fix your problem, but has saved others from further hours of banging head against wall.

Next try doing 
```

./configure

``` again. 

Look for error messages. Post if you see any.
If it looks like it finished properly, check that a Makefile has been written:
```

ls -l Makefile
```

If you don't get a Makefile, there is no point in running make. This is the problem you are having when you get the error message
> 
pete@pete:~/Desktop/qtella-0.7.0$ make
make: *** No targets specified and no makefile found. Stop.

---

### Post by fignig on 2008-06-02
> **rockerphil said:**
> i personally use FrostWire. it's not available through the reops, but you can download the .deb file from [http://www.frostwire.com](http://www.frostwire.com) then just open up your terminal and run this code


sudo dpkg -i frostwire-4.13.5.i586.deb

and just so you know FrostWire works exactly like LimeWire Pro and is based on a branch of LimeWire Pro's source code and is completely free. hope this helps

pete@pete:~$ sudo dpkg -i frostwire-4.13.5.i586.deb
dpkg: error processing frostwire-4.13.5.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.13.5.i586.deb

is what happened when i tried that code. and ./configure and sudo make and sudo make install didn't work. any ideas?

---

### Post by avtolle on 2008-06-02
If you downloaded the deb file to your desktop, you will first need to ```
cd Desktop
``` at the CLI (terminal) then type the dpkg instruction as above. If you are in the same directory where the file is downloaded, then I'm clueless right now.

---

### Post by fignig on 2008-06-03
so i have the frostwire installed i believe. but it's not running. there's an icon under applications > internet > frostwire. but when i click it it doesn't run. nor does it run by running "frostwire" thru the run application gui.

---

### Post by fignig on 2008-06-07
> **fignig said:**
> so i have the frostwire installed i believe. but it's not running. there's an icon under applications > internet > frostwire. but when i click it it doesn't run. nor does it run by running "frostwire" thru the run application gui.

can anyone help me?

---

