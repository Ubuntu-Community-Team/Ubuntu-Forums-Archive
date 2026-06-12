---
title: "32-bit binary generation by gcc on 64-bit Karmic (x86_64)"
date: 2010-04-13
forum: Packaging and Compiling Programs
---

### Post by nov13 on 2010-04-13
Dear all,
 
I installed 64-bit Karmic 9.10, on x86_64 machine.
Now I want to generate a binary for x86 (32bit) cpu by using gcc or cross-compiler
 
Q1) Is it possible to generate (32bit) binary using (64bit) gcc shown in 64-bit Karmic 9.10? If it is possible which option for gcc is required to generate 32bit binary?
Q2) if the answer for Q1 is impossible, where can I get the cross-compiler (tool-chain) for x86(32bit) on x86_64 ubuntu ?
 
Sincerely yours.
- jeongjoon yoo.

---

### Post by benj.david on 2010-04-14
Hello,
The first link on google when searching "gcc 32bits" is [http://www.cyberciti.biz/tips/compile-32bit-application-using-gcc-64-bit-linux.html](http://www.cyberciti.biz/tips/compile-32bit-application-using-gcc-64-bit-linux.html)
You'll find the answer.

ben

---

### Post by SevenMachines on 2010-04-14
Just a quick note on ubuntu-specific advice. 

*You'll want to install multilib gcc support, this also pulls in the 32bit libc6 dev libraries as a dependency
$sudo apt-get install gcc-multilib

* You can also install any other 32 bit libs you need, search in synaptic for lib32 and you'll see a few. If a 32 bit lib isnt available in the repository you'll need to compile/install it manually

* Then, as the previous link mentions, add -m32 to your gcc command to build a 32bit binary
$gcc -m32 -o myapp32 myapp.c

$file myapp32
test32: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped

yay!

---

