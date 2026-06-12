---
title: "lsof -i"
date: 2009-11-23
forum: Programming Talk
---

### Post by K-Z on 2009-11-23
Hi, for my project in Linux scheduler, I need to verify whether an incoming process is using network files or not. For that, I need to use the output of lsof -i command. Can you please guide me how to use its output. I have searched a lot for its related data structure or place where its output would be stored but I found nothing. Plzz Help.

---

### Post by A_Fiachra on 2009-11-23
> **K-Z said:**
> Hi, for my project in Linux scheduler, I need to verify whether an incoming process is using network files or not. For that, I need to use the output of lsof -i command. Can you please guide me how to use its output. I have searched a lot for its related data structure or place where its output would be stored but I found nothing. Plzz Help.

If you know a process id, lsof -i | grep PID should tell you what you need to know.

In particular, if  you open a PIPE in perl and read the tab delimited output of lsof, you can keep a list of lists (of a hash of lists with NAME or DEVICE as the key) and work off that.

Look into opening a PIPE in Perl.

You can also do this with bash.

---

### Post by CptPicard on 2009-11-23
Running lsof as an external process and parsing its output is probably not much good in a kernel scheduler. :)

I am currently staring at lsof's source just because I got curious, and it's pretty intense. **proc.c** is my best guess off where some relevant information might be found: [http://pastebin.com/m1acb267c](http://pastebin.com/m1acb267c)

But, in general, I just have this hunch that someone writing a kernel scheduler should have a nice thick kernel internals book handy that explains how to go through network file descriptors of different processes :)

---

