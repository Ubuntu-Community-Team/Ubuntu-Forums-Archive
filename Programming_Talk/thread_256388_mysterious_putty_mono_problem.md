---
title: "mysterious putty mono problem"
date: 2006-09-12
forum: Programming Talk
---

### Post by grim918 on 2006-09-12
I am learning how to program in C# using Mono and I have a question about a problem that I get when I log into my computer remotely using Putty from a Windows box. Everytime that I compile a program and then run it I get this weird character in front of the result of my program. Here is an example of what I get. Keep in mind that this problem only happens when I log in with Putty. I don't get this problem when I run programs locally, this also only happens with C# on mono. Does anyone know what could be causing this and is there a way to fix it. The mysterious characters that I get are always the same, they never change. Here are the characters that I get. 

> grim918@ubuntu:~/C#/variables$ mono objecttest.exe
ï»¿True
False


---

### Post by toojays on 2006-09-12
This may or may not help you, but . . . one thing which can improve the characters you see when you use PuTTY, is the setting of the TERM variable. You can set this in the options for PuTTY. IIRC by default it is xterm, but on modern servers like Ubuntu you can set it to putty, which may improve things.

This may not fix your problem, but it's worth a try.

---

