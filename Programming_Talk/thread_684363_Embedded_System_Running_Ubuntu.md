---
title: "Embedded System Running Ubuntu"
date: 2008-02-01
forum: Programming Talk
---

### Post by amartch on 2008-02-01
I'm doing a small embedded project thats in all essence a full fledged car computer.

So basically I need help on:
-Setting up a development rig and getting started
-Driver development
-Kernel hacking and hardening
-Minimizing memory footprint of OS
-Integrating voice recognition into OS
-Remote debugging

Please keep in mind that I'm not a newbie, I simply have never done any development on Linux.

---

### Post by Vadi on 2008-02-01
Check out Ubuntu Mobile (google gives excellent results on "Ubuntu Mobile"), I think that's a project designed for this type of thing.

---

### Post by amartch on 2008-02-01
> **Vadi said:**
> Check out Ubuntu Mobile (google gives excellent results on "Ubuntu Mobile"), I think that's a project designed for this type of thing.
One of the first pages that I checked was
[https://wiki.ubuntu.com/MobileAndEmbedded](https://wiki.ubuntu.com/MobileAndEmbedded)

It offered me some information, but not quite what I need.

---

### Post by chewearn on 2008-02-01
For a start, what hardware platform are you choosing?  PC-based intel, or some embedded CPU like ARM?

---

### Post by pmasiar on 2008-02-01
> **amartch said:**
> I'm doing a small embedded project thats in all essence a full fledged car computer.
...
Please keep in mind that I'm not a newbie, I simply have never done any development on Linux.

Sounds like rather interesting project. Is it a hobby or professional? I mean do you have deadlines?

If it is a hobby, it looks like really a long-time project. I would advise to join a community which works on part of the problem, like device development. You can learn "tricks of trade" from experienced kernel hackers, and skills which you can transfer to your project later. If you dive directly to your project, you may be forced to reinvent the wheel (and it might turn up a square :-) ).

---

### Post by amartch on 2008-02-01
> **AstalaVista said:**
> For a start, what hardware platform are you choosing?  PC-based intel, or some embedded CPU like ARM?

Currently looking at several things, PC104, TI DSP C55x, ARM9, ARM11.
So far, it looks like PC104 will be easiest, so assume the architecture will be x86.

> **pmasiar said:**
> Sounds like rather interesting project. Is it a hobby or professional? I mean do you have deadlines?

If it is a hobby, it looks like really a long-time project. I would advise to join a community which works on part of the problem, like device development. You can learn "tricks of trade" from experienced kernel hackers, and skills which you can transfer to your project later. If you dive directly to your project, you may be forced to reinvent the wheel (and it might turn up a square :-) ).

It's part hobby, part thesis and target completion date is in 18 months.
I'm not interested in reinventing the wheel, which why I'm posting here.

---

### Post by l.capriotti on 2008-02-01
> **amartch said:**
> 
So far, it looks like PC104 will be easiest, so assume the architecture will be x86.

I would choose Ubuntu Mobile and Embedded (UME), and start from the following: 

[Creating  A Generici 386 Plaform For MIC]("https://wiki.ubuntu.com/CreatingAGenerici386PlaformForMIC")

i.e. using UME tools with a generic i386 architecture.

Cheers

Luigi

---

### Post by amartch on 2008-02-01
Currently I'm setting up 7.10 on my desktop which I plan to use for all the coding,
I've also managed to get my hands on a touch computer thats about as powerful as the system I plan on making.

Now the big question:
What do I use instead of Visual Studio and how can I remotely run and debug what I make (Visual Studio's remote debugging capabilities)?

---

