---
title: "java.lang.ClassFormatError in Eclipse"
date: 2007-08-15
forum: Programming Talk
---

### Post by Coder_wannabe on 2007-08-15
I am trying to compile a hello world program but i keep getting:

Exception in thread "main" java.lang.ClassFormatError: HelloWorld (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

I think its because i am using the java 6 but eclipse is using java 5.  Is there any thing i can do from the command line to allow eclipse to use the correct version of java?

---

### Post by Damiel on 2007-08-16
Check that the java-6-sun JRE is added in the list of installed JREs. In Eclipse, go to Windows->Preferences->Java->Installed JREs. Mine's location is */usr/lib/jvm/java-6-sun*. Then, change your JRE system library in your project.

---

