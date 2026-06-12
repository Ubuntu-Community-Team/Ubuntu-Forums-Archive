---
title: "Ubuntu 7.10 stack security"
date: 2007-10-30
forum: Programming Talk
---

### Post by m00n on 2007-10-30
Hello everyone !!!
I have posted it in Security Forum,
no one was able to help me there but i have been suggested to repost it here. Im sorry if its a wrong section but i really have to find solution.

I'm running ubuntu 7.10 and i'm facing some problems with overwriting eip in memory.
I have disabled Virtual Adress space Randomisation
and im compiling my poccodes with -fno-stack-protector flag in gcc.
And the stack is still unexecutable :(
Im overwriting ebp address successfully but eip cant be overwritten
here is a sample :
eax 0x0 0
ecx 0x31313131 825307441
edx 0xb7fd40d0 -1208139568
ebx 0xb7fd2ff4 -1208143884
esp 0x3131312d 0x3131312d
ebp 0x31313131 0x31313131
esi 0xb8000ce0 -1207956256
edi 0x0 0
eip 0x804848e 0x804848e

Something blocks the execution before it reaches eip.
I couldn't find any exec-shield presence on system, correct me if it's there, so which kind of patch or security implementation is preventing eip of being overwritten on Ubuntu 7.10 ???
Currently i have gcc-4.1.3.

I dont want to install old redhat releases without stack protection, is it possible to do a stack overflow research on ubuntu?
Thanks in advance!

---

### Post by dataw0lf on 2007-10-30
Interesting.  I'm able to overwrite the EIP in 7.04, but I don't have a 7.10 machine handy to test it on (I'm at work).  When I get home I'll let you know.

---

### Post by m00n on 2007-10-30
thank you for help dataw0lf

---

### Post by m00n on 2007-10-30
finally ive got it ))
(gdb) r aaaaaaaaaaaaaaaaaaa
Starting program: /media/disk/tmp/stack aaaaaaaaaaaaaaaaaaa

Program received signal SIGSEGV, Segmentation fault.
0x61616161 in ?? ()
f**cking gcc security drives me crazy
for those who will have the same problem
use gcc v3.3 <= it will work

---

