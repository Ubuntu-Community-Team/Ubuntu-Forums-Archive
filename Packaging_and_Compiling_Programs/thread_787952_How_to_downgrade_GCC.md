---
title: "How to downgrade GCC?"
date: 2008-05-09
forum: Packaging and Compiling Programs
---

### Post by matts0344 on 2008-05-09
Hello, I'm trying to compile some same NVIDIA CUDA programs in Ubuntu 8.04 using GCC 4.2. 

I get error messages when I try to "make" the sample projects. Following the instructions at this link:

[http://developer.download.nvidia.com/compute/cuda/1_1/CUDA_SDK_release_notes_linux.txt]("http://developer.download.nvidia.com/compute/cuda/1_1/CUDA_SDK_release_notes_linux.txt")

I get error messages when I make the projects with
```
make emu=1
```

I get stuff like:

```
"/usr/include/c++/4.2/i486-linux-gnu/bits/c++config.h", line 149: error: 
          expected a "{"
  namespace std __attribute__ ((__visibility__ ("default"))) {
                ^

"/usr/include/c++/4.2/bits/cpp_type_traits.h", line 74: error: expected a "{"
  namespace __gnu_cxx __attribute__ ((__visibility__ ("default"))) {
                      ^

```


I read that you can not use gcc version 4.2 and to try using 4.1 instead. How do I go about doing this? I'm a linux newb so I need some very detailed instructions. 

I tried just 

```
sudo apt-get install gcc-4.1 
```

but that didn't help. Not sure if I should have done that if it messes up anything :confused:

Thanks for any help you can give.

---

### Post by steinlee on 2008-05-09
after sudo apt-get install gcc-4.1, you have two versions of gcc.
type gcc --version to see the default version. I think it is still gcc 4.2.
You can use ln -s to replace default gcc with gcc-4.1. If you only use 4.1
to compile this piece of code, try to replace gcc or g++ in your Makefile 
with gcc-4.1 or gc++-4.1.

---

### Post by matts0344 on 2008-05-09
I tried changing the CC variable in the makefile, it didn't change anything, I'm not too experienced with makefiles however.

How do I create that symbolic link exactly? (don't want to mess this up since its something for school and I have limited time)

---

### Post by steinlee on 2008-05-09
In your Makefile, you normally have the following:
CC  = gcc
CXX = g++

Change them to
CC  = gcc-4.1
CXX = g++-4.1

In order to make sure if gcc-4.1 exists, try
  ls -al /usr/bin | grep gcc
to see if gcc-4.1 and g++-4.1 are there.

---

### Post by matts0344 on 2008-05-09
Didn't seem to work.

Here is the Makefile I'm using:

```
################################################################################
#
# Build script for project
#
################################################################################

# Add source files here
EXECUTABLE	:= matrixMul
# Cuda source files (compiled with cudacc)
CUFILES		:= matrixMul.cu
# C/C++ source files (compiled with gcc / c++)
CCFILES		:= \
	matrixMul_gold.cpp


################################################################################
# Rules and targets

include ../../common/common.mk
```


It includes common.mk so I changed the variables there like so:



```
################################################################################
#
# Common build script
#
################################################################################

.SUFFIXES : .cu .cu_dbg_o .c_dbg_o .cpp_dbg_o .cu_rel_o .c_rel_o .cpp_rel_o .cubin

CUDA_INSTALL_PATH ?= /usr/local/cuda

ifdef cuda-install
	CUDA_INSTALL_PATH := $(cuda-install)
endif

# Basic directory setup for SDK
# (override directories only if they are not already defined)
SRCDIR     ?= 
ROOTDIR    ?= ..
ROOTBINDIR ?= $(ROOTDIR)/../bin
BINDIR     ?= $(ROOTBINDIR)/linux
ROOTOBJDIR ?= obj
LIBDIR     := $(ROOTDIR)/../lib
COMMONDIR  := $(ROOTDIR)/../common

# Compilers
NVCC       := nvcc 
CXX        := g++-4.1
CC         := gcc-4.1
LINK       := g++-4.1 -fPIC

# Includes
INCLUDES  += -I. -I$(CUDA_INSTALL_PATH)/include -I$(COMMONDIR)/inc

# architecture flag for cubin build
CUBIN_ARCH_FLAG := -m32

# Warning flags
CXXWARN_FLAGS := \
	-W -Wall \
	-Wimplicit \
	-Wswitch \
	-Wformat \
	-Wchar-subscripts \
	-Wparentheses \
	-Wmultichar \
	-Wtrigraphs \
	-Wpointer-arith \
	-Wcast-align \
	-Wreturn-type \
	-Wno-unused-function \
	$(SPACE)

CWARN_FLAGS := $(CXXWARN_FLAGS) \
	-Wstrict-prototypes \
	-Wmissing-prototypes \
	-Wmissing-declarations \
	-Wnested-externs \
	-Wmain \

# Compiler-specific flags
NVCCFLAGS := 
CXXFLAGS  := $(CXXWARN_FLAGS)
CFLAGS    := $(CWARN_FLAGS)

# Common flags
COMMONFLAGS += $(INCLUDES) -DUNIX

# Debug/release configuration
ifeq ($(dbg),1)
	COMMONFLAGS += -g
	NVCCFLAGS   += -D_DEBUG
	BINSUBDIR   := debug
	LIBSUFFIX   := D
else 
	COMMONFLAGS += -O3 
	BINSUBDIR   := release
	LIBSUFFIX   :=
	NVCCFLAGS   += --compiler-options -fno-strict-aliasing
	CXXFLAGS    += -fno-strict-aliasing
	CFLAGS      += -fno-strict-aliasing
endif

# append optional arch/SM version flags (such as -arch sm_11)
NVCCFLAGS += $(SMVERSIONFLAGS)

# architecture flag for cubin build
CUBIN_ARCH_FLAG := -m32

# detect if 32 bit or 64 bit system
HP_64 =	$(shell uname -m | grep 64)

# OpenGL is used or not (if it is used, then it is necessary to include GLEW)
OPENGLLIB := -lGL -lGLU -lglut
ifeq ($(USEGLLIB),1)
	ifeq "$(strip $(HP_64))" ""
		OPENGLLIB += -lGLEW
	else
		OPENGLLIB += -lGLEW_x86_64
	endif

	CUBIN_ARCH_FLAG := -m64
endif

ifeq ($(USEPARAMGL),1)
	PARAMGLLIB := -lparamgl$(LIBSUFFIX)
endif

ifeq ($(USECUDPP), 1)
	ifeq "$(strip $(HP_64))" ""
		CUDPPLIB := -lcudpp
	else
		CUDPPLIB := -lcudpp64
	endif

	CUDPPLIB := $(CUDPPLIB)$(LIBSUFFIX)

	ifeq ($(emu), 1)
		CUDPPLIB := $(CUDPPLIB)_emu
	endif
endif

# Libs
LIB       := -L$(CUDA_INSTALL_PATH)/lib -L$(LIBDIR) -L$(COMMONDIR)/lib
ifeq ($(USEDRVAPI),1)
   LIB += -lcuda -lcudart ${OPENGLLIB} $(PARAMGLLIB) $(CUDPPLIB) ${LIB} 
else
   LIB += -lcudart ${OPENGLLIB} $(PARAMGLLIB) $(CUDPPLIB) ${LIB}
endif

ifeq ($(USECUFFT),1)
  ifeq ($(emu),1)
    LIB += -lcufftemu
  else
    LIB += -lcufft
  endif
endif

ifeq ($(USECUBLAS),1)
  ifeq ($(emu),1)
    LIB += -lcublasemu
  else
    LIB += -lcublas
  endif
endif

# Lib/exe configuration
ifneq ($(STATIC_LIB),)
	TARGETDIR := $(LIBDIR)
	TARGET   := $(subst .a,$(LIBSUFFIX).a,$(LIBDIR)/$(STATIC_LIB))
	LINKLINE  = ar qv $(TARGET) $(OBJS) 
else
	LIB += -lcutil$(LIBSUFFIX)
	# Device emulation configuration
	ifeq ($(emu), 1)
		NVCCFLAGS   += -deviceemu
		CUDACCFLAGS += 
		BINSUBDIR   := emu$(BINSUBDIR)
		# consistency, makes developing easier
		CXXFLAGS		+= -D__DEVICE_EMULATION__
		CFLAGS			+= -D__DEVICE_EMULATION__
	endif
	TARGETDIR := $(BINDIR)/$(BINSUBDIR)
	TARGET    := $(TARGETDIR)/$(EXECUTABLE)
	LINKLINE  = $(LINK) -o $(TARGET) $(OBJS) $(LIB)
endif

# check if verbose 
ifeq ($(verbose), 1)
	VERBOSE :=
else
	VERBOSE := @
endif

################################################################################
# Check for input flags and set compiler flags appropriately
################################################################################
ifeq ($(fastmath), 1)
	NVCCFLAGS += -use_fast_math
endif

ifeq ($(keep), 1)
	NVCCFLAGS += -keep
	NVCC_KEEP_CLEAN := *.i* *.cubin *.cu.c *.cudafe* *.fatbin.c *.ptx
endif

ifdef maxregisters
	NVCCFLAGS += -maxrregcount $(maxregisters)
endif

# Add cudacc flags
NVCCFLAGS += $(CUDACCFLAGS)

# Add common flags
NVCCFLAGS += $(COMMONFLAGS)
CXXFLAGS  += $(COMMONFLAGS)
CFLAGS    += $(COMMONFLAGS)

ifeq ($(nvcc_warn_verbose),1)
	NVCCFLAGS += $(addprefix --compiler-options ,$(CXXWARN_FLAGS)) 
	NVCCFLAGS += --compiler-options -fno-strict-aliasing
endif

################################################################################
# Set up object files
################################################################################
OBJDIR := $(ROOTOBJDIR)/$(BINSUBDIR)
OBJS +=  $(patsubst %.cpp,$(OBJDIR)/%.cpp_o,$(notdir $(CCFILES)))
OBJS +=  $(patsubst %.c,$(OBJDIR)/%.c_o,$(notdir $(CFILES)))
OBJS +=  $(patsubst %.cu,$(OBJDIR)/%.cu_o,$(notdir $(CUFILES)))

################################################################################
# Set up cubin files
################################################################################
CUBINDIR := $(SRCDIR)data
CUBINS +=  $(patsubst %.cu,$(CUBINDIR)/%.cubin,$(notdir $(CUBINFILES)))

################################################################################
# Rules
################################################################################
$(OBJDIR)/%.c_o : $(SRCDIR)%.c $(C_DEPS)
	$(VERBOSE)$(CC) $(CFLAGS) -o $@ -c $<

$(OBJDIR)/%.cpp_o : $(SRCDIR)%.cpp $(C_DEPS)
	$(VERBOSE)$(CXX) $(CXXFLAGS) -o $@ -c $<

$(OBJDIR)/%.cu_o : $(SRCDIR)%.cu $(CU_DEPS)
	$(VERBOSE)$(NVCC) -o $@ -c $< $(NVCCFLAGS)

$(CUBINDIR)/%.cubin : $(SRCDIR)%.cu cubindirectory
	$(VERBOSE)$(NVCC) $(CUBIN_ARCH_FLAG) -o $@ -cubin $< $(NVCCFLAGS)

$(TARGET): makedirectories $(OBJS) $(CUBINS) Makefile
	$(VERBOSE)$(LINKLINE)

cubindirectory:
	@mkdir -p $(CUBINDIR)

makedirectories:
	@mkdir -p $(LIBDIR)
	@mkdir -p $(OBJDIR)
	@mkdir -p $(TARGETDIR)


tidy :
	@find | egrep "#" | xargs rm -f
	@find | egrep "\~" | xargs rm -f

clean : tidy
	$(VERBOSE)rm -f $(OBJS)
	$(VERBOSE)rm -f $(CUBINS)
	$(VERBOSE)rm -f $(TARGET)
	$(VERBOSE)rm -f $(NVCC_KEEP_CLEAN)

clobber : clean
	rm -rf $(ROOTOBJDIR)
```






I still get the same output errors though. Its still getting the files from gcc 4.2 it seems.

---

### Post by steinlee on 2008-05-09
After your changes in the Makefile, you may need to do "make clean" at first. Then make again. If it still does not work, it is not gcc-4.1 
problem. You may need to get older versions.

---

### Post by matts0344 on 2008-05-09
Tried the "make clean" command. Still no dice.

Still getting stuff like:

```
"/usr/include/c++/4.2/cstdlib", line 161: error: expected a "{"
  namespace __gnu_cxx __attribute__ ((__visibility__ ("default"))) {

```

Hmmm.

---

### Post by koderpat on 2008-10-05
Try creating a gutsy-installation directory using debootstrap.  You can use it to test binaries amongst various distributions.  Or in your case, create a ubunutu 7.10 distribution to link against.

```

apt-get install debootstrap
debootstrap gutsy newDir
chroot newDir

```

from here you can get your gcc 4.1, and various other dependencies
```

apt-get install gcc-4.1 g++-4.1 gdb freeglut3 make automake build-essential freeglut3-dev

```

From here you can try installing and compiling the CUDA Library and SDKs

At some point you might have to mount proc and sys fs; so, for completeness
(from inside chroot)
```

mount -t proc none /proc
mount -t sysfs none /sys
might have to also copy your /dev/* entries from host

```

hope this helps :popcorn:

---

### Post by abhilashm86 on 2008-10-09
try this command,
sudo aptitude update && sudo aptitude install build-essential

automatically gcc n other compilers will get downgrade and installed..........

---

