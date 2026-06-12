---
title: "pkg-config and automake"
date: 2010-12-19
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-19
Creating automake scripts for a library distribution.
All my modules have simple compiler options except for two: One uses uses gtkmm and the other uses gtk in simple bash scrip I have: 

```

g++ -Wall -pedantic -std=c++0x -c *.cc
g++ -Wall -pedantic -std=c++0x -c cs_unistring.cpp `pkg-config gtkmm-2.4 --cflags`
g++ -Wall -pedantic -std=c++0x -c cs_glade.cpp `pkg-config --cflags gtk+-2.0`
ar -rcs cs_lib.a *.o

```

I used the trick of giving the two special cases a .cpp extension so they would not be included in the *.cc compilation. However now IDK how to do this with automake :confused:

... any suggestions please?

---

### Post by MadCow108 on 2010-12-19
you could create two static libraries from these two files (possibly with noinst_ prefix)
they can have different flags than the rest

but is this really needed? who cases if there are some extra -I flags for the other files?
or does your program break when adding -pthread? o_O

also look at the autoconf macros section of man pkg-config

and automake discourages such use of wildcards:
[http://www.gnu.org/software/hello/manual/automake/Wildcards.html#Wildcards](http://www.gnu.org/software/hello/manual/automake/Wildcards.html#Wildcards)

---

### Post by worksofcraft on 2010-12-19
> **MadCow108 said:**
> you could create two static libraries from these two files (possibly with noinst_ prefix)
they can have different flags than the rest

but is this really needed? who cases if there are some extra -I flags for the other files?
or does your program break when adding -pthread? o_O

also look at the autoconf macros section of man pkg-config

and automake discourages such use of wildcards:
[http://www.gnu.org/software/hello/manual/automake/Wildcards.html#Wildcards](http://www.gnu.org/software/hello/manual/automake/Wildcards.html#Wildcards)

I think my problem is more that I don't know what autoconf variable to associate the pkg-config command with... is it just compiler flags or can it include module names and paths to header files?

Similar considerations for the link/loader options. Might even specify things that are in conflict with the ones I want :confused:

Certainly I can check what pkg-config produces on my computer but is that going to be the same for some other system? What about systems that don't have those packages installed but could use all the rest of the library... with the exception of the two affected modules?

For a start, running g++ --help, the -pthread option isn't even listed so what does that do then ?

---

### Post by saulgoode on 2010-12-19
I have only recently investigated using Autotools for creating libraries (as opposed to programs), so the following should be taken tentatively.

> **worksofcraft said:**
> I think my problem is more that I don't know what autoconf variable to associate the pkg-config command with... is it just compiler flags or can it include module names and paths to header files?

Since gtk+ and gtkmm are libtoolized (i.e., they have .la metadata files), you should be able to include them by adding a line to your configure.ac similar to:

```
PKG_CHECK_MODULES([DEPS], [gtk+-2.0 >= 2.20.1 gtkmm-2.4 >= 2.18.2])
```

Since gtk+ is a dependency of gtkmm, I don't think it needs to specified; the following should be sufficient:

```
PKG_CHECK_MODULES([DEPS], [gtkmm-2.4 >= 2.18.2])
```

> **worksofcraft said:**
> Certainly I can check what pkg-config produces on my computer but is that going to be the same for some other system?
That is the intended purpose of the library archive metafiles, providing a cross-platform "pkg-config" type mechanism. EDIT: *I think I misunderstood this question. By "other system" did you mean another GNU/Linux system upon which the same shared object/static library file is used, or a different platform which may use a different approach to dynamic libraries?*

> **worksofcraft said:**
> What about systems that don't have those packages installed but could use all the rest of the library... with the exception of the two affected modules?
The PKG_CHECK_MODULES macro supports options for action to be taken if a library is not found. I do not know how to use this functionality but am guessing that it can address your concern.

> **worksofcraft said:**
> For a start, running g++ --help, the -pthread option isn't even listed so what does that do then ?
The -pthread switch is used by the linker (not the compiler). It is specified as an inherited option in the libgtkmm-2.4.la and libgtk-x11-2.0.la library archive files.

---

### Post by worksofcraft on 2010-12-20
> **saulgoode said:**
> I have only recently investigated using Autotools for creating libraries (as opposed to programs), so the following should be taken tentatively.



Since gtk+ and gtkmm are libtoolized (i.e., they have .la metadata files), you should be able to include them by adding a line to your configure.ac similar to:

```
PKG_CHECK_MODULES([DEPS], [gtk+-2.0 >= 2.20.1 gtkmm-2.4 >= 2.18.2])
```

Since gtk+ is a dependency of gtkmm, I don't think it needs to specified; the following should be sufficient:

```
PKG_CHECK_MODULES([DEPS], [gtkmm-2.4 >= 2.18.2])
```


That is the intended purpose of the library archive metafiles, providing a cross-platform "pkg-config" type mechanism. EDIT: *I think I misunderstood this question. By "other system" did you mean another GNU/Linux system upon which the same shared object/static library file is used, or a different platform which may use a different approach to dynamic libraries?*


The PKG_CHECK_MODULES macro supports options for action to be taken if a library is not found. I do not know how to use this functionality but am guessing that it can address your concern.


The -pthread switch is used by the linker (not the compiler). It is specified as an inherited option in the libgtkmm-2.4.la and libgtk-x11-2.0.la library archive files.

Ok thanks PKG_CHECK_MODULES is indeed the one I needed but I think I'll leave that for another day now because it seems to be really complicated and convoluted for me at the moment :(

---

### Post by MadCow108 on 2010-12-20
autotools is not the easiest tool to learn. And usually you only need 0.001% of its many (very hard to use) features.
And its m4 language is just plain unreadable ...

maybe a more modern easier build system like cmake (only requires c++ compiler), scons (requires python) or cons (perl) is more suited for you.

> 
The -pthread switch is used by the linker (not the compiler). It is specified as an inherited option in the libgtkmm-2.4.la and libgtk-x11-2.0.la library archive files.

This is not correct.
-pthread also turns on -D_REENTRANT or -D_THREADSAFE in the compiler in addition to the -lpthread linker flag

---

### Post by worksofcraft on 2010-12-22
> **MadCow108 said:**
> autotools is not the easiest tool to learn. And usually you only need 0.001% of its many (very hard to use) features.
And its m4 language is just plain unreadable ...

maybe a more modern easier build system like cmake (only requires c++ compiler), scons (requires python) or cons (perl) is more suited for you.


This is not correct.
-pthread also turns on -D_REENTRANT or -D_THREADSAFE in the compiler in addition to the -lpthread linker flag

Oh.. ok thanks :)
I can see it's quite innocuous to inlcude it with all my modules now. I settled on this bash script in the end:

[php]
CFLAGS="-std=c++0x -Wall -pedantic -g `pkg-config --cflags --libs gtk+-2.0 gmodule-2.0 gtkmm-2.4`"
echo "linking glade file"
ld -r -b binary former.glade -o glade.o 2> /tmp/errors.log

echo "building static library objects"
g++ $CFLAGS -c *.cc 2>> /tmp/errors.log

echo "making static link library " cs_lib.a$MAJ
ar -rcs cs_lib.a$MAJ *.o 2>> /tmp/errors.log

echo "making test program ./check"
g++ $CFLAGS check.cpp cs_lib.a$MAJ -o check 2>> /tmp/errors.log
echo "running tests"
./check > check.out 2>> /tmp/errors.log
if [ $? -ne 0 ]
then
	echo "check detected a problem"
	exit $?
fi
# check for errors in log (warnings are ok) report 1st 3
grep -m 3 -i "error" /tmp/errors.log
if [ $? -eq 0 ]
then
	echo "there are errors, see /tmp/errors.log"
	exit 1
fi
# check expected output was generated
diff check.out check.txt
if [ $? -ne 0 ]
then
	echo "check.bin did not produce expected output"
	echo "compare check.out with check.txt"
	exit $?
fi
[/php]

The bit I like best is my integral validation check :)

... however I just notice that the glade file doesn't really have to go in the library! Only goes to show how pointless it is trying to do hard things when I'm already getting the easy ones wrong... :D

---

### Post by MadCow108 on 2010-12-22
For this a plain gnu makefile is probably quite easy to write.
it will be just as simple as you script and you can use the make features (minimal recompile, parallel build etc.)

---

### Post by worksofcraft on 2010-12-22
> **MadCow108 said:**
> For this a plain gnu makefile is probably quite easy to write.
it will be just as simple as you script and you can use the make features (minimal recompile, parallel build etc.)

Meh... and then I change some include path, or split a source file in two, or get the dependencies wrong so that parts don't get rebuilt when they should...

Nah, a basic g++ *.cc followed by ar *.o is just fine for me :)
all the rest is just window dressing ;)

---

### Post by Arndt on 2010-12-22
> **worksofcraft said:**
> Oh.. ok thanks :)
I can see it's quite innocuous to inlcude it with all my modules now. I settled on this bash script in the end:

[php]
CFLAGS="-std=c++0x -Wall -pedantic -g `pkg-config --cflags --libs gtk+-2.0 gmodule-2.0 gtkmm-2.4`"
echo "linking glade file"
ld -r -b binary former.glade -o glade.o 2> /tmp/errors.log

echo "building static library objects"
g++ $CFLAGS -c *.cc 2>> /tmp/errors.log

echo "making static link library " cs_lib.a$MAJ
ar -rcs cs_lib.a$MAJ *.o 2>> /tmp/errors.log

echo "making test program ./check"
g++ $CFLAGS check.cpp cs_lib.a$MAJ -o check 2>> /tmp/errors.log
echo "running tests"
./check > check.out 2>> /tmp/errors.log
if [ $? -ne 0 ]
then
	echo "check detected a problem"
	exit $?
fi
# check for errors in log (warnings are ok) report 1st 3
grep -m 3 -i "error" /tmp/errors.log
if [ $? -eq 0 ]
then
	echo "there are errors, see /tmp/errors.log"
	exit 1
fi
# check expected output was generated
diff check.out check.txt
if [ $? -ne 0 ]
then
	echo "check.bin did not produce expected output"
	echo "compare check.out with check.txt"
	exit $?
fi
[/php]



Testing for errors the way you do, you may happen to catch a warning with a variable name containing the string "error".

---

### Post by JupiterV2 on 2010-12-23
One very simple solution is to use pkg-config's and GTK+'s m4 macros:

configure.ac
```

dnl Test for pkg-config
PKG_PROG_PKG_CONFIG([0.22])

dnl Test for gtk+
AM_PATH_GTK_2_0([2.20.1],,AC_MSG_ERROR([Gtk+ 2.20.1 or higher required.]))

```

Then in your Makefile.am file you can simply use the @GTK_LIBS@ and @GTK_CFLAGS@ variables.

If you use the above method, make sure you use aclocal and include the macro definitions it supplies in your package. Otherwise, others who don't have the above m4 definitions on their local PC won't be able to ./configure your program.

Note: Unless you plan to use pkg-config for your own program, you probably don't need to call PKG_PROG_PKG_CONFIG in configure.ac since AM_PATH_GTK_2_0 should check for pkg-config itself.

---

### Post by worksofcraft on 2010-12-23
> **Arndt said:**
> Testing for errors the way you do, you may happen to catch a warning with a variable name containing the string "error".

Good point... in fact that already happened, but then I just ignored the error message and used the library anyway. Grepping for the word "error" seems better than having to check through warning messages manually... on 64 bit it compiles without any warnings but on 32 bit they are currently unavoidable because I need to use 64 bit "long long" an that is not part of the C++ standard.

---

