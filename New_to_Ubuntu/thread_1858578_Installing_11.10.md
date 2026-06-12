---
title: "Installing 11.10"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by cheatos on 2011-10-12
As 11.10 will be released soon, I was thinking about upgrading to a 64-bit version as this is faster (I have heard)

Are there any specifications my PC has to comply with? And if yes, how can I check if my computer is compatible with 64-bit?

Furthermore will there be problems if I run a 32-bit Win7 on the same computer (dual-booting)

Thanks for your advice

---

### Post by josephmills on 2011-10-12
could you open your terminal and type in 
```
free -m 
``` then ```
cat /proc/cpuinfo 
``` then paste here thanks

---

### Post by acrazyplayer on 2011-10-12
I can safely tell you that you can boot whatever else you want without problems with the whole 64 32 bit thing. 

It all depends on your processor which you never told us what it is.

---

### Post by zampes on 2011-10-12
Being able to install the 64-bit version depends on if you have a 64 bit processor that can handle it. You can have a 32-bit windows install right next to a 64-bit GNU/linux install, it doesn't matter. A 64-bit processor can handle 32 bit but not the other way around.

---

### Post by viperdvman on 2011-10-12
Well, if your computer is running any of the following processors....:

AMD Athlon 64
AMD Athlon 64 x2
AMD Athlon x2
AMD Turion *(any)*
AMD Phenom *(any)*
AMD V-series
AMD C-series
AMD E-series
AMD A-series
Intel Pentium D
some late-model Pentium 4's
Intel Core 2 Duo
Intel Core 2 Quad
Intel Pentium Dual-Core *(not the earliest Core-based laptop model, as it's 32-bit)*
Intel Celeron *(Core 2-based and Core i3-based)*
Intel Core i7
Intel Core i5
Intel Core i3
Intel Atom

*I know I'm probably missing a bunch of processors, including VIA's. But these are the most common. I also omitted the PowerPC processors as well because there aren't a lot of Linux distros that run on PowerPC computers.*

If you run any of these processors, whether your computer is a Mac or a Windows computer, you can run 64-bit Ubuntu, or any 64-bit operating system for that matter. If your computer runs 4GB or more of RAM, then it's recommended you use a 64-bit system to utilize all your RAM (if your processor is a 64-bit one).

Hope that incomplete list helps :)

---

### Post by cheatos on 2011-10-12
Okay, this is my processor model
model name    : Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
Following the list, it should be compatible with 64bit, right?

Still, why does the ubuntu homepage then tell me that the 32bit version is recommended, if the 64bit one is faster?
Is it just because it is not ensured what type of processor is used or is it not as stable as 32bit?

---

### Post by Mark Phelps on 2011-10-12
Just so you know, the 64-bit version is NOT inherently faster than the 32-bit version.  It's just that, in many cases, PCs using the 64-bit version have faster processors, and more memory, than PCs using the 32-bit version -- but that makes the PC in general faster, not because of the 64-bit version.

I experimented with 32-bit and 64-bit versions of both Ubuntu and Windows 7 recently when I build a new PC and in both cases, the performance of the 32-bit installs was the same as the 64-bit installs.

---

### Post by ajgreeny on 2011-10-12
> **cheatos said:**
> Okay, this is my processor model
model name    : Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
Following the list, it should be compatible with 64bit, right?

Still, why does the ubuntu homepage then tell me that the 32bit version is recommended, if the 64bit one is faster?
Is it just because it is not ensured what type of processor is used or is it not as stable as 32bit?
It is just because if you don't know what processor you have, a 32 bit OS will run OK in either a 32 or 64 bit cpu, but only if it is a 64 bit cpu will it be able to run a 64 bit OS.  Therefore there are still some (many?) computers, mine included that can run only a 32 bit operating system.

---

### Post by alphacrucis2 on 2011-10-12
> **Mark Phelps said:**
> Just so you know, the 64-bit version is NOT inherently faster than the 32-bit version.  It's just that, in many cases, PCs using the 64-bit version have faster processors, and more memory, than PCs using the 32-bit version -- but that makes the PC in general faster, not because of the 64-bit version.

I experimented with 32-bit and 64-bit versions of both Ubuntu and Windows 7 recently when I build a new PC and in both cases, the performance of the 32-bit installs was the same as the 64-bit installs.


Try doing Video transcoding. You will see a significant difference.

---

### Post by oldos2er on 2011-10-12
> **cheatos said:**
> Still, why does the ubuntu homepage then tell me that the 32bit version is recommended, if the 64bit one is faster?


Some CPU intensive tasks like video encoding are demonstrably faster. Day-to-day tasks like web browsing, email, etc. aren't much different.

Someone already mentioned it, but the webpage recommendation to use 32-bit is geared toward people who may not know the full capabilities of their hardware.

I've got a 1.8GHz Core 2 Duo; been running 64-bit on it for years.

---

### Post by cheatos on 2011-10-13
okay, so I'll be trying the 64bit version on my new installation.

---

### Post by d4m1r on 2011-10-13
> **oldos2er said:**
> Some CPU intensive tasks like video encoding are demonstrably faster. Day-to-day tasks like web browsing, email, etc. aren't much different.

Someone already mentioned it, but the webpage recommendation to use 32-bit is geared toward people who may not know the full capabilities of their hardware.

I've got a 1.8GHz Core 2 Duo; been running 64-bit on it for years.

Actually no. 32 vs 64 bit will NOT affect CPU speed, but RAM! Yes 64 bit is inherently faster than 32 bit but only when it comes to RAM intensive/low latency requiring programs.

On Windows 7, 64 bit is the way to go...The majority of the applications are 64 bit compatible, and of those that are still not, 32 bit versions exist that 9/10 times will run in a 64 bit environment (but not always).

On Ubuntu, it is a little different. I don't know how many of the popular applications are available in 64 bit versions as the majority of users use a 32 bit version. Even though I have a very fast PC, I went with the "recommended" 32 bit client to avoid running into these software issue (like I did when I was an earlier adopter of 64 bit Vista) especially since I am new to the Ubuntu scene.

---

### Post by oldos2er on 2011-10-14
> **d4m1r said:**
> Actually no. 32 vs 64 bit will NOT affect CPU speed, but RAM! Yes 64 bit is inherently faster than 32 bit but only when it comes to RAM intensive/low latency requiring programs.

That's not been my experience.

> On Windows 7,

Linux isn't Windows.

> On Ubuntu, it is a little different. I don't know how many of the popular applications are available in 64 bit versions as the majority of users use a 32 bit version.

How do you know? I can think of one "popular" application that is 32-bit only; Adobe Acrobat. Otherwise you'll find the 64-bit repos are just as full as the 32-bit ones.

>  Even though I have a very fast PC, I went with the "recommended" 32 bit client to avoid running into these software issue (like I did when I was an earlier adopter of 64 bit Vista) especially since I am new to the Ubuntu scene.

That's a shame; you've been bitten by this bug, caused by the web site designers, not the developers: [https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

Extrapolating your Windows experience to Linux won't really work since Linux is fundamentally different from the ground up.

---

### Post by cheatos on 2011-10-14
okay as I only titled this thread installing 11.10, I think i can still ask some other question.
I have installed 11.04 with a CD and I didn't want to rewrite a new CD now, but try the version with the USB-Stick.
What do I have to be careful about and what is different to installing from CD?
And where can I set the right boot order in the bios or in the boot loader?

---

### Post by dFlyer on 2011-10-14
Before you do anything, clone or back up your current OS.

---

### Post by cheatos on 2011-10-14
I have already done that, respectively I have saved all my data in my Windows partition, so this one shouldn't be affected, right?

The problem I have is the boot order, my computer is configured, so that it doesn't boot from a USB-Stick but only CD and HDD.

I will still backup all important data, though, so backing up stuff isn't really my problem, the problem is how to set the boot order right and what I have heard is, that you need to make the USB-Stick bootable, how would I do that?

---

### Post by pp. on 2011-10-15
What are the issues when choosing between 32bit and 64bit Ubuntu?

My pc is an hp d7900 with 5GB of RAM. I would love to use all of my machine.

Besides the apps that come with Ubuntu I also use a few with WINE (crossover, actually) and VMWare player.

What kinds of problems am I likely to run into, given that I haven't the foggiest notions about the OS except as a rank user (since Ubuntu 7.10, I think).

I could not find any similar threads. If you can provide pointers to the answers I'd be immensely grateful.

Thank you in advance.

---

### Post by 3rdalbum on 2011-10-15
> **pp. said:**
> What are the issues when choosing between 32bit and 64bit Ubuntu?

My pc is an hp d7900 with 5GB of RAM. I would love to use all of my machine.

Besides the apps that come with Ubuntu I also use a few with WINE (crossover, actually) and VMWare player.

What kinds of problems am I likely to run into?

I don't think you'll run into any problems. 64-bit Ubuntu is basically 32-bit Ubuntu with bigger numbers. Same source, different binary. With the Multiarch support in 11.10 you don't even need to "force architecture" anymore when installing 32-bit packages; it all Just Works.

---

### Post by cheatos on 2011-10-15
Hi there,

According to what you said about your system config, I'd say take the 64bit version, as your RAM speed will be (almost?) twice as fast or something like that...

---

### Post by mister_playboy on 2011-10-15
It's easy to have a fully 64-bit Linux system without any problems... nothing like Windows in this regard.

You have 5GB of RAM so you will use 64-bit. :popcorn:

---

### Post by Owenoen on 2011-10-15
Absolutely x64 it better. I just got a Lenovo B460 laptop with 2GB ram. It's running the newest Ubuntu 11.10 x64 well.

---

### Post by sadaruwan12 on 2011-10-15
I've tried both 32bit and 64bit in earlier days when x64 came on to the seen you might had to ask this question which is better but now you want see or feel a difference.

I have 2 PC's one a desktop running ubuntu 10.04_x64 with 3Gb of RAM and lot of HDD space the other is my new Lenovo B560 laptop running ubuntu 11.10 with 4Gb of RAM.

Both perform very nicely on the Laptop how ever the system is flying very responsive and I'm able to run 32bit programs as well as 64bit once.

For you I say go with the 64bit one 'cos you've lot of RAM to work with all that Gb's you need the x64 power.

---

### Post by pp. on 2011-10-15
Thanks to all. I've run the 64bit live system on my PC and have not found any problems yet. Some apps are much more responsive, but that could be because I have updated my Ubuntu linux for several years now without doing a new installation from scratch.

Since I have to re-install anyway (because of problems not related to the number of bits), I will take the plunge.

---

### Post by Sunfist on 2011-10-15
> **cheatos said:**
> okay, so I'll be trying the 64bit version on my new installation.

Only problem I had and the only reason I switched back to the 32 bit version is that some software is only available in a 32bit version and won't run on a 64bit OS, that is changing rapidly as more and more people are running 64bit processors, but it may be an issue.

---

### Post by cheatos on 2011-10-16
Where is my personal linux profile being stored?
I would like to migrate all my passwords and stuff to the 11.10 but still want to do the fresh install...
So how can I get to these settings?

---

