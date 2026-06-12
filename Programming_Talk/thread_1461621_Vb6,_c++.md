---
title: "Vb6, c++"
date: 2010-04-24
forum: Programming Talk
---

### Post by KruSuPhy on 2010-04-24
Hi, I just got a new laptop about a week ago, and so it's ubuntu. while I don't mind this, I do wonder what it means for my programming. I was formerly a VB6 programmer on windows xp, and I was starting to learn the C languages. Now that i have ubuntu, which i know doesn't run programs like xp does, i need to know what this would mean for my programming.. While I don't think I'll be programming vb6 anymore because of linux, I still have hopes for C. can anyone give me advice on how different it will be? or will it be the same?

---

### Post by sunk8 on 2010-04-24
> **KruSuPhy said:**
> Hi, I just got a new laptop about a week ago, and so it's ubuntu. while I don't mind this, I do wonder what it means for my programming. I was formerly a VB6 programmer on windows xp, and I was starting to learn the C languages. Now that i have ubuntu, which i know doesn't run programs like xp does, i need to know what this would mean for my programming.. While I don't think I'll be programming vb6 anymore because of linux, I still have hopes for C. can anyone give me advice on how different it will be? or will it be the same?

install anjuta from the repos if you're still in the learning curve...
gcc is also good...

---

### Post by KruSuPhy on 2010-04-24
okay i'll try anjuta. i can get it from  the ubuntu software center, right?

---

### Post by nvteighen on 2010-04-24
Look at the stickies, they've got lots of good information that might be useful for you.

Anyway, GCC is the "standard" compiler for C, C++ and others in the GNU/Linux world. Anjuta, on the other hand, is an IDE, a program that places relevant programming tools together to ease development... but it uses GCC (or whatever you've installed) as its compiler.

IMO, don't rely that much on IDEs... I mean, use them but know what's part of learning to use the IDE and what's actually part of the language you're using. As you know, widespread programming languages are usually cross-platform and by knowing to separate IDE from language knowledge you'll be able to learn how to work with the same language in other environments.

---

### Post by Ravenshade on 2010-04-24
There are enough variations on Basic (FreeBasic, DarkBasic, QuickBasic) that I'm sure you'll forget about Microsoft soon enough. 

That being said, I thought FreeBasic was simply free version of Visual Basic. Not being a fan of Visual Basic (huge fan of hardcoding) you should be okay as there will likely be a linux based compiler for the language somewhere. 

There's always wine / virtualisation if things get too tricky.

---

### Post by nvteighen on 2010-04-25
> **Ravenshade said:**
> There are enough variations on Basic (FreeBasic, DarkBasic, QuickBasic) that I'm sure you'll forget about Microsoft soon enough. 


Just a note: QuickBasic was Microsoft's.

---

### Post by mmix on 2010-04-25
you could try gambas, yes, it is basic.
[http://en.wikipedia.org/wiki/Gambas](http://en.wikipedia.org/wiki/Gambas)

there is mini language written in java.
[http://en.wikipedia.org/wiki/Processing_%28programming_language%29](http://en.wikipedia.org/wiki/Processing_%28programming_language%29)

QT SDK
[http://qt.nokia.com/downloads/downloads#lgpl](http://qt.nokia.com/downloads/downloads#lgpl)

Ultimate++
[http://en.wikipedia.org/wiki/Ultimate%2B%2B](http://en.wikipedia.org/wiki/Ultimate%2B%2B)

---

### Post by TheStatsMan on 2010-04-26
> **KruSuPhy said:**
> Hi, I just got a new laptop about a week ago, and so it's ubuntu. while I don't mind this, I do wonder what it means for my programming.


It is worth knowing that there are many free IDE's and text editors that cater for many different languages that are all freely available to you. Really as many as you could possibly interested in. Just to name a few you have freely available to you, Python, C, C++ Fortran, scheme, CL, Ocaml, Ruby, Perl, Haskell, Objective C, Java, Go plus many more. 

Most of these languages are just a single command away or are already installed. For instance if you type ocaml into the terminal, you are given the command to type in and install the ocaml interpreter. Obviously you will want an editing environment but that is up to you to find one that suits you.

> 
 I was formerly a VB6 programmer on windows xp, and I was starting to learn the C languages. Now that i have ubuntu, which i know doesn't run programs like xp does, i need to know what this would mean for my programming.. While I don't think I'll be programming vb6 anymore because of linux, I still have hopes for C. can anyone give me advice on how different it will be? or will it be the same?

As for C, try a few of the IDE's and see if there is one that suits your taste. There are fully integrated one like in Windows. Most people in Linux usually end up using a really good editor like vim or emacs and use a Makefile for C. This tends to be more efficient than and IDE, but it probably isn't something you want to bother with when you are first getting used to linux. Essentially (vim and emacs) offer a lot of shortcuts that enable you to operate in a more efficiently, but they don't operate in a standard manner (when you are used to a Windows system) so I am not sure you should bother with such things when you first move over. I think really you should just make a mental note as something to look at in the future. They also require a few language specific plugins to get the most out of them, so that would possibly be an annoyance at first as well.

---

### Post by phrostbyte on 2010-04-26
I usually recommend Python to VB programmers. [I usually recommend Python to a lot of people :)]

It's kind of in the "spirit" of BASIC in that it is a programming language that is fairly easy to use, but unlike basic that it contains modern features expected in a programming language (objects, rich API, etc.).

If you want to make GUI apps there is this program called "Glade" that has a visual designer. That always was something people expect coming from VB6.

---

