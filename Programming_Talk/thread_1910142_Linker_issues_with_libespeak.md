---
title: "Linker issues with libespeak"
date: 2012-01-16
forum: Programming Talk
---

### Post by ve4cib on 2012-01-16
I just upgraded one of the robots in the lab at school to use Xubuntu 11.10 (it originally used Ubuntu 9.10), and I am getting the following problem when trying to compile some custom applications we use for our research:

```
/usr/local/lib/libdarwin.so: undefined reference to `espeak_Synth'
/usr/local/lib/libdarwin.so: undefined reference to `espeak_Initialize'
/usr/local/lib/libdarwin.so: undefined reference to `espeak_SetVoiceByName'
/usr/local/lib/libdarwin.so: undefined reference to `espeak_Synchronize'
collect2: ld returned 1 exit status
make: *** [marathon] Error 1
```

Here is the Makefile used to compile:

```
#---------------------------------------------------------------------
# C++ COMPILER, COMPILER FLAGS, AND TARGET PROGRAM NAME
#---------------------------------------------------------------------
DIR_DARWIN  = /usr/local
DIR_OBJS    = .objects
DIR_QT      = /usr/include/qt4

TARGET      = marathon
CC          = gcc
CX          = g++
CCFLAGS     = -O2 -O3 -DLINUX -D_GNU_SOURCE -Wall $(INCLUDES)
CXFLAGS     = -O2 -O3 -DLINUX -D_GNU_SOURCE -Wall $(INCLUDES)
LNKCC       = $(CX)
LNKFLAGS    = $(CXFLAGS) -Wl,-rpath,$(DIR_DARWIN)/lib
INCLUDES   += -I$(DIR_QT)/QtCore -I$(DIR_QT)/QtGui -I$(DIR_QT)/QtXml -I$(DIR_QT)
INCLUDES   += -I$(DIR_DARWIN)/include/darwin/framework -I$(DIR_DARWIN)/include/darwin/linux -I$(DIR_DARWIN)/include/motionlibrary
LIBRARIES  += -lQtXml -lQtGui -lQtCore
LIBRARIES  += -lpthread -ldl -lcv -lhighgui -lespeak -ldarwin -lmlibrary -lcxcore


#---------------------------------------------------------------------
# FILES
#---------------------------------------------------------------------
SOURCES = main.cpp darwin_hardware.cpp image_processing.cpp image_window.cpp map.cpp settings.cpp strategy.cpp

OBJECTS = $(addsuffix .o,$(addprefix $(DIR_OBJS)/,$(basename $(notdir $(SOURCES)))))


#---------------------------------------------------------------------
# COMPILING RULES
#---------------------------------------------------------------------
$(TARGET): make_directory $(OBJECTS)
	$(LNKCC) $(LNKFLAGS) $(OBJECTS) $(LIBRARIES) -o $(TARGET)

all: $(TARGET)

clean:
	rm -rf $(TARGET) $(DIR_OBJS) core *~ *.a *.so *.lo

make_directory:
	mkdir -p $(DIR_OBJS)/

$(DIR_OBJS)/%.o: %.c
	$(CC) $(CCFLAGS) -c $? -o $@

$(DIR_OBJS)/%.o: %.cpp
	$(CX) $(CXFLAGS) -c $? -o $@


#---------------------------------------------------------------------
# END OF MAKEFILE
#---------------------------------------------------------------------

```

The application uses a few custom libraries we wrote in-house:
- libdarwin (contains some code that uses libespeak; installed as libdarwin.so[.1[.0[.0]]] in /usr/local/lib)
- libmlibrary (math-heavy library; installed to /usr/local/lib)

libdarwin compiles just fine.  But when I try to compile anything against it I get linker errors relating to espeak.  I have the libesepak-dev package installed, and libespeak.so exists in /usr/lib.


Just to add to the problems everything compiles just fine on my laptop (running Ubuntu 11.04), using exactly the same code and makefiles.  Could there be some kind of change to GCC that I am not aware of?  The unreferenced functions exist in the Espeak header files, and there weren't any deprecation warnings before, so as far as I can tell they *should* exist.  The linker just can't find them.

If anyone has any suggestions, or if you need more information (makefiles/source from the offending sections of libdarwin, etc...) please let me know.  Your help is greatly appreciated!

---

### Post by Bachstelze on 2012-01-16
ld now operates with -as-needed by default. In a nutshell, this means that an object file or library that references a symbol must be placed *before* the object file or library that provides it on the command line.

(Alternatively, you can restore the old behaviour by adding -no-as-needed to LDFLAGS).

---

