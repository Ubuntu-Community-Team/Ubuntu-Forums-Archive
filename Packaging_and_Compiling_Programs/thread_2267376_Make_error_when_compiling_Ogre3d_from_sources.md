---
title: "Make error when compiling Ogre3d from sources"
date: 2015-03-01
forum: Packaging and Compiling Programs
---

### Post by Andika_Demas_Riyan on 2015-03-01
Hi, I got some error when i run make command to build Ogre3d Application.. the error is as follows:

```
[COLOR=#000000][FONT=monospace Monaco]Linking CXX executable ../../bin/OgreXMLConverter../../lib/libOgreMainStatic.a(compile_OgreMain_2.cpp.o): In function `Ogre::DeflateStream::init()':compile_OgreMain_2.cpp:(.text+0x7c907): warning: the use of `tmpnam' is dangerous, better use `mkstemp'/usr/bin/ld: ../../lib/libOgreMainStatic.a(compile_OgreMain_0.cpp.o): undefined reference to symbol 'dlclose@@GLIBC_2.2.5'//lib/x86_64-linux-gnu/libdl.so.2: error adding symbols: DSO missing from command linecollect2: error: ld returned 1 exit statusmake[2]: *** [bin/OgreXMLConverter] Error 1make[1]: *** [Tools/XMLConverter/CMakeFiles/OgreXMLConverter.dir/all] Error 2make: *** [all] Error 2[/FONT][/COLOR]
```

and if you would like to see my thread there, please refer to this link..
> [http://www.ogre3d.org/forums/viewtopic.php?f=2&t=82858&p=515316#p515316](http://www.ogre3d.org/forums/viewtopic.php?f=2&t=82858&p=515316#p515316)

actually at first i still confuse regarding the -lnosys in the linker.. but as in the above thread it seems that i can only delete the -lnosys and run fine.. 

thank you

---

