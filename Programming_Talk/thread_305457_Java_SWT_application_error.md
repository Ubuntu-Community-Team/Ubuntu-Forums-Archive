---
title: "Java SWT application error"
date: 2006-11-23
forum: Programming Talk
---

### Post by hoagie on 2006-11-23
Hello fellow programmers. 
I'm a new programmer to linux so forgive my stupidness.
I tried to create my first java SWT application but I came across some errors that I'm unable to understand and figure out.
When I try to run my program from Eclipse I get the following error.
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-motif-3316 in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.motif.OS.<clinit>(OS.java:18)
	at org.eclipse.swt.graphics.Device.<clinit>(Device.java:115)
	at HelloWorldSWT.main(HelloWorldSWT.java:14)

```

Any advised would be appreciated.
Hoagie

---

### Post by brak on 2006-11-23
did you put the swt library jars in yours project's building path?

---

### Post by hoagie on 2006-11-23
I tried that but I still get the same error message.

---

### Post by hoagie on 2006-11-23
So nobody knows how to solve this?

---

### Post by hod139 on 2006-11-24
You need to install Sun's version of java.  See this [howto]("http://ubuntuforums.org/showthread.php?t=201378") (ignoring the parts on eclipse, unless you want eclipse) for how to set up sun's java.

---

### Post by hoagie on 2006-11-26
It still didn't work. I guess I wasn't meant to be a programmer. ](*,)

---

### Post by shining on 2006-11-27
Maybe you could start over from there:
[http://www.eclipse.org/swt/examples.php](http://www.eclipse.org/swt/examples.php)

---

### Post by eheck on 2006-11-27
The important part being item no 5 at the bottom of that page. You have to give the location where your swt native libraries are in the "-Djava.library.path=...".
"UnsatisfiedLinkError" always means a .so (or an entry point in a .so) can't be found (libswt-motif-3316.so in your case)

---

### Post by hod139 on 2006-11-27
Also, in linux (unlike Windows) the current directory is not part of the system include path.  So you can't just put the .so files in the same directory and expect it to find them.

---

### Post by T_W on 2006-11-27
> **eheck said:**
> The important part being item no 5 at the bottom of that page. You have to give the location where your swt native libraries are in the "-Djava.library.path=...".
"UnsatisfiedLinkError" always means a .so (or an entry point in a .so) can't be found (libswt-motif-3316.so in your case)

I beleive you can also set the LD_LIBRARY_PATH environment variable to the directory containing the shared library.  

-Djava.library.path is a beter solution.

Are you sure you want to be using the Motif version of SWT and not the GTK version?

---

