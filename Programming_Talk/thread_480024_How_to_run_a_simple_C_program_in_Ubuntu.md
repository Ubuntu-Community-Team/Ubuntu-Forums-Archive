---
title: "How to run a simple C program in Ubuntu"
date: 2007-06-20
forum: Programming Talk
---

### Post by aehjaj on 2007-06-20
I am a new user to ubuntu but i have experience working on other linux platform. I installed Ubuntu Fiesty a couple of days ago. I tried to run a simple "helloworld" like C program using gcc but i was shocked to find out that fiesty could not compile a simple C program. here's what i ran at the terminal

$gcc first.c

error:couldnot locate stdio.h


Please help me on how to solve this problem.

---

### Post by xtacocorex on 2007-06-20
```
sudo apt-get install build-essential
```

---

### Post by aehjaj on 2007-06-20
i dont have an internet connection will this command "sudo apt-get install build-essential" work

---

### Post by xtacocorex on 2007-06-20
build-essential is on the CD, so put it in, open synaptic and search for it, just make sure synaptic is set to read off the CD repository.

---

### Post by aehjaj on 2007-06-20
OK Thanks.

---

### Post by EagleRock on 2007-06-20
Don't have an Internet connection?  How are you posting?  :p

It probably will not, as I doubt that utility is on the LiveCD.  It can't hurt to try, as you can put in the CD and try to apt-get using it...

---

### Post by xtacocorex on 2007-06-21
> **EagleRock said:**
> Don't have an Internet connection?  How are you posting?  :p

It probably will not, as I doubt that utility is on the LiveCD.  It can't hurt to try, as you can put in the CD and try to apt-get using it...
It is on the CD, this has been discussed in length about a year ago in the Community Cafe subforum because people wanted it installed by default, me being one of them.

---

### Post by aehjaj on 2007-06-21
I am posting from somewhere else actually from my office desktop !!!. I will try installing build-essential from the live-cd

---

### Post by aehjaj on 2007-06-21
I too agree that this package build-essential should be installed by default in Ubuntu. If we try C programs in other linux distributions it works.

---

### Post by producer on 2007-06-29
I just ran into the same problem.  Yes, I'll get the build-essential module, but I want ot voice my support for having it in the distribution.  If you have a gcc, why leave out the stdio.h?  gcc won't do much without it.

---

### Post by producer on 2007-06-29
OK, worse t han I thought.  I've installed build-essential and still there is no stdio.h anywhere on my computer.  How are we supposed to get this thing?

---

### Post by Lux Perpetua on 2007-06-29
Show us your program.

---

### Post by producer on 2007-06-29
My program is confidential, but even when I do a search, I find no stdio.h anywhere on the disk.  That's the problem.  Where should it be, and how do I get it?

---

### Post by vexorian on 2007-06-29
If build-essential doesn't work then there's something odd about your code.

Imho you just need to post the #includes section.

And how are you calling gcc?

---

### Post by producer on 2007-06-29
Well, that's simple, it's a small program and the #include section is one line.
#include <stdio.h>
I don't think that's giving away too much.  However I fail to understand how it makes a difference when I can go into Places > Search for files...  and seach for "stdio.h" and even that doesn't turn up the file.
I run 
gcc -o<filename> <filename.c>
without the angle brackets of course, and I've substituted "filename" for the real filename, for security reasons.

---

### Post by aquiles_caigo on 2007-06-29
hmm.. correct me if im wrogn but... i think that gcc should be called this way:
gcc <filename.c> -o <filename>

---

### Post by producer on 2007-06-29
The man page says,
[I]cc [-c|-S|-E] [-std=standard]
           [-g] [-pg] [-Olevel]
           [-Wwarn...] [-pedantic]
           [-Idir...] [-Ldir...]
           [-Dmacro[=defn]...] [-Umacro]
           [-foption...] [-mmachine-option...]
           [-o outfile] infile...[/I]
although I think it would work in either sequence.  I'm too tired tonight to try it.  I'll get back here in the morning, unless I get a brain cramp and forget.;)

---

### Post by producer on 2007-06-30
Mine is working now.  I'm not sure why.  Maybe it was the build-essential?

---

### Post by xtacocorex on 2007-07-01
> **aquiles_caigo said:**
> hmm.. correct me if im wrogn but... i think that gcc should be called this way:
gcc <filename.c> -o <filename>
It doesn't matter the order in which command line arguments are called.

---

