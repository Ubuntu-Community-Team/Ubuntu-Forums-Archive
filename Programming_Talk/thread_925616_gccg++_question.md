---
title: "gcc/g++ question"
date: 2008-09-20
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-09-20
so basically im making a joke language that is just parsing some code and then compiling it in gcc/g++...just one question is there a way to send a send a string of code from the source code file for my language to the compiler without having a file for my language and a converted c/c++ file?

thanks in advance

---

### Post by Zugzwang on 2008-09-21
I doubt that g++ will accept piped code.

However, you can just create a temporary file in the respective directory (/tmp) here. What's wrong with that approach?

---

### Post by jimi_hendrix on 2008-09-21
good idea...so i save it to /tmp and do g++ filename.cpp in temp?

---

### Post by Zugzwang on 2008-09-22
> **jimi_hendrix said:**
> good idea...so i save it to /tmp and do g++ filename.cpp in temp?

Technically, yes.

To make your program safe for multiple executions of it at the same time, having some other user having a file with the same name in that dir, etc., etc., you are hereby advised to create a directory in /tmp/ using the [mkdtemp]("http://linux.die.net/man/3/mkdtemp") function. That's however linux only. In all other cases, look [here]("http://opengroup.org/onlinepubs/007908775/") to find something POSIX-compatible.

---

### Post by jimi_hendrix on 2008-09-22
> **Zugzwang said:**
> Technically, yes.

To make your program safe for multiple executions of it at the same time, having some other user having a file with the same name in that dir, etc., etc., you are hereby advised to create a directory in /tmp/ using the [mkdtemp]("http://linux.die.net/man/3/mkdtemp") function. That's however linux only. In all other cases, look [here]("http://opengroup.org/onlinepubs/007908775/") to find something POSIX-compatible.

unfortunetly, that function wont help me because i made the parser in C# since its the language i can manipulate strings best in.  If it doesnt work out then i will switch to C++...thanks for the help

---

### Post by kjohansen on 2008-09-22
there is a getrandomfilename function in C#

see here:
[http://social.msdn.microsoft.com/forums/en-US/netfxbcl/thread/53def6a4-076c-43f8-86e9-e223d99396a0/](http://social.msdn.microsoft.com/forums/en-US/netfxbcl/thread/53def6a4-076c-43f8-86e9-e223d99396a0/)

---

### Post by jimi_hendrix on 2008-09-22
thanks...will it compile in linux?

thanks all

---

