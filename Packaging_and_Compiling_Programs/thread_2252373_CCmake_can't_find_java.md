---
title: "CCmake can't find java"
date: 2014-11-11
forum: Packaging and Compiling Programs
---

### Post by Daniele_Pezzolla on 2014-11-11
[COLOR=#000000][FONT=Arial]After three days of research I have to give up: my version of Cmake can't find the Oracle JDK. After launching the Cmake this is the error given by the program at the end of the configure phase.[/FONT][/COLOR]
[COLOR=#2B91AF]CMake[/COLOR] [COLOR=#2B91AF]Error[/COLOR] at
 /usr/share/cmake-[COLOR=#800000]2.8[/COLOR]/[COLOR=#2B91AF]Modules[/COLOR]/[COLOR=#2B91AF]FindPackageHandleStandardArgs[/COLOR].cmake:[COLOR=#800000]108[/COLOR]
 (message):
   [COLOR=#2B91AF]Could[/COLOR] NOT find JNI (missing: JAVA_AWT_LIBRARY JAVA_JVM_LIBRARY
   JAVA_INCLUDE_PATH JAVA_INCLUDE_PATH2 JAVA_AWT_INCLUDE_PATH)
 [COLOR=#2B91AF]Call[/COLOR] [COLOR=#2B91AF]Stack[/COLOR] (most recent call first):
   /usr/share/cmake-[COLOR=#800000]2.8[/COLOR]/[COLOR=#2B91AF]Modules[/COLOR]/[COLOR=#2B91AF]FindPackageHandleStandardArgs[/COLOR].cmake:[COLOR=#800000]315[/COLOR]
 (_FPHSA_FAILURE_MESSAGE)
   /usr/share/cmake-[COLOR=#800000]2.8[/COLOR]/[COLOR=#2B91AF]Modules[/COLOR]/[COLOR=#2B91AF]FindJNI[/COLOR].cmake:[COLOR=#800000]251[/COLOR]
 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
   [COLOR=#2B91AF]Wrapping[/COLOR]/[COLOR=#2B91AF]Java[/COLOR]/[COLOR=#2B91AF]CMakeLists[/COLOR].txt:[COLOR=#800000]2[/COLOR] (find_package)*


 [COLOR=#2B91AF]CMake[/COLOR] [COLOR=#2B91AF]Error[/COLOR]: [COLOR=#2B91AF]The[/COLOR] following variables are used in [COLOR=#00008B]this[/COLOR] project, but they are
 set to NOTFOUND.
 [COLOR=#2B91AF]Please[/COLOR] set them or make sure they are set and tested correctly in the [COLOR=#2B91AF]CMake[/COLOR]
 files:


[COLOR=#000000][FONT=Arial]I've tried to change the FindJNI.cmke script as I read on the web but nothing had changed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My OS is ubuntu 14.04, the JDK is the 7th, and Cmake is the latest version.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thank in advance[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Daniele[/FONT][/COLOR]

---

### Post by slickymaster on 2014-11-11
Hi Daniele_Pezzolla, welcome to the forums.

Have you set the JAVA_HOME environment variable with the path to the installed JDK before running CMake?```
export JAVA_HOME=/usr/lib/jvm/java-7-oracle
cmake -DBUILD_SHARED_LIBS=OFF ..
```

---

### Post by Daniele_Pezzolla on 2014-11-12
Set on Off the Shared Libs was the solution. 
Many Thanks man

---

### Post by slickymaster on 2014-11-12
Glad you got it working.

Please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution for this type of problem.

---

