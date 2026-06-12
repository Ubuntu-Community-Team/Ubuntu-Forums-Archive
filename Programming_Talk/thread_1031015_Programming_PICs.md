---
title: "Programming PICs?"
date: 2009-01-04
forum: Programming Talk
---

### Post by Liliitha on 2009-01-04
I am a bit new to programming and heard of the PIC micro-controller.  It is just a small micro-controller that contains around 35-80 instructions.  Now the company released a C compiler for this micro-controller and I had wondered if it would be easier to program it in assembly language?  If you do not have a compiler/assembler for the job, can you modify one to work with the micro-controller?

---

### Post by ZuLuuuuuu on 2009-01-05
> **Liliitha said:**
> I am a bit new to programming and heard of the PIC micro-controller.  It is just a small micro-controller that contains around 35-80 instructions.  Now the company released a C compiler for this micro-controller and I had wondered if it would be easier to program it in assembly language?  If you do not have a compiler/assembler for the job, can you modify one to work with the micro-controller?

It usually depends on the work you want to do. If it is a high level thing like a robot with artificial intelligence and you don't need very detailed speed optimizations then I suggest programming with PIC C. But if the work is not that hard, like a simple line follower robot, a watch, some LED effect etc, then it could be done in PIC Assembly. We did quite a few line follower and sumo robots in our robotics society using PIC Assembly.

If a platform does not have a PIC C compiler then it is not quite easy to make one from existing C compilers because microcontrollers and microprocessors work a little different. Usually, microcontrollers are pretty basic compared to microprocessors. Like you said, PIC16F84 microcontroller, for example, has only 33 instructions.

---

### Post by skullmunky on 2009-01-07
Some people prefer programming the PIC in assembly, because they can completely control the code and optimize it.  But unless you really need that kind of control, I always prefer easier languages like C or something higher over assembly.  

The last I checked, there wasn't a PIC-C compiler for linux, but we run the Windows C compiler in WINE and that's been fine.

If you're new to programming and want to do something with microcontrollers, take a look at the Arduino:

[http://www.arduino.cc]("http://www.arduino.cc")

it's a cross platform, open source, language, pretty easy to use, and based on the AVR microcontroller.

---

