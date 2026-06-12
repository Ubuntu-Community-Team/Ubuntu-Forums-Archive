---
title: "make[2]: *** No rule to make target 'make.so', needed by 'libneed.so'. Stop."
date: 2013-09-29
forum: New to Ubuntu
---

### Post by bradford2 on 2013-09-29
Hello,

I am just beginning with ubuntu. I have been working on satisfying all of the dependencies required from running 'make'. For the most part, when I run into an dependency (I believe) issue, say:
```

/usr/inlcude/RthCommon/Logger.h:25:28: fatal error: log4cxx/logger.h: No such file or directory
compilation terminated
make[2]: *** [CMakeFiles/PeakFinder2Plugin.dir/ReconCustomScriptPlugin.cpp.o] Error 1
make[1]: *** [CMakeFiles/PeakFinder2Plugin.dir/all] Error 2
make: *** [all] Error 2 
```

I used 'aptitude search log4cxx' which would yield something like 'liblog4cxx10-dev' of a few options which would then allow for 'sudo apt-get install liblog4cxx10-dev' and I would continue running 'make' until further dependency issues arrised which I would get past in a similar manner.

I believe I am running into a similar problem later in the 'make' process, however I an unable to get around it with any commands I know:

```

user@ubuntu:~/Desktop/trackingPackage/trackingRecon/scriptPluginPeakFinder2/build$ make
make[2]: *** No rule to make target `/usr/local/qwt-6.1.0-rc3/lib/libqwt.so', needed by `libPeakFinder2Plugin.so'.  Stop.
make[1]: *** [CMakeFiles/PeakFinder2Plugin.dir/all] Error 2
make: *** [all] Error 2 
```

I attempted: 
```

aptitude search qwt 
```
which yielded 'libqwt-dev' and other similar derivations of 'libqwt ... -dev'
each of which I then ran:
```

sudo apt-get install libqwt-dev 
```

I have tried updating with sudo apt-get update and a number of other things, but I can't find a solution in any of the threads. 
This is my first time posting here, so please also let me know if/how I should reformat my question to fit the standard syntax.
Thank you!

---

### Post by steeldriver on 2013-09-29
Hello and welcome to the forums

It will make your posts easier to read if you enclose any terminal output / code fragments in [CODE]...[&#8725;CODE] tags (you can type them, or select the text and then press the # button on the post editor).

It would be easier to answer your question if you post the relevant section of your Makefile - however yes, it sounds like you are missing some library or LPATH directives in the *link phase* of one or more of your targets.

---

### Post by bradford2 on 2013-09-30
Thank you for the pointers. The make file is on the longer side but this is a portion of the Target Rules section:

```

# Target rules for targets named PeakFinder2Plugin


# Build rule for target.
PeakFinder2Plugin: cmake_check_build_system
	$(MAKE) -f CMakeFiles/Makefile2 PeakFinder2Plugin
.PHONY : PeakFinder2Plugin


# fast build rule for target.
PeakFinder2Plugin/fast:
	$(MAKE) -f CMakeFiles/PeakFinder2Plugin.dir/build.make CMakeFiles/PeakFinder2Plugin.dir/build
.PHONY : PeakFinder2Plugin/fast


CustomScriptPlugin.o: CustomScriptPlugin.cpp.o
.PHONY : CustomScriptPlugin.o


# target to build an object file
CustomScriptPlugin.cpp.o:
	$(MAKE) -f CMakeFiles/PeakFinder2Plugin.dir/build.make CMakeFiles/PeakFinder2Plugin.dir/CustomScriptPlugin.cpp.o
.PHONY : CustomScriptPlugin.cpp.o


CustomScriptPlugin.i: CustomScriptPlugin.cpp.i
.PHONY : CustomScriptPlugin.i 
```

---

