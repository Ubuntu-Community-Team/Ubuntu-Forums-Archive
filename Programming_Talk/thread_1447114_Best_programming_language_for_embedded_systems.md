---
title: "Best programming language for embedded systems"
date: 2010-04-04
forum: Programming Talk
---

### Post by real_magiz on 2010-04-04
Dear all

I would start to learn the best programming language for embedded systems to control devices. What I have heard about that is Assembly Language.

I want to know if there is any better languages to code for embedded systems using Ubuntu machines and please also mention Integrated Development Environment or Editor for that language in Ubuntu.

many thanks
Real

---

### Post by MindSz on 2010-04-05
I think it depends on the embedded system. Currently I work with ARM processors and i program in C, but I've used some other processors hat work with different languages (like Basic).

---

### Post by johnl on 2010-04-05
I have worked with a few different embedded systems with different architectures (avr, msp430, xscale).  The huge majority of code for each of these was written in C, although there were a few small parts that had to be done in assembly.  

My advice is that for programming an embedded system, you should understand the architecture, how things work, and that will probably include being familiar with the assembly instruction set on that platform.  But I wouldn't advise writing every line of code in your program in assembly; just what you need.

---

### Post by GregBrannon on 2010-04-06
I work with real-time embedded systems.  Programming at the machine level is typically done with a real-time OS (RTOS), and VxWorks is the RTOS favored by many.  When an API exists between the machine code and the user, it is typically written C++.  If a graphics layer is required, OpenGL is favored.  Most of the programming work is done in a Windows environment using commercial tools.  There must be Linux equivalents, but I haven't looked.

---

### Post by ubun2warrior on 2010-04-06
I think the best programming language to learn would be JAVA (for embedded systems). Java is a platform independent language. So no matter what architecture the machine has you can program in JAVA. This is the biggest advantage of Java. In ubuntu you have to download jdk from synaptics.

---

### Post by Barrucadu on 2010-04-06
> **ubun2warrior said:**
> I think the best programming language to learn would be JAVA (for embedded systems). Java is a platform independent language. So no matter what architecture the machine has you can program in JAVA. This is the biggest advantage of Java. In ubuntu you have to download jdk from synaptics.

Yes, but that's assuming the embedded system has a Java Runtime Environment on it, which is a pretty huge assumption.

---

### Post by sprince09 on 2010-04-07
I've done a bunch of stuff with AVR's which use C with a bit of assembly. ARM's, from what I've read, are similar (and can run Ubuntu!). I've never used PIC's, but I believe those are also C with assembly like AVR's.

I'd say C is a good starting place at the very least, but assembly certainly wouldn't hurt. Again, it depends on the device you're working with.

---

### Post by GeoMX on 2010-04-07
What kind of embedded devices are you willing to work with?

Assembly is a good start, but when programs become more complex most devices support C, so I'd recommend going with C for most of your projects and practicing assembly with your device of choice.

---

### Post by soltanis on 2010-04-07
Yeah, it really depends on how embedded your device is. If it consists of a single microcontroller with 32K RAM then chances are there is no operating system, you write all the code to deal with things more or less yourself. If it's a little bigger, like say a mobile phone system, or an embedded Linux system, then you have a little more leeway to work with, and a wider choice of language.

You are typically restricted to the languages you have the tools to work with, and from what I see, that's either assembly instructions specific to the controller, a specialized subset of C that you cross-compile, or some incantation of BASIC.

---

### Post by ashoksharmaz87 on 2011-02-19
C language is favourite language of programmers for embedded systems but if you want to go in depth i will suggest to choose assembly language

---

### Post by forrestcupp on 2011-02-19
I know this is an old thread, but it's kind of like asking "What language should I speak if I'm going to some nation in the world?" We need to know what nation before we can give you the best answer.

---

