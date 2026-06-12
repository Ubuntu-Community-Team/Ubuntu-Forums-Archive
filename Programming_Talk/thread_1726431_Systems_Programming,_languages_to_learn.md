---
title: "Systems Programming, languages to learn?"
date: 2011-04-11
forum: Programming Talk
---

### Post by GeissT on 2011-04-11
Hey everyone,

Now you have just read the title and are about to comment with "Use C or ASM you n00b" And thats fine, just shows how mature you are.

So I really want to start some systems programming but obviously its not that easy to start with so I want to find a suitable language to learn for this task. Yes C and ASM are the mains, but are their others? I know that Linux Modules are written in C, correct? So I have started that, but I want to expand to other aspects of SysCoding.

Thanks in advance.

GeissT

---

### Post by Some Penguin on 2011-04-11
The Linux kernel, including modules, are written in ordinary C.  If you're talking about operating systems, device drivers and the like -- C will be your best bet.  Direct access to memory addresses is rather useful for efficiently sharing the same data between threads and processes (e.g. for communicating with various bits of hardware).   C also tends to have fewer binary incompatibility issues than, say, C++.

That's not to say that other languages haven't been used... but just not as widely, at least for standard desktop hardware.  For other ecologies like mobile where you aren't likely to be expected to provide compatibility with a large and diverse ecology of ancient devices... e.g there's Objective C in iOS land, and the related-to-Java Android universe.

---

### Post by GeissT on 2011-04-11
Thanks for your informative post.

C seems to be my best bet hey? Ive seen others describe Pascal as another candidate, could this be a possibility?

Thanks in advance,

GeissT

---

### Post by MadCow108 on 2011-04-11
have a look at go:
> Go is an expressive, concurrent, garbage-collected systems programming language.
[http://code.google.com/p/go/](http://code.google.com/p/go/)

it is also included in gcc 4.6
[http://gcc.gnu.org/gcc-4.6/changes.html#go](http://gcc.gnu.org/gcc-4.6/changes.html#go)

---

### Post by nvteighen on 2011-04-11
If you are really really brave, you might look at Forth :P It's quite low-level, quite powerful, but a rough beast to tame. It's sometimes used in embedded systems because of its low memory requirements.

---

### Post by Pithikos on 2011-04-11
There is always the minimal [Brainfuck]("http://en.wikipedia.org/wiki/Brainfuck") you could try :tongue:

---

### Post by deathadder on 2011-04-11
I would suggest C as well, although I've used Ada before in real-time systems and embedded programming. Which takes influence from Pascal and a couple of other languages (smalltalk).

---

### Post by GeissT on 2011-04-12
Thanks to all that responded, I have seen Brainfuck before this encounter XD [sarcasm]Looks like i would enjoy it [/sarcasm].

Go, this is another language that I have 'messed' with before and I just did not like it, I cant seem to pinpoint why, but judging by the rest of the posts I will learn C :)

Thanks for all your input.

GeissT

---

### Post by ve4cib on 2011-04-12
"Systems programming" is typically pretty low-level stuff, so as you said in your first post, C and the assembly language for your CPU of choice are your best bets.

Depending on the type of system you're working with you may or may not even need any assembler.  Writing Linux modules for a desktop will probably be entirely in C.  On the other hand, if you want to create your own OS for an 8-bit microcontroller then you will probably need some inline assembly here and there.

Also, [Haiku](http://haiku-os.org), unlike Linux, is written in C++, not C.  So again, the type of system you want to write for will impact your choice of language a great deal.

---

