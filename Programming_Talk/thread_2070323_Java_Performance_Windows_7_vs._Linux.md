---
title: "Java Performance Windows 7 vs. Linux"
date: 2012-10-12
forum: Programming Talk
---

### Post by Kentucky88 on 2012-10-12
Has anyone done any benchmarks on Java 6/7 performance on Windows 7 vs. Linux?  This video here:

[http://www.youtube.com/watch?v=pXOMw9bQoPU](http://www.youtube.com/watch?v=pXOMw9bQoPU)

Claims that Java performs much slower in Linux vs. Windows.  (However, obviously that test is heavy on graphics and I would guess it comes down to graphics driver optimization.)  But for non-graphics applications (data mining), would Linux be much slower than Windows?  Fortunately, I can run on either platform without having to recompile so it's not a big deal, just curious if anyone has studied Java 6/7 performance Win vs. Linux.

---

### Post by CptPicard on 2012-10-12
I'm pretty sure the difference really is about the graphics. Assuming the same machine, The JVM JIT-compiles the same code which then runs on the CPU... I can't imagine the rest of the Java runtime having huge differences in performance between OSes.

---

### Post by litiform on 2012-10-12
I've stopped using Java as a plugin for browsers. I isn't secure.

What things do you guys need to use Java for? Since I've uninstalled it, I haven't found a single thing I need it for (thankfully)!

---

### Post by CptPicard on 2012-10-12
> **litiform said:**
> 
What things do you guys need to use Java for? Since I've uninstalled it, I haven't found a single thing I need it for (thankfully)!

I use Java at work on (mostly Linux) servers to run major infrastructure that runs our world as we know it, as do a lot of other people.

---

### Post by trent.josephsen on 2012-10-12
Minecraft.

Seriously, Java is a lot more useful NOT in a browser. Android comes to mind. So does JSP.

---

### Post by CptPicard on 2012-10-12
> **trent.josephsen said:**
> So does JSP.

... and so does whatever you end up seeing in that JSP, or hopefully not within a JSP anymore in this day and age.

---

### Post by dixcuxx on 2013-06-30
> **CptPicard said:**
> I'm pretty sure the difference really is about the graphics. Assuming the same machine, The JVM JIT-compiles the same code which then runs on the CPU... I can't imagine the rest of the Java runtime having huge differences in performance between OSes.

How about a pure calculations program? Just a lot of calculations in a lot of data in arrays, would you expect big different?

---

### Post by Mikeb85 on 2013-07-01
Watching the video, I'm curious how he installed Linux.  Is he running Wubi?  Also, Linux Mint is one of the slowest (the slowest?) Linux distros I've used.  

I do have a laptop running Intel graphics, and Java games as well as native games run great.  Java performance seems very good, I use OpenJDK 7, though not in the browser.

---

### Post by Mikeb85 on 2013-07-01
> **litiform said:**
> I've stopped using Java as a plugin for browsers. I isn't secure.

What things do you guys need to use Java for? Since I've uninstalled it, I haven't found a single thing I need it for (thankfully)!

Android development, servers, some GUI apps.  The JVM (Java Virtual Machine) is probably the single most portable and scalable development environment, alot of infrastructure runs on the JVM.  I personally use Clojure, not Java the language, but Java the environment is incredibly useful.

---

### Post by CptPicard on 2013-07-01
> **dixcuxx said:**
> How about a pure calculations program? Just a lot of calculations in a lot of data in arrays, would you expect big different?

No, I would actually expect them to run pretty much all the same. This of course assumes that it really is just JVM internal stuff being used and not much system calls to the OS, after which things would become OS-dependent.

---

### Post by slickymaster on 2013-07-02
Here's a pretty interesting read on the subject: [Roy Longbottom's Java Offline Benchmarks]("http://www.roylongbottom.org.uk/javadraw.htm")

---

### Post by Leuchten on 2013-07-02
Going solely based on [the benchmarks game]("http://benchmarksgame.alioth.debian.org/u64q/which-programs-are-fastest.php"), java is about the fastest language you can find on linux that isn't natively compiled, and it beats a good few that are. I wouldn't worry about java performance on linux too much, just keep in mind that java as it is now is not suited to the many tiny instances application model, so don't try for that.

---

### Post by CptPicard on 2013-07-02
> **Leuchten said:**
> Going solely based on [the benchmarks game]("http://benchmarksgame.alioth.debian.org/u64q/which-programs-are-fastest.php"), java is about the fastest language you can find on linux that isn't natively compiled, 

Well, actually, it is natively compiled... that's what the JIT-compiler does. Not straight from the text of the original Java program, but what ends up running on the processor is native code.

---

### Post by Leuchten on 2013-07-02
> **CptPicard said:**
> Well, actually, it is natively compiled... that's what the JIT-compiler does. Not straight from the text of the original Java program, but what ends up running on the processor is native code.

Well, not exactly. A java program will always start off as completely interpreted, and as functions cross their call threshold they become jitted into native code. If they are used particularly heavily they will be jitted again with a more aggressive set of optimizations and so on. On the other hand, functions that are not used enough may never be jitted before the program exits.

---

### Post by RoyLongbottom on 2013-11-28
[FONT=Verdana]Some more results and benchmarks (others can run via DL from the following):[/FONT]

[FONT=Verdana]JavaDraw JDK 6/7, JRE 6/7 Win, Ubuntu - Win better on one PC but Ubuntu better on another.[/FONT]
[FONT=Verdana][http://www.roylongbottom.org.uk/javadraw.htm#anchor3](http://www.roylongbottom.org.uk/javadraw.htm#anchor3) [/FONT]

[FONT=Verdana]JavaDraw JRE 6,7,8 [/FONT]
[FONT=Verdana][http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm#anchor17](http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm#anchor17) [/FONT]

[FONT=Verdana]Number crunching JRE 6,7,8, Cacao, JamVM[/FONT]
[FONT=Verdana][http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm#anchor15](http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm#anchor15) [/FONT]

[FONT=Verdana]Number Crunching Java 6, Win, Linux, off-line, on-line[/FONT]
[FONT=Verdana][http://www.roylongbottom.org.uk/whetstone%20results.htm#anchorjava2](http://www.roylongbottom.org.uk/whetstone%20results.htm#anchorjava2) [/FONT]

---

