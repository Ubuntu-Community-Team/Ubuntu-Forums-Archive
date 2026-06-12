---
title: "Why JVM5 is slower in Linux than in Windows?"
date: 2007-01-18
forum: Programming Talk
---

### Post by Dislimit on 2007-01-18
Hi, all:
It really surprised me that Java code runs much faster (at least for not so large
program) in Windows than in Linux.

Recently I tested the speed of part of my learning package, whose task is to
parse a 10MB (about 210,000 lines) text file to extrace some figures ,discretize them and put the
result into a new file.

With the same model of i386 PC (P4 2.8G, 1GB DDR), same version of Sun Java (1.5.0_6), 
same program (class files compiled by 1.5.0_10), same input data
file, both run from cmd line using default settings (additional option for
java), here is the recorded average execution time
(every time restart the program, not keep running):
OS \t Main \t Whole
Ubuntu5.10: 6s 8s
Windows XP: 1.6s 2-3s
Ubuntu(CPP): ?  3.5s

The 'main' execution time is recorded inside Java program just to evaluate the most
costly part (scan line by line, and parse numbers), so it has removed the
overhead of the startup. The 'whole' time is displayed by 'time' utility. 
How can the difference be so large? I tried other Linux JRE like IBM and
JRocket with the same code, the result is no better, if not worse.
Is it because different GC strategy setting of
Linux and Windows version or something?

The last line of the table is one more thing to mention, I write an equivalent CPP version with common input stream, 
which takes 4s (whole) to run, slower than my Java version (if runs on WinXP), where I use my own Scanner class
(Sun's Scanner is too slow). Does CPP computation program also run faster in Windows? I don't know.
Anyway, Ubuntu has been my main OS for a year.

---

### Post by phossal on 2007-01-18
I installed the JDK [this way]("http://ubuntuforums.org/showthread.php?t=332674"). I don't notice any performance penalties. In fact, some of the programs I run perform significantly better on my Ubuntu machines.

---

### Post by Grey on 2007-01-18
The compiled version should be faster than the java version if they use the same algorithms.  Period.  I would start looking at some benchmarks to see if maybe there's a bottleneck somewhere on your computer.  Looking at whether DMA is enabled or not on your hard drive would be a good start.

---

### Post by Dislimit on 2007-01-18
> **phossal said:**
> I installed the JDK [this way]("http://ubuntuforums.org/showthread.php?t=332674"). I don't notice any performance penalties. In fact, some of the programs I run perform significantly better on my Ubuntu machines.

I installed the JDK5 with:
1. 'make-jpkg' to convert .bin to .deb
2. 'dpkg -i' to install the jdk.deb

Should any performance penalty on JRE there?

---

### Post by Dislimit on 2007-01-18
After cutting some redundant Java code, the current performance is:
OS \t Main \t Whole
Ubuntu5.10: 5.7s 7.5s
Windows XP: 1.5s 3s
Ubuntu(CPP): ? 3.5s

The Java version looks fast because my Scanner 
is simpler than CPP input stream.
The difference between Ubuntu and WinXp is still too large. 
But I haven't checked the DMA.

---

### Post by Tomosaur on 2007-01-18
You're using Sun's Java right? My Java code runs faster on linux than it does on Windows.

---

### Post by Dislimit on 2007-01-19
It seems that the critical slow-down reason is that the time logger, namely, System.currentTimeMillis(), which we use to track the internal running time, returns much slower in Linux than in Windows.

If we wipe out the timing, the whole running time in Linux is about 2.5s.

---

### Post by laxmanb on 2007-01-19
Yeah... Java performance using Netbeans(huge java app) and the Demo Applets provided with the JDK seems better on Linux than Windows to me...

---

### Post by steve.horsley on 2007-01-20
> **Grey said:**
> The compiled version should be faster than the java version if they use the same algorithms.  Period.  I would start looking at some benchmarks to see if maybe there's a bottleneck somewhere on your computer.  Looking at whether DMA is enabled or not on your hard drive would be a good start.

Wrong. Read Sun's white papers on "hot spot". It can optimise the machine code already knowing which are the common branch choices and pathways because it has already profiled the running application. Although startup is slow, long-running applications (a second or more) can be very fast, with well optimised machine code.

---

