---
title: "problem with makefile fortran source"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by emily8 on 2015-03-24
Hi everyone,

I'm very new to Linux. I'm trying to install the program mothur, which requires the user to do some editing of the makefile ([http://www.mothur.org/wiki/Makefile_options](http://www.mothur.org/wiki/Makefile_options)), including the fortran source settings.  I have gfortran version 4.8.2 installed.

The line in the original file looks like this:
fortranSource:
    ${FORTAN_COMPILER} -c $(FORTRAN_FLAGS) *.f

I changed it to this:
fortranSource:
    ${gfortran} -c $(-m64)

And I get this error message:
make: c: Command not found
make: [fortranSource] Error 127 (ignored)
...
compilation terminated.

I'm not sure what to do.

Cheers, Emily

---

### Post by steeldriver on 2015-03-24
Hello and welcome to the forums

That's not the way that makefile syntax works: you can't just stick a value (gfortran) into a variable expansion like ${FORTRAN_COMPILER}; instead, you would usually find the assignment expression that looks like

```

FORTRAN_COMPILER = something

```
and modify it to

```

FORTRAN_COMPILER = gfortran

```

or alternatively invoke make with a variable override of the form
```

make "FORTRAN_COMPILER=gfortran"

```

However, in this case it looks like gfortran is already the default:

```

     1  ###################################################
     2  #
     3  # Makefile for mothur
     4  #
     5  ###################################################
     6
     7  #
     8  # Macros
     9  #
    10
    11  USEMPI ?= no
    12  64BIT_VERSION ?= yes
    13  USEREADLINE ?= yes
    14  USECOMPRESSION ?= no
    15  MOTHUR_FILES="\"Enter_your_default_path_here\""
    16  RELEASE_DATE = "\"3/23/2014\""
    17  VERSION = "\"1.35.0\""
    18  **FORTAN_COMPILER = gfortran**
    19  FORTRAN_FLAGS =

```

In fact, it looks like all you need to do to build on Ubuntu x86_64 is follow the instructions in makefile lines 24-42 and:

[LIST=1]
[*]comment out (using the # character) the line [COLOR=#ff0000]**TARGET_ARCH += -arch x86_64**[/COLOR] 
[*]uncomment the line  [COLOR=#0000ff]**CXXFLAGS += -mtune=native -march=native**[/COLOR] 
[/LIST]

```

    20
    21  # Optimize to level 3:
    22  CXXFLAGS += -O3
    23
    24  ifeq  ($(strip $(64BIT_VERSION)),yes)
    25      #if you are using centos uncomment the following lines
    26      #CXX = g++44
    27
    28      **#if you are a mac user use the following line**
    29      [COLOR=#ff0000]**#TARGET_ARCH += -arch x86_64**[/COLOR]
    30
    31      #if you using cygwin to build Windows the following line
    32      #CXX = x86_64-w64-mingw32-g++
    33      #CC = x86_64-w64-mingw32-g++
    34      #FORTAN_COMPILER = x86_64-w64-mingw32-gfortran
    35      #TARGET_ARCH += -m64 -static
    36
    37      **#if you are a linux user use the following line**
    38      [COLOR=#0000ff]**CXXFLAGS += -mtune=native -march=native**[/COLOR]
    39
    40      CXXFLAGS += -DBIT_VERSION
    41      FORTRAN_FLAGS = -m64
    42  endif
    43
    .
    .
    .

```

You will probably need to install the libreadline-dev and libncurses5-dev packages if you have not already done so.

---

### Post by emily8 on 2015-03-24
Thank you very much!  I've been beating my head against the wall with this all day.  I made the changes and it appears to be successfully installing (at least there's lots of text and no error messages yet).  

Emily

---

