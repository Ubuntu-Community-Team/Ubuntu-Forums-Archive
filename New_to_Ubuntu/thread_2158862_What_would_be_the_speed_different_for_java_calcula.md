---
title: "What would be the speed different for java calculation program in windows vs linux?"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by dixcuxx on 2013-06-30
I know there may be no perfect objective answer for this, but did someone create benchmark like this? Or around how much different should I expect? The computer hardware is pretty good in these years, then there is not much different now? I main concern is a program that mainly purely a lot of calculation in a lot of data in array with no graphic except a very basic swing gui as control panel. If we have the same hardware and same java code for the calculation program, what difference should that be?

---

### Post by KARNVORbeefRAGE on 2013-06-30
Try this if you have a dual boot:
[http://forums.fedoraforum.org/showthread.php?t=105244](http://forums.fedoraforum.org/showthread.php?t=105244)

---

### Post by KARNVORbeefRAGE on 2013-06-30
Also, keep in mind that there are different compilers.  Linux, if a manual install of Java, may include the 64-bit version vs. Windows which is typically default with a 32-bit version.

---

### Post by dixcuxx on 2013-06-30
I look at the benchmark measure code and I guess running a for loop like that may not have a very objective result, especially it keep print out stuff which may let the graphic power of java in windows/linux affects the speed a lot.

---

### Post by dixcuxx on 2013-06-30
it is a very micro coding, not represent speed in general.

---

### Post by HermanAB on 2013-07-01
Hmm, well, depends on whether you include the time required to scan and remove viruses and other malware and reboot three times, before you can start the test...

---

### Post by dixcuxx on 2013-07-01
> **HermanAB said:**
> Hmm, well, depends on whether you include the time required to scan and remove viruses and other malware and reboot three times, before you can start the test...

linux has this advantage since normally we don't even have anti virus.

---

### Post by 3rdalbum on 2013-07-01
Speed of execution is probably very similar, when comparing 32-bit operating systems. Linux does keep more RAM available for programs, though.

---

### Post by ofnuts on 2013-07-01
> **dixcuxx said:**
> I know there may be no perfect objective answer for this, but did someone create benchmark like this? Or around how much different should I expect? The computer hardware is pretty good in these years, then there is not much different now? I main concern is a program that mainly purely a lot of calculation in a lot of data in array with no graphic except a very basic swing gui as control panel. If we have the same hardware and same java code for the calculation program, what difference should that be?
As long it's pure computation (no system calls) and you are using the same JVM (ie, Oracle/Sun, IBM, OpenJDK) of identical bitness... zilch. You would get more difference using different JVMs on the same hardware and operating system (and likely find that each is a bit better that the others for at least one kind of computation). That would even apply to running your Java in a Windows virtual box on Linux and vice-versa.

Linux starts looking better when you are doing a lot of I/O.

---

### Post by dixcuxx on 2013-07-01
> **ofnuts said:**
> As long it's pure computation (no system calls) and you are using the same JVM (ie, Oracle/Sun, IBM, OpenJDK) of identical bitness... zilch. You would get more difference using different JVMs on the same hardware and operating system (and likely find that each is a bit better that the others for at least one kind of computation). That would even apply to running your Java in a Windows virtual box on Linux and vice-versa.

Linux starts looking better when you are doing a lot of I/O.

I find out this link:
[http://dior.ics.muni.cz/~makub/java/speed.html](http://dior.ics.muni.cz/~makub/java/speed.html)
the conclusion should be with the same official JVM version, the performance in Linux and Windows are extremely similar

---

