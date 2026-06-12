---
title: "unable to run a jar file"
date: 2008-10-16
forum: Programming Talk
---

### Post by arunvir on 2008-10-16
I try running the following command and get the following error.
Could someone shed light on how to get the remaining 3 errors to be displayed and can someone tell me why am I getting this error as the same jar file runs error free in windows.


java -jar /media/sda2/EBooks\ and\ Help\ Manuals/java2certification/pgjc2e-engine.jar
Exception in thread "main" java.lang.ExceptionInInitializerError
        at no.rwr.engine.SessionGUI.<init>(SessionGUI.java:130)
        at no.rwr.engine.App.<init>(App.java:53)
        at no.rwr.engine.App.main(App.java:15)
Caused by: java.lang.NullPointerException
        at no.rwr.engine.GUIStyle.<clinit>(GUIStyle.java:25)
        ... 3 more


the java version is:-
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

operating system is kubuntu hardy 8.04

In windows I have java version 1.6.05
I don't think that could be the reason
The jar file actually contains some scjp questions that I want to prepare for

Help will be greatly appreciated.

:):)

---

### Post by cl333r on 2008-10-16
```

Caused by: java.lang.NullPointerException
at no.rwr.engine.GUIStyle.<clinit>(GUIStyle.java:25)

```
Looks like it's the application's fault. If you have the source code have a look at line 25 from GUIStyle.java.

---

### Post by arunvir on 2008-10-16
Even I thought like that
But the very same code runs without even a warning in windows.

I wonder if it is the code or the implementation of certain stuff in java that let down the usage in linux

I have tried it with openjdk as well

I think I'll try the 1.4 java 
ll post results

---

### Post by SeanHodges on 2008-10-16
The MANIFEST file in that jar indicates that it was actually compiled in Linux:

```
Manifest-Version: 1.0
Created-By: 1.4.1 (Blackdown Java-Linux Team)
Main-Class: no.rwr.engine.App
```

If you contacted the authors, they might be able to offer you some advice on getting it working. Or at least offer the source code so you can post it up and maybe get some more useful help from us.

[http://www.ii.uib.no/~khalid/pgjc2e/authors.html](http://www.ii.uib.no/~khalid/pgjc2e/authors.html)

---

### Post by arunvir on 2008-10-16
Take a gun and shoot me and I might say thank you

Holy god
It worked flawlessly in jdk1.5 under linux


Both openjdk6
and sun jdk6

produced errors

But I did get some output like follows

Can anyone tell me why??


> Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7f41767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7f418b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb1c9d1bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1d8ddce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1d77d77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1d77ef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb1d78136]
#7 [0xb25f0c1b]
#8 [0xb25eab3b]
#9 [0xb25eab3b]
#10 [0xb25e8219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77a82bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78bced8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77a80ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7805b9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb759c30d]
#16 [0xb25f04bb]
#17 [0xb25eaa64]
#18 [0xb25e8219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77a82bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7f41767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7f4181e]
#2 /usr/lib/libX11.so.6 [0xb1c9c518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb1c930a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1d770b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1d77303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1d77fa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb1d78136]
#8 [0xb25f0c1b]
#9 [0xb25eab3b]
#10 [0xb25eab3b]
#11 [0xb25e8219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77a82bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78bced8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77a80ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7805b9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb759c30d]
#17 [0xb25f04bb]
#18 [0xb25eaa64]
#19 [0xb25e8219]


What could have been the reason???

---

### Post by Reiger on 2008-10-16
Looks like the Java app is crossing the boundaries of its privileges, which is to say: it (either) requires root privileges to do what it wants to, or something else has been holding an exclusive lock on these dirs (running two instances of the same app/code at the same time, perhaps?).

---

### Post by arunvir on 2008-10-17
Well then does java 5 have commands that have the privileges to override user rights(a normal user with the ability to perform tasks of an administrator.......) that means anyone running java 5 must be able to indirectly access all the resources in a system........ even by passing of system resources......

further I think this is only a SCJP mock and in no way has to do anything with accessing a system resource(probably gaining some kind of handles to a drawing area in the screen where the stuff is to be displayed which is common to all apps, I believe......)

might be something was removed from java 6 that could be causing the following error.....

I don't know whether some kind of Initialization that was allowed in earlier versions of java might has been removed in java 6 due to security reasons and that could be causing the problem.That means older java programs cannot be run in new java 6 due to improved security.

Further the term portability of java apps becomes nullified as the code itself ain't getting through all the releases of java SDK itself..... even if compilation of such programs in java 6 cannot be allowed, shouldn't atleast running of such programs be allowed through proper adjustment with the Java runtime???? 

am I right or wrong???

---

