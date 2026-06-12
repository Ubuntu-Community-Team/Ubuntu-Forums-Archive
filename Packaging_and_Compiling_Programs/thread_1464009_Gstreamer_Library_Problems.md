---
title: "Gstreamer Library Problems"
date: 2010-04-27
forum: Packaging and Compiling Programs
---

### Post by Crump3t on 2010-04-27
I'm trying to compile the basic gstreamer example seen here [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-init.html]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-init.html").

I have linked everything so far that has error-ed (glib and libxml) however upon compiling I receive the errors: 

/home/david/NetBeansProjects/Simple Mp3/main.cpp:11: undefined reference to `gst_init'
/home/david/NetBeansProjects/Simple Mp3/main.cpp:13: undefined reference to `gst_version'
collect2: ld returned 1 exit status

I can't see anything missing and those are the only errors I get.

Here is my make file (I'm using netbeans on 10.4):

```
#
# Generated Makefile - do not edit!
#
# Edit the Makefile in the project folder instead (../Makefile). Each target
# has a -pre and a -post target defined where you can add customized code.
#
# This makefile implements configuration specific macros and targets.


# Environment
MKDIR=mkdir
CP=cp
CCADMIN=CCadmin
RANLIB=ranlib
CC=gcc
CCC=g++
CXX=g++
FC=
AS=as

# Macros
CND_PLATFORM=GNU-Linux-x86
CND_CONF=Debug
CND_DISTDIR=dist

# Include project Makefile
include Makefile

# Object Directory
OBJECTDIR=build/${CND_CONF}/${CND_PLATFORM}

# Object Files
OBJECTFILES= \
	${OBJECTDIR}/main.o

# C Compiler Flags
CFLAGS=

# CC Compiler Flags
CCFLAGS=
CXXFLAGS=

# Fortran Compiler Flags
FFLAGS=

# Assembler Flags
ASFLAGS=

# Link Libraries and Options
LDLIBSOPTIONS=-L/usr/lib/glib-2.0 -L/usr/lib/libxml++-2.6 -L/usr/lib/gstreamer-0.10 

# Build Targets
.build-conf: ${BUILD_SUBPROJECTS}
	${MAKE}  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/simple_mp3

dist/Debug/GNU-Linux-x86/simple_mp3: ${OBJECTFILES}
	${MKDIR} -p dist/Debug/GNU-Linux-x86
	g++ -o ${CND_DISTDIR}/${CND_CONF}/${CND_PLATFORM}/simple_mp3 ${OBJECTFILES} ${LDLIBSOPTIONS} 

${OBJECTDIR}/main.o: nbproject/Makefile-${CND_CONF}.mk main.cpp 
	${MKDIR} -p ${OBJECTDIR}
	${RM} $@.d
	$(COMPILE.cc) -g -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -MMD -MP -MF $@.d -o ${OBJECTDIR}/main.o main.cpp

# Subprojects
.build-subprojects:

# Clean Targets
.clean-conf: ${CLEAN_SUBPROJECTS}
	${RM} -r build/Debug
	${RM} dist/Debug/GNU-Linux-x86/simple_mp3

# Subprojects
.clean-subprojects:

# Enable dependency checking
.dep.inc: .depcheck-impl

include .dep.inc
```

I'm probably missing something simple, but I can't work out what it is. :confused:

Thanks.

---

### Post by SevenMachines on 2010-04-28
hi there. the error is telling you that gcc isnt linking against the gstreamer-0.10 library. looking at the makefile it seems your accidentally adding directories to search for libraries ( the -L/usr/lib/gstreamer-0.10 bit ) rather than actually linking to the library itself ( -lgstreamer-0.10 which is what you want to do ). I dont know where in Netbeans you add the actually libraries to link to sorry 
Just on a side note you may want to instead use pkg-config to generate all the includes and linking for gstreamer, again, i dont know where you add this in netbeans ( sorry again! ) By adding
`pkg-config --cflags --libs gstreamer-0.10`
to the command line ( for a quick explanation [see here]("http://ubuntuforums.org/showpost.php?p=9181671&postcount=2") )

---

### Post by Crump3t on 2010-04-28
> **SevenMachines said:**
> hi there. the error is telling you that gcc isnt linking against the gstreamer-0.10 library. looking at the makefile it seems your accidentally adding directories to search for libraries ( the -L/usr/lib/gstreamer-0.10 bit ) rather than actually linking to the library itself ( -lgstreamer-0.10 which is what you want to do ). I dont know where in Netbeans you add the actually libraries to link to sorry 
Just on a side note you may want to instead use pkg-config to generate all the includes and linking for gstreamer, again, i dont know where you add this in netbeans ( sorry again! ) By adding
`pkg-config --cflags --libs gstreamer-0.10`
to the command line ( for a quick explanation [see here]("http://ubuntuforums.org/showpost.php?p=9181671&postcount=2") )

Thanks for your help, I added the -lgstreamer-0.10 to the library line and the program compiles and runs fine.

---

