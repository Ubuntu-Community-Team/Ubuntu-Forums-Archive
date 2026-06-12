---
title: "Does the terminal have anything to do with programming?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-10-29
I only use the terminal when I ask a question on this forum and someone gives me some code so I can get help for a question.

So what does the terminal do besides this? Does it involve programming? What does it mean to compile the kernel?

---

### Post by lisati on 2011-10-29
A common misconception is that you enter CODES into the terminal. This is incorrect: the terminal accepts COMMANDS, some of which might be CODES.

---

### Post by cgroza on 2011-10-29
Programmers use some of their tools via the command line. Bash code can be entered at the command line.
But you do not need to be a programmer to learn the command line.

Compiling the kernel means running a program called "compiler' on the kernel source code. Usually this is done to enable some feature that is not present by default.
In the case of Linux, the source files are not fed to the compiler directly. The whole process is managed by scripts and makefiles that handle dependencies and linkage.

---

### Post by Paqman on 2011-10-29
> **brawnypandora0 said:**
> 
So what does the terminal do besides this? 


The terminal is just a way of interfacing with the OS. You can issue commands, run applications and get information. That's about it.

> Does it involve programming? 

No. Code is written in a text editor and/or IDE. Although there are text editors that work in a terminal.

> 
What does it mean to compile the kernel?

Before it can be run, software has to be compiled. Compiling is just taking the source code and turning it into something that can be executed by your hardware. Normally all the packages you get for Ubuntu are pre-compiled, but you can compile them from source too. The advantage of doing this is that you can change some of the options of how the software will work.

---

### Post by antoinethewiz on 2011-10-29
> **brawnypandora0 said:**
> Does it involve programming?

No, but programming involves it. Here's how you can get a basic setup for C programming.
```
sudo apt-get install build-essentials vim subversion autoconf libc6-dbg
svn co svn://svn.valgrind.org/valgrind/trunk valgrind
cd valgrind
./autogen.sh
./configure
make
make install
cd ../
rm -f valgrind

```Now, you can write any C program with vim, compile it with make (I recommend adding -Wall and -g parameters), and debug with valgrind.

---

