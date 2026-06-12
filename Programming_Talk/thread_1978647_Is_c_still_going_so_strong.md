---
title: "Is c still going so strong ?"
date: 2012-05-12
forum: Programming Talk
---

### Post by hoboy on 2012-05-12
when I look at this it seemed like c still going strong 
but many job add ask for java or c# or objective c, I am right ?

[http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

---

### Post by zombifier25 on 2012-05-12
If elite hackers like Linus Torvalds or Richard M. Stallman still believe that C is the best programming language ever, then it's still going strong.

---

### Post by PaulM1985 on 2012-05-12
There is still lots of software out there built using C.  These things will always need some maintenance, but people are trying to use newer technologies with them.  For example using C# to call C++ or C code.

I think the banking sector still have software written in C, Fortran, etc.

Paul

---

### Post by lisati on 2012-05-12
+1 for learning C if you so choose. 
> **PaulM1985 said:**
> 
I think the banking sector still have software written in C, Fortran, etc.

As an aside, when I worked for a company that processed a lot of financial information back in the 1980s, including processing on behalf of some of the local banks, their codebase was mainly COBOL for the financial stuff.

---

### Post by zombifier25 on 2012-05-12
I learn C++, but it's not very different from C anyway.

---

### Post by Some Penguin on 2012-05-12
> **hoboy said:**
> when I look at this it seemed like c still going strong 
but many job add ask for java or c# or objective c, I am right ?

[http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

In some sectors there's not much of a choice.  For instance, if you want to build an application that runs natively on iOS, you're *really* pushed into using Mac OSX, Objective C, and Xcode.  If you're building an Android app, you're pushed in the direction of Java.

Java is rather common for server-side work, since there's a huge number of libraries and interesting VM features that make it an excellent choice (e.g. pretty good concurrency control primitives, good support for monitoring and profiling via JMX and JVMTI and the like; very useful for understanding what's going on when you have an industrial-scale system).  It's also less vulnerable (barring JNI abuse) to the whole class of memory mismanagement issues that tends to arise w/ C-like languages when you depend upon the work of numerous non-absolutely-perfect programmers (and your average software engineer is absolutely not perfect...).

---

### Post by trent.josephsen on 2012-05-12
Something that becomes more and more evident to me as I pursue my chosen field is that nobody, *nobody* ever accounts for firmware and embedded software when this question comes up. Even the people who mention it are prone to treat embedded systems as some kind of niche market that you're unlikely to encounter in the wild. Perhaps it's just because I hang around the wrong forums...

Anyway, let me tell you, there is a huge need for C programmers in the embedded world that dwarfs the entire industry of consumer-oriented applications. Everything that has a microcontroller in it, which is more and more things these days, needs to be programmed. Objective-C and C++ are rarely used on the lowest level because they are significantly (and unnecessarily) more complex than C. C isn't going anywhere; it's miles easier to work with than assembly for only a slight complexity increase.

I'm not talking about your smartphone here. I'm talking about industrial controls, avionics, GPS, test instruments, smart grids... there is an incomprehensibly massive world of non-consumer electronics out there, and the language it whispers is unmistakably C. (Smatterings of C++, yes, but largely C.) But your average CS major only thinks about the **software industry** and never about all the other industries that need programming talent, because they're so far removed from the consumer that he probably doesn't know they exist.

As a hardware engineer who always gets stuck doing all the programming because I'm the only competent one, PLEASE PLEASE PLEASE study C and displace some of the electrical engineers, because they don't know what they're doing with software and would be better utilized somewhere else.

---

### Post by 11jmb on 2012-05-12
> **zombifier25 said:**
> I learn C++, but it's not very different from C anyway.

It is extremely different, actually. Especially the "right" ways to program in these two languages.

---

### Post by codemaniac on 2012-05-12
A simple analysis of the most updated version (a Git checkout) of the Linux kernel reveals that the number of lines of all its C source code surpasses 10 million .That gives us just an idea about the huge amount of C code floating around us .

A true system and network hacker must posses the C weapon in her arsenal .

---

### Post by codemaniac on 2012-05-12
> **lisati said:**
> +1 for learning C if you so choose. 

As an aside, when I worked for a company that processed a lot of financial information back in the 1980s, including processing on behalf of some of the local banks, their codebase was mainly COBOL for the financial stuff.

Yes there are ample of Legacy applications which still use ancient languages like COBOL , for example prior to the advent of telecom Billing COTS like oracle BRM , Geneva and all the main Telecom billing engine was developed in COBOL .

---

### Post by forrestcupp on 2012-05-12
C is still going strong, and probably always will be. Other languages are going strong, too. The whole point is that you use whatever language suits the project or part of the project you are working on. You wouldn't use C for simple GUI apps, and you wouldn't use C# or Java for developing drivers or kernels. It's all about what you're trying to accomplish.

Incidentally, there is becoming a lot less call for C and winAPI since Microsoft's push toward .Net, and their upcoming push toward html5 and Javascript. But C will never disappear because there are some things that it will always be best for.

---

### Post by Joeb454 on 2012-05-12
I doubt whether languages like C will ever disappear. If C ever disappears, there'll be something else that has taken its place for low-level software development.

As was mentioned earlier in the thread, embedded systems, drivers, kernels etc. all rely on C. I know, for example, that Intel use a lot of C for development of tools they use, and given that it's all low-level stuff, that shouldn't *really* come as a surprise :)

---

### Post by xb12x on 2012-05-12
> **trent.josephsen said:**
> Something that becomes more and more evident to me as I pursue my chosen field is that nobody, *nobody* ever accounts for firmware and embedded software when this question comes up...

Anyway, let me tell you, there is a huge need for C programmers in the embedded world that dwarfs the entire industry of consumer-oriented applications. Everything that has a microcontroller in it, which is more and more things these days, needs to be programmed. Objective-C and C++ are rarely used on the lowest level because they are significantly (and unnecessarily) more complex than C. C isn't going anywhere; it's miles easier to work with than assembly for only a slight complexity increase.

... I'm talking about industrial controls, avionics, GPS, test instruments, smart grids... there is an incomprehensibly massive world of non-consumer electronics out there, and the language it whispers is unmistakably C. ...

@Trent,

I agree with this 100%. There's LOTS of work out there for people fluent in C at the hardware level. Firmware, prototype bring-up, hardware debugging, drivers, you name it. 

Now with the advent of UEFI even the replacement for the PC BIOS is written in C (no longer assembly). 

During the software industry slowdowns that have occurred during my career I've seen friends out of work, for months sometimes. But I've always been able to keep working. 

And I suspect I've made much more money over my career than I would have made writing apps, web-pages, etc. Plus had much more fun doing it.

---

### Post by vanangamudi on 2012-05-30
As mentioned before by other. Disappearance of C is never gonna take place. Still, there are need for operating systems, firmwares, drivers which requires speed and concurrency. both. 

Moreover Java and other runtime engines become popular but are first written in C. Eventually 99% of all the application in earth are written in C directly or indirectly. Real-time systems are still written in C. C is still going to be strong. Not only GNU project assures this, there are plenty of open source projects and shared libraries are being written in C.

Creating a library in C and writing wrappers, binding for other languages is so long trend in insdustries.  Java, C# are confined to software engineering application, and dbms apps. Whereas C can b used to perform any kind of apps.

---

