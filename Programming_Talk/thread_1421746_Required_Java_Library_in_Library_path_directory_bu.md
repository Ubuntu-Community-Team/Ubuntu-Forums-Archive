---
title: "Required Java Library in Library path directory but getting unsatisfied link error"
date: 2010-03-04
forum: Programming Talk
---

### Post by Joe88 on 2010-03-04
*Exception in thread "main" java.lang.UnsatisfiedLinkError: no parport in java.library.path*

The library I'm trying to use is the Parport parallel port library and I have put its .so library file into this library path directory:

**/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/i386/client**

This is my computers java.library.path:

[B]/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/i386/client:
/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/i386:
/usr/lib/jvm/java-6-sun-1.6.0.14/jre/../lib/i386:
/usr/local/java/classes:/usr/java/packages/lib/i386:/lib:/usr/lib[/B]

I'm using the Netbeans and have shown it the location of the library classes in my /usr/local/java/classes directory. I have also added the library to my project and there are no detected errors in the source code.

The read me just says I have to put the library into a library path directory.

Anyone know why I'm getting this error, despite having the library file in a library path directory?

---

### Post by Joe88 on 2010-03-04
**SOLVED**

I thought I had put just the library file into the library path directory, but I had actually put in the the Parport folder.

---

