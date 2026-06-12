---
title: "Java Compiling and Android"
date: 2014-07-22
forum: Programming Talk
---

### Post by Sir_Sword on 2014-07-22
These days Java is a bit of an odd duck.  It's nice and fast because when you run a Java program it gets compiled to native on your own machine, but it also uses a lot of memory because of the JVM and self-contained Java applications can be quite large if you package the Oracle JRE with them because you have to include almost the whole JRE.

But Java has lots of other options too.  Alternate JVMs, such as OpenJDK, other JVMs which are much smaller than the Oracle JVM and can be distributed with a Java application to make it self-contained, and programs to compile Java to native so you can distribute them in native format.  This is all third-party software.

Then there's the world of Android.  Up until now Android has used the Dalvik JVM which, like the standard JVM, compiles the Java bytecode to native when the Java app is run.  However Dalvik is going to be replaced by Android Runtime, or ART, which is a new JVM that compiles the bytecode to native when the app is installed instead of when the app is run, so when the app is actually ran it runs from native directly every time.

I was wondering, do any of you think desktop Java will follow a similar path?  Do you think it will ever include a mechanism so that Java applications are compiled at install time, or perhaps at the first run, and then the native binary is used every time going forward instead having to recompile it again each time?

For that matter, do you think Oracle will ever create a version of the JRE that can intelligently and dynamically detect which libraries are needed for a Java application, and allow people to create self-contained applications that only include those parts which are actually needed instead of almost the whole thing?

---

### Post by slooksterpsv on 2014-07-22
I believe it's a developing technology. Granted it's old, but keeps becoming relatively new - in terms of what it can do. Java isn't going away by any means. Oracle may adjust to compile to directly native binary, but that causes issues as for each specific platform there'd have to be a specific binary. To have it recompile for each persons machine would be a pain, a user downloads it, well then that app has to find and download APIs, Plugins, libaries, etc. per user to compile for it's platform. That itself is, ugh, imagine having a large java program, but having to wait while it compiles on an AMD Sempron or an older Intel Atom - that'd take way too long - where it could just be interpreted by the byte code.

Let's imagine that there's a large program and here's how it would flow for compilation:
Intel Core i7 Haswell - 6 sec.
Intel Core i5 3rd Gen - 8 sec.
AMD FX-8350 - 10 sec.
Intel Core i3 3rd Gen - 15 sec.
AMD A6-5200 - 1 min.
Intel Atom Baytrail - 3 min.
AMD Sempron - 7 min.
Intel Atom - 14 min.
Older CPUs - 15+ min.

Wouldn't seem feasible to do.

---

### Post by slooksterpsv on 2014-07-22
I believe it's a developing technology. Granted it's old, but keeps becoming relatively new - in terms of what it can do. Java isn't going away by any means. Oracle may adjust to compile to directly native binary, but that causes issues as for each specific platform there'd have to be a specific binary. To have it recompile for each persons machine would be a pain, a user downloads it, well then that app has to find and download APIs, Plugins, libaries, etc. per user to compile for it's platform. That itself is, ugh, imagine having a large java program, but having to wait while it compiles on an AMD Sempron or an older Intel Atom - that'd take way too long - where it could just be interpreted by the byte code.

Let's imagine that there's a large program and here's how it would flow for compilation:
Intel Core i7 Haswell - 6 sec.
Intel Core i5 3rd Gen - 8 sec.
AMD FX-8350 - 10 sec.
Intel Core i3 3rd Gen - 15 sec.
AMD A6-5200 - 1 min.
Intel Atom Baytrail - 3 min.
AMD Sempron - 7 min.
Intel Atom - 14 min.
Older CPUs - 15+ min.

Wouldn't seem feasible to do.

---

### Post by ofnuts on 2014-07-23
> These days Java is a bit of an odd duck.  It's nice and fast because  when you run a Java program it gets compiled to native on your own  machine, but it also uses a lot of memory because of the JVM and  self-contained Java applications can be quite large if you package the  Oracle JRE with them because you have to include almost the whole JRE.

Java is not compiled when it's run. It's compiled when you transform your source text to bytecode. When you run the code the bytecode is translated to machine code, but this is much faster than a real compilation.

One baisc principle of the the JRE is that you have one JRE installed on your target machines and don't need to provide a full JRE with each application. So your applications are small, and updates are small. Android comes with a full Java JRE (one could almost says that Android is a just a JRE...)

---

### Post by Sir_Sword on 2014-07-23
> **ofnuts said:**
> One baisc principle of the the JRE is that you have one JRE installed on your target machines and don't need to provide a full JRE with each application. So your applications are small, and updates are small. Android comes with a full Java JRE (one could almost says that Android is a just a JRE...)

That's true ideally, but I believe many Windows users still don't have a JRE installed or even know what one is or want to be bothered to download and install one, which is why an application may want to bundle a JRE with their program, to avoid the hassle and make the whole process more transparent to the user.

---

