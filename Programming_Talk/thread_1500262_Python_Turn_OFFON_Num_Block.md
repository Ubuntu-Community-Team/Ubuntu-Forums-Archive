---
title: "Python: Turn OFF/ON Num Block?"
date: 2010-06-02
forum: Programming Talk
---

### Post by juancarlospaco on 2010-06-02
How can i turn OFF/ON the **Numerical Block** of the Keyboard using Python???
(NOT the Leds lights)

*Im not using GTK/QT/Wx*

---

### Post by nvteighen on 2010-06-03
I doubt that's possible. Coincidentally, I was reading about x86 interrupts (Assembly) and there was one to do that... so, such thing is for sure "visible" from Assembly and not from a very high-level programming language like Python...

An idea would be to interface your script with a C program that in turns interface with Assembly code... :P

---

### Post by juancarlospaco on 2010-06-03
*Too bad, we need something like that on Python 3.x*
:(

---

### Post by nvteighen on 2010-06-03
> **juancarlospaco said:**
> *Too bad, we need something like that on Python 3.x*
:(

It's worse... actually no Linux program can do that because Linux restricts access to BIOS interrupt calls (which is a good idea). Either you start programming in DOS Assembly (and no, WinNT DOS emulation doesn't count in) or you should write a new OS to do this...

---

### Post by juancarlospaco on 2010-06-03
You can do that on Assembly/Linux.
You can control Num Block Leds with python.
But not the Num Block Itself.

---

### Post by ja660k on 2010-06-03
> **juancarlospaco said:**
> You can do that on Assembly/Linux.
You can control Num Block Leds with python.
But not the Num Block Itself.

i like it, make people THINK we've done somehting....

---

