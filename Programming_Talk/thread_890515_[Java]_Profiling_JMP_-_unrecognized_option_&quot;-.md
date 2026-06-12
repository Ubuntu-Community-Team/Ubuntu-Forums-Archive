---
title: "[Java] Profiling: JMP - unrecognized option &quot;-Xrunjmp&quot;"
date: 2008-08-15
forum: Programming Talk
---

### Post by verteidi on 2008-08-15
Hello everyone,

I am having a problem using JMP (not the data analysis software) for profiling my Java programs in Ubuntu and I'd be glad if someone could point me in the right direction.

I've installed the package "jmp" with apt and then followed the instructions in the JMP users guide [[COLOR="Blue"]here[/COLOR]]("http://www.khelekore.org/jmp/").

Running
```
java -Xrunjmp:help
```
in a terminal prints the following usage message:
```
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

```
According to the users guide, I should get something like:
```
jmp/0.51.1 initializing...
```
followed by instructions on how to run JMP.

I have made sure that the library "libjmp.so" is in the "LD_LIBRARY_PATH":
```
echo $LD_LIBRARY_PATH
/usr/lib/
```
Checking the supported X arguments by running
```
java -X
```
prints
```
  -Xms<size>         set initial heap size
  -Xmx<size>         set maximum heap size
  -Xss<size>         set thread stack size

```
which might indicate, that the option "-Xrunjmp" is simply not recognized? Also, JMP depends on the GTK+ libraries, could there be a problem with that?
I am running Java version 1.5.0 and JMP version 0.51-1.

I have tried searching this forum and google for "JMP" and related problems but couldn't find any answer so far. I would really appreciate any help that will enable me to profile my Java programs. Thank you!

---

### Post by tinny on 2008-08-15
Sorry I cant help you with JMP.

But, the NetBeans IDE has an excellent Application profiler built in.

[http://www.netbeans.org/features/java/profiler.html](http://www.netbeans.org/features/java/profiler.html)

Ive personally used it to Profile Java Swing and J2EE applications.

---

### Post by verteidi on 2008-08-15
Thank you for your reply, I will give NetBeans a shot. Any profiler would be sufficient for me at this point.

---

### Post by tinny on 2008-08-15
I seem to recall that you can attach the NetBeans profiler to a running JVM instance. This means that you will not have to port your Java application into a NetBeans IDE project. You can just use it as an external profiling tool.

---

### Post by verteidi on 2008-08-15
Thanks again, but I already imported my current project into NetBeans and must say I am astonished by its simplicity and features. So far I have been using eclipse only and found it to be difficult to use at times, especially when it comes to profiling (TPTP is very difficult to install for the average user, I think) - although it is a good IDE as well. NetBeans, however seems to be a lot more straightforward. And, not to forget, the profiler is perfect for my needs.
Great advice!

---

### Post by Shin_Gouki2501 on 2008-08-15
IT depends what and how you search but try to look up google for JMX. Sometimes its an nice option!

---

### Post by txcrackers on 2008-08-15
Note the error message: *gij* is **not** the Sun JVM, so the -X options will most likely not work. You need to ensure that you're actually running the Sun JVM.

---

### Post by verteidi on 2008-08-16
Well, now that I am running NetBeans, the JVM switched to OpenJDK VM, but I am sure it was the Sun JVM before. My actual problem (how use profiling) is solved and I personally I don't need an answer to my initial question about JMP, but maybe other users have come upon the same problem and an answer would be useful to them. Thanks again for your efforts.

---

