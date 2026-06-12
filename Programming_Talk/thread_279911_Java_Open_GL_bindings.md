---
title: "Java Open GL bindings"
date: 2006-10-18
forum: Programming Talk
---

### Post by KoalaOfDoom on 2006-10-18
Could some generous soul please give me the step by step process of installing the Java Open GL bindings ([JOGL](https://jogl.dev.java.net/)). Both for runtime and development.

I've tried *everything*. I put the jogl.jar and the four .so files in every */lib/ directory I've been able to find, but no luck. And I've exported their location to the CLASSPATH and another variable I can't remember the name of, so they should be able to find it (how do I remove that?). One possible solution is to put it in the JDK folder, but I don't know where that is. I have ANT & ANTLR.

Oh, and how do you make Firefox start Java Web Start apps with javaws? It wants me to navigate to the executable, I just want to enter javaws.

Thanks in advance for any help.

EDIT: Just to be clear, what happens now when I try to compile is that it doesn't find javax.media.opengl (or whatever it's name is).

---

### Post by starsky on 2006-10-18
Put these files in /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/

$ ls -al /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/
total 3264
-rw-r--r-- 1 root root   8176 2005-12-17 21:17 dnsns.jar
-rw-r--r-- 1 root root 995350 2006-09-20 03:09 jogl.jar
-rw-r--r-- 1 root root  10107 2006-09-20 04:03 libjogl_awt.so 
-rw-r--r-- 1 root root 185584 2006-09-20 04:03 libjogl_cg.so 
-rw-r--r-- 1 root root   6421 2006-09-20 04:03 libjogl_drihack.so 
-rw-r--r-- 1 root root 962937 2006-09-20 04:03 libjogl.so
-rw-r--r-- 1 root root 802394 2006-05-15 10:02 localedata.jar
-rw-r--r-- 1 root root 153235 2005-12-17 21:00 sunjce_provider.jar
-rw-r--r-- 1 root root 175811 2005-12-17 21:00 sunpkcs11.jar


Hope it helps.

---

