---
title: "Signals, Interrupts and all the rest"
date: 2012-08-23
forum: Programming Talk
---

### Post by erupter on 2012-08-23
Hi guys.
I'm mainly an embedded C programmer, thus I continously make use of hardware interrupts to synchronize different segments of code.
In an embedded device you have some n timer interrupts you can use for all purposes, plus lots of hardware related interrupts (like serial, i2c, adc, and so on).

I've also done my share of windows coding with .NET where interrupts can be created easily as seen fit, those are called events.

Now I'm trying my luck with a moderately complex Unix program.
From what I've understood Unix interrupts are called signals, and are a fixed number predefined in the libraries.
There are two that are free to use (SIGUSR1/2) that I believe are thread (or maybe process?) dependent: that's to say two different applications are allowed both to use SIGUSR1 without interfering. 
At least this is what I've understood, and it may well be wrong.

So how do I get back the same flexibility I have under windows or even under embedded?
Right now I had all [sorts of problems using SIGALRM](http://cboard.cprogramming.com/c-programming/150271-puzzled-sigalrm-signal-handler-doesnt-install.html) to make a timeout, until I gave up (the handler wasn't installing and the application did just quit after the signal was issued) and used timer_create() with SIGUSR1.
But this is just the beginning and I think I'll need more ways to send interrupts to my code.
How can I do it?

---

### Post by spjackson on 2012-08-23
If you are looking for event driven programming, similar to what you might have done in .NET, then in C++ land you have several options. What I am most familiar with is Qt, but there's also the boost signals library among others. and there might be something in C++11 - I don't know. There is new multithreading stuff in C++11, but I don't know if there's anything like you are looking for.

If you are looking for something in C land similar to your embedded interrupts, then I'm not aware of anything other than what you have already discovered. This isn't to say that there isn't anything, but I haven't done that sort of stuff on Linux in C.

Or there's Java, or Mono, or...

---

### Post by erupter on 2012-08-23
> **spjackson said:**
> If you are looking for event driven programming, similar to what you might have done in .NET, then in C++ land you have several options. What I am most familiar with is Qt, but there's also the boost signals library among others. and there might be something in C++11 - I don't know. There is new multithreading stuff in C++11, but I don't know if there's anything like you are looking for.

If you are looking for something in C land similar to your embedded interrupts, then I'm not aware of anything other than what you have already discovered. This isn't to say that there isn't anything, but I haven't done that sort of stuff on Linux in C.

Or there's Java, or Mono, or...

So you're confirming me that the only way to generate custom events in C is to use SIGUSR1 and SIGUSR2?

That is unfortunate as I'm confined for this project to either C or C++ but I'm most confident with the first.
Never studied C++, although I learned a lot regarding OOP with .NET.
I'd rather stick with C but if I can't...

---

### Post by spjackson on 2012-08-23
> **erupter said:**
> So you're confirming me that the only way to generate custom events in C is to use SIGUSR1 and SIGUSR2?

That is unfortunate as I'm confined for this project to either C or C++ but I'm most confident with the first.
Never studied C++, although I learned a lot regarding OOP with .NET.
I'd rather stick with C but if I can't...
Well, I'm not saying definitively that there's nothing that you can use in C other than those 2 signals. You can for example use the POSIX timer_create(...), and GTK does event driven programming in C. What does it use? Dunno. What I am saying is that my own experience is not using C on Linux for this type of stuff. I've only used C intermittently since about 1994.

Perhaps someone else can answer you better from a C perspective, but since you'd had no responses in a couple of hours, I thought I'd offer my contribution. As a matter of interest, do you use C for your .NET programming?

---

### Post by erupter on 2012-08-23
> **spjackson said:**
> As a matter of interest, do you use C for your .NET programming?

Of course not, VB.NET.
C is not even supported under .NET.
Although I think you can get away with a mixed bag of C++ and C# to exploit both worlds, but I never tried.

BTW thanks for your suggestions!

---

