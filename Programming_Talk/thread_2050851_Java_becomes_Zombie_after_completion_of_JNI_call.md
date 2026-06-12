---
title: "Java becomes Zombie after completion of JNI call"
date: 2012-08-31
forum: Programming Talk
---

### Post by upkeep1 on 2012-08-31
Hello,

  I call .so library (built by FreePascal) from Java via JNI. The call proceeds normally, the library performs all its job and even returns apparently normally (because System.out.println, which is placed in Java program immediately after the call, prints what is expected). But then there is no proper return from the Java program - no prompt on the terminal, and when I look in Monitor, I see that "java" process is Zombie.

This happens for both default Java VM and "jamvm" Java VM, if my Java program ends with "return". But if my Java program ends with Sustem.Exit(0) then "jamvm" finished normally (and a prompt appears on on the terminal), while the default Java VM still becomes Zombie.

Without JNI call this Java program completes normally (no Zombie, and a prompt appears on the terminal).

What may cause this improper completion of Java program (or Java VM) after JNI call, and what can I do about that?

I'm using Ubuntu 11.04, on VM under VMVare Player.

On Windows the same pair of Java program and the DLL (again, built by FreePascal) works properly, without any strange effects.


Alexander

After investigation it appeared that the problem shows itself even without an actual call of the function in the library - just execution of LoadLibrary in Java for that library is enough..

Luckily, it appeared that after upgrade of Lazarus/FreePascal to the latest version 1.0/2.6 (from 0.9.30.2/2.4) and rebuilding the library with it the problem disappeared completely - now both LoadLibrary and JNI call proceed as they should and the process finishes properly (with normal prompt on the terminal and no Zombie in Monitor).

---

