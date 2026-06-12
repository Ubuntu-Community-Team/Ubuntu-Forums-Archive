---
title: "java serial rxtx again - intrepid install"
date: 2008-12-08
forum: Programming Talk
---

### Post by mikecalder on 2008-12-08
Yet another install failure.

Installed the Intrepid package (librxtx) to develop Java programs with serial ports. As installed, even compiles don't work.

I copied RXTXcomm.jar from /usr/share/java to /usr/lib/jvm/java-6-sun/jre/lib/ext, and with that I can compile programs using the javacomm api with an include of gnu.io.*

Unfortunately, when they run, we get the exception:
      Exception in thread "main" java.lang.NoClassDefFoundError: gnu/io/CommPortIdentifier

which tells us that RXTX is not installed properly.  I've looked in the RXTXcomm.jar, and yes, gnu/io/CommPortIdentifier is there.

I'm on a fully up-to-date Intrepid system on an AMD64 processor.

Has anybody got the slightest idea of how I can go on from here to get this blessed thing working?

---

### Post by mikecalder on 2008-12-10
Not to worry; I've bypassed it.

In case anyone else gets similar problems, I've found a much easier way of communicating with serial ports in Java than struggling with RXTX or anything else.

Wrote a simple handler program in C that talks to the comms port, and have that talking to the Java program via a simple socket (C program acting as server, java as client).  To make it all automatic so no nonsense about having to start up the server separately or have it as a daemon, registered it with inetd.

Why not use JNI interface to talk directly from Java to the C code?  Have you ever *looked* at the JNI mechanism? and how you have to convert strings?  ***Blech***.

Isn't Linux wonderful?  There's *always* a way.

---

