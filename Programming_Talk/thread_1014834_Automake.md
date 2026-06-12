---
title: "Automake"
date: 2008-12-18
forum: Programming Talk
---

### Post by WitchCraft on 2008-12-18
Hi, i have a project with appx. 15 sourcefiles.

I have a Makefile.posix
and a Makefile.windows

Now I can compile it and it works fine on windows and linux.

Just one question:
I'd like to have a ./configure 
make

Process, where it copies the appropriate makefile for the respective platform.

So far I have done
autoscan
autoheader
autoconf

And that works on Linux, but it only creates an automake process for linux.

Any ideas/help?

---

### Post by hod139 on 2008-12-18
Can I suggest an alternative to automake, cmake.

---

### Post by cabalas on 2008-12-18
I'd suggest looking at a program/library that is already set up to use the autotools to compile for both windows and linux.  The only one I can think of off hand is [SDL]("http://libsdl.org"), for the life of me I cannot think of an application that does this.

Also chances are that you already know this but I'm just checking anyway that you know that you'll need some form of compatibility layer for windows [cygwin]("http://www.cygwin.com/") and [msys]("http://MinGW.org") seem to be the most popular choices.

---

### Post by WitchCraft on 2008-12-18
> **cabalas said:**
> I'd suggest looking at a program/library that is already set up to use the autotools to compile for both windows and linux.  The only one I can think of off hand is [SDL]("http://libsdl.org"), for the life of me I cannot think of an application that does this.

Also chances are that you already know this but I'm just checking anyway that you know that you'll need some form of compatibility layer for windows [cygwin]("http://www.cygwin.com/") and [msys]("http://MinGW.org") seem to be the most popular choices.

I have msys and g++. It compiles well on all platforms.
Just working on the makefile, now.

Here my makefile for linux:
```

# Specify the compiler
CC = g++
# Specify the compiler FLAGs
CFLAGS = -fPIC -shared
# Specify the default build type
TYPE = debug
# Specify the main target
TARGET = libAladin.so
# Specify the directories containing the source files
#DIRS = . src util openal windows linux mac ia32 ia64 ppc
DIRS = . 
# Add directories to the include and library paths
INCPATH = .
LIBPATH = 
# Specify the libraries which are to be linked
LIBS = pthread
# Dynamic libraries
DLIBS =
# Which files to add to backups, apart from the source code
EXTRA_FILES = Makefile


# The next blocks change some variables depending on the build type
ifeq ($(TYPE),debug)
LDPARAM = 
CCPARAM = -Wall -g -Wno-unused
CCPARAM += $(CFLAGS)
MACROS =
endif

ifeq ($(TYPE),profile)
LDPARAM = -pg /lib/libc.so.6
CCPARAM = -Wall -pg
CCPARAM += $(CFLAGS)
MACROS = NDEBUG
endif

ifeq ($(TYPE), release)
LDPARAM = -s
CCPARAM = -Wall -O2
CCPARAM += $(CFLAGS)
MACROS = NDEBUG
endif



# Where to store object and dependancy files.
STORE = .make-$(TYPE)
# Makes a list of the source (.cpp) files.
SOURCE := $(foreach DIR,$(DIRS),$(wildcard $(DIR)/*.cpp))
# List of header files.
HEADERS := $(foreach DIR,$(DIRS),$(wildcard $(DIR)/*.hpp))
# Makes a list of the object files that will have to be created.
OBJECTS := $(addprefix $(STORE)/, $(SOURCE:.cpp=.o))
# Same for the .d (dependancy) files.
DFILES := $(addprefix $(STORE)/,$(SOURCE:.cpp=.d))

# Specify phony rules. These are rules that are not real files.
.PHONY: clean backup dirs

# Main target. The @ in front of a command prevents make from displaying
# it to the standard output.
$(TARGET): dirs $(OBJECTS)
	@echo Linking $(TARGET).
	@$(CC) -o $(TARGET) $(OBJECTS) $(CCPARAM) $(LDPARAM) $(foreach LIBRARY, \
                $(LIBS),-l$(LIBRARY)) $(foreach LIB,$(LIBPATH),-L$(LIB))

# Rule for creating object file and .d file, the sed magic is to add
# the object path at the start of the file because the files gcc
# outputs assume it will be in the same dir as the source file.
$(STORE)/%.o: %.cpp
	@echo Creating object file for $*...
	@$(CC) -Wp,-MMD,$(STORE)/$*.dd $(CCPARAM) $(foreach INC,$(INCPATH),-I$(INC))\
                $(foreach MACRO,$(MACROS),-D$(MACRO)) -c $< -o $@
	@sed -e '1s/^\(.*\)$$/$(subst /,\/,$(dir $@))\1/' $(STORE)/$*.dd > $(STORE)/$*.d
	@rm -f $(STORE)/$*.dd

# Empty rule to prevent problems when a header is deleted.
%.hpp: ;

# Cleans up the objects, .d files and executables.
clean:
	@echo Making clean.
	@-rm -f $(foreach DIR,$(DIRS),$(STORE)/$(DIR)/*.d $(STORE)/$(DIR)/*.o)
	@-rm -f $(TARGET)

# Backup the source files.
backup:
	@-if [ ! -e .backup ]; then mkdir .backup; fi;
	@zip .backup/backup_`date +%d-%m-%y_%H.%M`.zip $(SOURCE) $(HEADERS) $(EXTRA_FILES)

# Create the necessary directories
dirs:
	@-if [ ! -e $(STORE) ]; then mkdir $(STORE); fi;
	@-$(foreach DIR,$(DIRS), if [ ! -e $(STORE)/$(DIR) ]; \
         then mkdir $(STORE)/$(DIR); fi; )

# Includes the .d files so it knows the exact dependencies for every source.
-include $(DFILES)

```

Here my makefile for Windows:
```

# Specify the compiler
CC = g++
# Specify the compiler FLAGs
CFLAGS = -shared
# Specify the default build type
TYPE = debug
# Specify the main target
TARGET = libAladin.dll
# Specify the directories containing the source files
#DIRS = . src util openal windows linux mac ia32 ia64 ppc
DIRS = . 
# Add directories to the include and library paths
INCPATH = .
LIBPATH = 
# Specify the libraries which are to be linked
LIBS = 
# Dynamic libraries
DLIBS =
# Which files to add to backups, apart from the source code
EXTRA_FILES = Makefile


# The next blocks change some variables depending on the build type
ifeq ($(TYPE),debug)
LDPARAM = 
CCPARAM = -Wall -g -Wno-unused
CCPARAM += $(CFLAGS)
MACROS =
endif

ifeq ($(TYPE),profile)
LDPARAM = -pg /lib/libc.so.6
CCPARAM = -Wall -pg
CCPARAM += $(CFLAGS)
MACROS = NDEBUG
endif

ifeq ($(TYPE), release)
LDPARAM = -s
CCPARAM = -Wall -O2
CCPARAM += $(CFLAGS)
MACROS = NDEBUG
endif



# Where to store object and dependancy files.
STORE = .make-$(TYPE)
# Makes a list of the source (.cpp) files.
SOURCE := $(foreach DIR,$(DIRS),$(wildcard $(DIR)/*.cpp))
# List of header files.
HEADERS := $(foreach DIR,$(DIRS),$(wildcard $(DIR)/*.hpp))
# Makes a list of the object files that will have to be created.
OBJECTS := $(addprefix $(STORE)/, $(SOURCE:.cpp=.o))
# Same for the .d (dependancy) files.
DFILES := $(addprefix $(STORE)/,$(SOURCE:.cpp=.d))

# Specify phony rules. These are rules that are not real files.
.PHONY: clean backup dirs

# Main target. The @ in front of a command prevents make from displaying
# it to the standard output.
$(TARGET): dirs $(OBJECTS)
	@echo Linking $(TARGET).
	@$(CC) -o $(TARGET) $(OBJECTS) $(CCPARAM) $(LDPARAM) $(foreach LIBRARY, \
                $(LIBS),-l$(LIBRARY)) $(foreach LIB,$(LIBPATH),-L$(LIB))

# Rule for creating object file and .d file, the sed magic is to add
# the object path at the start of the file because the files gcc
# outputs assume it will be in the same dir as the source file.
$(STORE)/%.o: %.cpp
	@echo Creating object file for $*...
	@$(CC) -Wp,-MMD,$(STORE)/$*.dd $(CCPARAM) $(foreach INC,$(INCPATH),-I$(INC))\
                $(foreach MACRO,$(MACROS),-D$(MACRO)) -c $< -o $@
	@sed -e '1s/^\(.*\)$$/$(subst /,\/,$(dir $@))\1/' $(STORE)/$*.dd > $(STORE)/$*.d
	@rm -f $(STORE)/$*.dd

# Empty rule to prevent problems when a header is deleted.
%.hpp: ;

# Cleans up the objects, .d files and executables.
clean:
	@echo Making clean.
	@-rm -f $(foreach DIR,$(DIRS),$(STORE)/$(DIR)/*.d $(STORE)/$(DIR)/*.o)
	@-rm -f $(TARGET)

# Backup the source files.
backup:
	@-if [ ! -e .backup ]; then mkdir .backup; fi;
	@zip .backup/backup_`date +%d-%m-%y_%H.%M`.zip $(SOURCE) $(HEADERS) $(EXTRA_FILES)

# Create the necessary directories
dirs:
	@-if [ ! -e $(STORE) ]; then mkdir $(STORE); fi;
	@-$(foreach DIR,$(DIRS), if [ ! -e $(STORE)/$(DIR) ]; \
         then mkdir $(STORE)/$(DIR); fi; )

# Includes the .d files so it knows the exact dependencies for every source.
-include $(DFILES)

```

---

### Post by WitchCraft on 2008-12-25
bump.

My idea is to use the uname command to get the os, and use it to set cflags, lflags, includes and defines accordingly.


Here some bash script code:
```

#!/bin/bash


OPERATINGSYSTEM=$(uname -o)
PLATFORM=$(uname -s)
PROCESSOR=$(uname -m)
HOSTNAME=$(uname -n | cut --delimiter=. --fields=1)

#echo $PLATFORM
#echo $HOSTNAME


if [ "$PLATFORM" == "" ]
then
	echo "Platform is null"
else

	if [ "$PLATFORM" == "Linux" ]
	then
		echo "Building for Linux"
	else
		if [ "$PLATFORM" == "Unix" ]
		then
			echo "Building for Unix"
		else
			echo "Building for something else"
		fi
	fi
fi



exit

```

A few other questions: Anybody knows...
1. How to find out whether the processor is 64 or 32 bit
2. How to find out whether the OS is 32 or 64 bit, if the processor is 64 bit.
3. The uname -s + -n + -m output for FreeBSD and MacOS/Darwin?

---

### Post by WitchCraft on 2008-12-25
OK, can find number one like this:

```


MACHINE_TYPE=`uname -m`
if [ ${MACHINE_TYPE} == 'x86_64' ]; then
  # 64-bit stuff here
else
  # 32-bit stuff here
fi


```

OR:
```

#!/bin/bash

platform=`uname -m`
if [ "$platform"="i686" ]; then
	echo "32-bit OS"
	# Install necessary deb packages
elif [ "$platform"="X86_64" ]; then
	echo "64-bit OS"
	# Install necessary deb packages
else
	echo "Unknown platform"
	# Don't install any packages
fi

```

Well better with case-statement
```

#!/bin/bash

platform=`uname -m`
case $platform in
"i686")
  	echo "32-bit OS"
	# Install necessary deb packages
	;;
"X86_64")
	echo "64-bit OS"
	# Install necessary deb packages
	;;
*)
	echo "Unknown platform"
	# Don't install any packages
	;;
esac

```

Oh, also found freebsd

```

hostname = kramer-smilko.com
uname -m = i386
uname -r = 5.4-RELEASE
uname -s = FreeBSD
uname -v = FreeBSD 5.4-RELEASE #0: Sun May  8 10:21:06 UTC 2005     root at harlow.cse.buffalo.edu:/usr/obj/usr/src/sys/GENERIC 

/usr/bin/uname -p = i386


```

Now still searching solaris and mac

oh on mac:  uname -s: Darwin
and on solaris: uname -s: SunOS
and on HP-UNIX: uname -s: HP-UX
if [ `uname -s` == "OpenBSD" ];
uname -s = NetBSD

---

