---
title: "eclipse UnsatisfiedLinkError problem"
date: 2007-07-18
forum: Programming Talk
---

### Post by js9863 on 2007-07-18
I solved the problem by manually creating a link:

```
ln -s /usr/lib/jni/libglibjni-0.4.so  /lib/libglibjni-0.4.so[\CODE] 


----------------------------------------------------------------------------------------------------

Hello everyone,

I'm trying to build a simple GTK application with java-gnome. The problem occurs when I try to run it. I get the following error:

[CODE]
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jni/libgtkjni-2.10.so: libglibjni-0.4.so: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.gnu.gtk.Gtk.<clinit>(Gtk.java:214)
	at org.testing.GTK_HelloWorld.main(GTK_HelloWorld.java:28)

```

Could someone tell me why I'm getting the above error? The libraries do exists in:
```

:~$ locate libglibjni && locate libgtkjni
/usr/lib/jni/libglibjni.so
/usr/lib/jni/libglibjni-0.4.so
/usr/lib/jni/libgtkjni.so
/usr/lib/jni/libgtkjni-2.10.so

```

Thanks in advance.

---

### Post by mrlem on 2007-11-02
Hi,

  Unless I'm mistaken, this seems to be a packaging error in Ubuntu : IMHO, /usr/lib/jni should be in the LD_LIBRARY_PATH (or in /etc/ld.so.conf.d/something).

  One may argue that the java.library.path should do the trick, which is partially true : it works when loading the library from Java itself, but not when a library holds a reference to another library - like libgtkjni & libglibjni.

  That is the problem you encounter.

  Adding glib to your /usr/lib solves the issue because /usr/lib (and /lib) are the default locations the loader looks into. But it seems a dirty hack to me (I wouldn't expect anybody to do this in order to deploy an application of mine).

  maybe it's cleaner to have your java application launched from a shell script that defines the following :

```
export LD_LIBRARY_PATH="/usr/lib/jni"
```

  I'm looking forward seeing that done by default in the future (has this been reported ? couldn't see any bug report on this subject)

---

