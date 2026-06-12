---
title: "trouble with makefile, system cannot find file specified"
date: 2011-08-19
forum: Packaging and Compiling Programs
---

### Post by tianshiz on 2011-08-19
hey guys,

  I'm having a lot of trouble building this makefile below. When I call make, I get the :
```
C:\nieseries>make
cl.exe /nologo /c /DkLittleEndian=1 /DkMicrosoft=1 /I./ChipObjects /I./Examples
 /I../nimhddkwdm /Foaiex1.obj ./Examples/aiex1.cpp
process_begin: CreateProcess(NULL, cl.exe /nologo /c /DkLittleEndian=1 /DkMicros
oft=1 /I./ChipObjects /I./Examples /I../nimhddkwdm /Foaiex1.obj ./Examples/aiex1
.cpp, ...) failed.
make (e=2): The system cannot find the file specified.
make: *** [aiex1.obj] Error 2
```
```
#
# nieseries/Makefile
#
# $DateTime: 2006/10/24 23:40:45 $
#

#
# Root source directory
#
EXAMPLE_SOURCE_DIR := .

#
# Directory where the examples and objects are built
# 
BUILD_DIR := .

#
#  DMA Library location
#
DMA_LIBRARY_DIR :=

#
#  OS Interface location
#
OSINTERFACE_DIR := ../nimhddkwdm
OSINTERFACE_MAKEFILE := win-wdm.mak

#
#  Define include directories, objects and targets
#

VPATH += \
    $(EXAMPLE_SOURCE_DIR)/ChipObjects \
    $(EXAMPLE_SOURCE_DIR)/Examples
 
CXX_INCLUDES += \
    $(INCLUDE_FLAG)$(EXAMPLE_SOURCE_DIR)/ChipObjects \
    $(INCLUDE_FLAG)$(EXAMPLE_SOURCE_DIR)/Examples

OBJECTS += \
    $(BUILD_DIR)/tESeries$(OBJ_SUFFIX) \
    $(BUILD_DIR)/tSTC$(OBJ_SUFFIX)

TARGETS += \
    $(BUILD_DIR)/aiex1$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex2$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex3$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex5$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex6$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex7$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex8$(PRG_SUFFIX) \
    $(BUILD_DIR)/aiex9$(PRG_SUFFIX) \
    $(BUILD_DIR)/aoex1$(PRG_SUFFIX) \
    $(BUILD_DIR)/aoex2$(PRG_SUFFIX) \
    $(BUILD_DIR)/aoex3$(PRG_SUFFIX) \
    $(BUILD_DIR)/aoex4$(PRG_SUFFIX) \
    $(BUILD_DIR)/aoex5$(PRG_SUFFIX) \
    $(BUILD_DIR)/digex1$(PRG_SUFFIX) \
    $(BUILD_DIR)/digex2$(PRG_SUFFIX) \
    $(BUILD_DIR)/gpct1$(PRG_SUFFIX) \
    $(BUILD_DIR)/gpct2$(PRG_SUFFIX) \
    $(BUILD_DIR)/gpct3$(PRG_SUFFIX)

#
# DMA Support
#
#    include only if the dma library path is defined
#
ifneq (,$(strip $(DMA_LIBRARY_DIR)))

    #
    # add DMA library objects
    #
    include $(DMA_LIBRARY_DIR)/dma.mak

    #
    # examples that use DMA
    #
    TARGETS +=

endif

#
#  OS specific rules and variables
#
include $(OSINTERFACE_DIR)/$(OSINTERFACE_MAKEFILE)


```

What am I doing wrong here?

---

