---
title: "programming"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by iceking0011 on 2012-12-05
how to do C programming using Ubuntu without installing any software?

---

### Post by CaptainMark on 2012-12-05
You use your favourite text editor to write the code I recommend gedit and the compiler is GCC which is already included in ubuntu

---

### Post by squakie on 2012-12-05
You may need to install the build-essential package to get headers, the GCC compiler, etc..  You can sure do the programming as mentioned if that's what you really want to do.  I might suggest, however, you try one of the Integrated Development Environments you can download via synaptic or the software center (they are free).  I personally like CodeBlocks, but everyone has their own tastes.  You can use the built in debugger in these to view statements, break points, examine variales, etc..

---

### Post by Wim Sturkenboom on 2012-12-05
I think everything is there in 12.04 by default; so in that case there is no need to install extra stuff. Possibly in 10.04 as well, but not sure.

---

### Post by oldos2er on 2012-12-05
> **CaptainMark said:**
> You use your favourite text editor to write the code I recommend gedit and the compiler is GCC which is already included in ubuntu

I've always had to install build-essential on Ubuntu to get the basic compiler.

---

### Post by squakie on 2012-12-05
+1.  That's why I mentioned build-essential as well.  GCC, etc., and well as other needed things come in that meta package.  Glad I wasn't seeing something had changed! ;)

---

### Post by CaptainMark on 2012-12-06
Sorry its not my best topic I don't really use compiled languages (not sure if this is the correct term), I do have GCC installed though and I haven't exclusively installed it, that is the C compiler correct? I suppose it is not enough on its own to compile all programs, is that what you mean?

---

### Post by Wim Sturkenboom on 2012-12-06
> **oldos2er said:**
> I've always had to install build-essential on Ubuntu to get the basic compiler.

> **squakie said:**
> +1.  That's why I mentioned build-essential as well.  GCC, etc., and well as other needed things come in that meta package.  Glad I wasn't seeing something had changed! ;)

I don't have build-essential installed and I can compile (a simple helloworld) C code. According to the info in synaptic, you don't need it if you don't build DEB packages.

---

### Post by MG&amp;TL on 2012-12-06
According to /usr/share/build-essential/list:

> michael@michael-laptop:~$ cat /usr/share/build-essential/list
                   List of Build-Essential packages
                    as of 2010-03-14, Debian sid

This file lists the non-essential packages that are build-essential.
The list is not closed under the "depends on" relation, so one will
usually need to install more packages than given here.

This list attempts to document the set of build-essential packages as
well as possible.  However, it is not authoritative (actually, there
is no authoritative list at all); the definition of the
"build-essential" class of packages given in Debian Policy Manual
(version >= 3.6.1.1), section 4 "Source packages" (more precisely
subsection 4.2 "Package relationships") is the definitive answer.
Here's the definition (as of Policy 3.6.1.1):

    It is not necessary to explicitly specify build-time relationships
    on a minimal set of packages that are always needed to compile,
    link and put in a Debian package a standard "Hello World!" program
    written in C or C++.  The required packages are called
    _build-essential_, and an informational list can be found in
    `/usr/share/doc/build-essential/list' (which is contained in the
    `build-essential' package).

The list is given below in a format which is readable by both humans and
programs.  The format is described at the end of this file.

BEGIN LIST OF PACKAGES
libc6-dev [!alpha !ia64 !hurd-i386] | libc0.3-dev [hurd-i386] | libc6.1-dev [alpha ia64] | libc-dev
  Provides the ISO C standard library
  Indirectly depended on by g++, but we'll ignore
  it since libc6-dev is used for non-C++ programs too.

libc6-dev-sparc64 [sparc]
  Used only on the sparc architecture.

gcc (>= 4:4.4.3)
g++ (>= 4:4.4.3)

  NOTE:
  The libstdc++ -dev library is not needed, as g++ depends on it

make
  Also depended on by dpkg-dev, but make does warrant its own
  dependency since debian/rules will need it even if dpkg-dev
  stopped depending on it

dpkg-dev (>= 1.13.5)
  Provides dpkg-genchanges and other scripts.  Versioned, because
  of support for the build-time dependency fields in /debian/control
  and dpkg-architecture support for OS and CPU information.

  NOTE:
  Although this list does not contain them, all `Essential: yes'
  packages are build-essential as well.  A list of such packages
  can be found by executing the following command
     `grep-status -FEssential -sPackage -ni yes'
  when the `grep-dctrl' package is installed and in its default
  configuration.  Such list is installed with this package as
  the file
     `/usr/share/doc/build-essential/essential-packages-list'
 
hurd-dev [hurd-i386]
  Provides libpthread.so (and other such essential components).

END LIST OF PACKAGES

Here's the format definition:

   - First line is the following, without any leading or trailing
     whitespace:
        BEGIN LIST OF PACKAGES

   - Last line is the following, without any leading or trailing
     whitespace:
        END LIST OF PACKAGES

   - A line with leading whitespace is a comment.

   - Other lines are joined with end-of-line replaced by comma, and
     the result is parsed like the body of the Build-Depends field.
     The list of build-essential packages for a particular
     architecture is constructed from the result list by ignoring all
     the package name - package version pairs which would be ignored
     if we were building for that architecture and then removing the
     architecture specifications.

The Python program list2depends parses stdin as if it were this
file and outputs one line that is suitable for use in a dependency
field body of a Debian binary package.

Local Variables:
mode: text
End:


---

### Post by oldos2er on 2012-12-06
Interesting. Without build-essential I get the "C++ compiler cannot create executables" error. I don't create *.deb files.

Whenever I first install (K)ubuntu I install build-essential along with many other packages, so I might miss the fact that it's being installed by default.

---

### Post by squakie on 2012-12-07
> **oldos2er said:**
> Interesting. Without build-essential I get the "C++ compiler cannot create executables" error. I don't create *.deb files.

Whenever I first install (K)ubuntu I install build-essential along with many other packages, so I might miss the fact that it's being installed by default.

+1.  I've always had to install build-essential even in 12.10.  Perhaps I try to do things beyond the simple things most beginners do, but I really don't think you can do much without the meta package.  I've never created a deb myself, I've just needed it.  I've run into errors in the past without it installed right from the start.  I did just go back and check synaptics, and it appears the description has changed, as it no longer talks about gcc and/or g++.  It now specifically says if you don't develop deb files you don't need it.  Maybe I'll try reloading Ubuntu in a vm and see if I can do anything without build-essential.  It just seems like I always end up with a lot of the very basic libs and headers missing if I don't.

---

### Post by s3a on 2012-12-07
To keep things minimal, install gcc and use any text editor. As a beginner, I recommend geany.

---

### Post by Pletched on 2012-12-07
> **oldos2er said:**
> Interesting. Without build-essential I get the "C++ compiler cannot create executables" error. I don't create *.deb files.

Whenever I first install (K)ubuntu I install build-essential along with many other packages, so I might miss the fact that it's being installed by default.

You don't need the build-essential package. That's for building debian packages. Too many programmers already do this and install extra garbage they will never use.

All you need is the g++ package for compiling C++ programs.

---

### Post by Ji Ruo on 2012-12-07
Use a text editor to create it and save it with the .c extension. Linux doesn't need the extension, but it's good practice to put it in. Open a terminal in the directory you created the file in. I use KDE not Unity, so unfortunately I can't tell you how to do this- in KDE you can right click the location in the file manager and select Actions->Open Terminal so hopefully Unity has something similar. Compile it by entering:
```
gcc -Wall -o myProgram myProgram.c
```
where myProgram is the name you have given it. gcc is the name of the compiler, -Wall will give you all the warnings, and -o allows you to name the output file (it will have a default name if you don't include this.) After it compiles, you should be able to run it by entering:```
./myProgram
```while you are still in the directory.

CodeBlocks is also a great option and is cross platform.

---

### Post by squakie on 2012-12-08
> **Pletched said:**
> You don't need the build-essential package. That's for building debian packages. Too many programmers already do this and install extra garbage they will never use.

All you need is the g++ package for compiling C++ programs.

Ah, but you USED to have to install it to get gcc - don't when they stopped doing that, but it can't be that long ago.

---

### Post by howefield on 2013-02-23
Old thread closed.

Please desist in posting to threads that have seen no replies in more than a year.

Feel free to start a fresh thread, and reference the old one if needs be.

Edit :
Reopened - closed in error.

---

