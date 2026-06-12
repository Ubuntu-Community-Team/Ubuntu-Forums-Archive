---
title: "GCJ with Glade"
date: 2007-10-09
forum: Programming Talk
---

### Post by indecisive on 2007-10-09
Does anyone know how to use** glade xml** files in **Java** and compile it with the** GCJ**?  Any suggestions on popular tutorials?

---

### Post by indecisive on 2007-10-10
After I followed the tutorial at [http://people.redhat.com/overholt/nativeeclipse/index.html](http://people.redhat.com/overholt/nativeeclipse/index.html) and installed the eclipse-gcj and glade packages, I received the following errors from my program:

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: libgtkjni-2.10: libglibjni-0.4.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at org.gnu.gtk.Gtk.<clinit>(gtk2.10.jar.so)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.testing.First.main(First.java:26)
```

May anyone help?

---

### Post by chackoc on 2007-12-01
[http://ubuntuforums.org/archive/index.php/t-504139.html](http://ubuntuforums.org/archive/index.php/t-504139.html)

I don't know if you solved this yet but if not the above link indicates why it happens.  

The kludge I ended up using was to symlink everything in /usr/lib/jni to /usr/lib.  Once that was done my sample app compiled and ran.

---

