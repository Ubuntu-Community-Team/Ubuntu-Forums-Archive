---
title: "Java + GTK - Unsatisfied Link"
date: 2007-01-16
forum: Programming Talk
---

### Post by Seine on 2007-01-16
I'm getting started with Java and GTK and have hit a wall.

Installed packages include libgtk-java, libgtk-java-gcj and libgtk-jni. My classpath includes /usr/share/java/gtk2.10.jar and /usr/share/java/glib0.4.jar. My java.library.path is /usr/lib/jni/, which allows references to libglibjni-0.4.so.

When I execute the following code:```
        Window window = new Window();
        window.setTitle("Seine Was Here");
```I get the following error```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jni/libglibjni-0.4.so: /usr/lib/jni/libglibjni-0.4.so: undefined symbol: g_type_depth
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.gnu.glib.Struct.<clinit>(Struct.java:85)
```

I noticed while compiling this message that I don't yet have the libgtk-java-doc package. I'll install and read that and post back.

---

### Post by Seine on 2007-01-16
No luck with that package. They are code samples for the API. *Very handy* but they too suffer from this unresolved dependency. 

Can anyone point me in the right direction?

Thanks!

---

### Post by ZylGadis on 2007-01-16
Why don't you just use standard Swing + the GTK plaf? Works great here. SWT and all the native calls it makes (I assume this is the case, as you need a jni lib) are an abomination.

---

### Post by Seine on 2007-01-16
Can I use standard Swing to embed an applet in the Gnome panel?

---

### Post by ZylGadis on 2007-01-16
I have not done that, but I don't see a reason you would not be able to. Just call the respective GTK method through JNI and don't mess with anything else external.

---

### Post by samir85 on 2007-01-17
> **Seine said:**
> I'm getting started with Java and GTK and have hit a wall.

Installed packages include libgtk-java, libgtk-java-gcj and libgtk-jni. My classpath includes /usr/share/java/gtk2.10.jar and /usr/share/java/glib0.4.jar. My java.library.path is /usr/lib/jni/, which allows references to libglibjni-0.4.so.

When I execute the following code:```
        Window window = new Window();
        window.setTitle("Seine Was Here");
```I get the following error```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jni/libglibjni-0.4.so: /usr/lib/jni/libglibjni-0.4.so: undefined symbol: g_type_depth
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.gnu.glib.Struct.<clinit>(Struct.java:85)
```

I noticed while compiling this message that I don't yet have the libgtk-java-doc package. I'll install and read that and post back.

Hey, experienced this too. There's a bug in Edgy so that the java gtk bindings are not working.
See here [https://bugs.launchpad.net/ubuntu/+source/glib-java/+bug/70113](https://bugs.launchpad.net/ubuntu/+source/glib-java/+bug/70113)

Unfortunately, the Ubuntu devs don't seem that they want to do anything about it, so you most likely have to wait until Feisty until this is fixed ...

---

