---
title: "Eclipse/Java problem"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Sequences on 2008-05-13
I did a fresh install of ubuntu so everything would be clean. I use Eclipse regularly but have had the problem of the GUIs not working out. now that I have reinstalled Ubuntu, I hope to make it work. 

So I installed java using 
sudo apt-get install sun-java5-jdk

then I downloaded Eclipse classic and tried to run one of the programs I have written and I get this error:
```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb1de9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb1de98b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb1e2b1bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1f17dce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1f01d77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1f01ef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb1f02136]
#7 [0xb2673bfa]
#8 [0xb266db3b]
#9 [0xb266db3b]
#10 [0xb266b219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78272bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb793bed8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78270ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7884b9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb761f30d]
#16 [0xb26734ab]
#17 [0xb266da64]
#18 [0xb266b219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78272bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb1de9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb1de981e]
#2 /usr/lib/libX11.so.6 [0xb1e2a518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb1e210a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1f010b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1f01303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb1f01fa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb1f02136]
#8 [0xb2673bfa]
#9 [0xb266db3b]
#10 [0xb266db3b]
#11 [0xb266b219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78272bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb793bed8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78270ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7884b9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb761f30d]
#17 [0xb26734ab]
#18 [0xb266da64]
#19 [0xb266b219]

```

No clue what it means, I just want the code I write to work. Thanks in advance.

---

### Post by Xiong Chiamiov on 2008-05-15
What about compiling it through the command line, eg:
```

cd [directory where code is]
javac *.java; java [name of class to run]

```
If you have any package declarations, you'll have to comment them out.

---

