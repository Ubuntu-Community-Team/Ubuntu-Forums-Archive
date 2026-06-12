---
title: "CPU/GPU Usage - How Much is Too Much?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Scavallo on 2008-08-25
Hello,

I have a Sony Vaio VGN-SZ240P Laptop which I have been using with its default OS, Microsoft Windows XP Professional. I have been using Wubi for quite awhile, and recently I downloaded the Live CD ISO which I installed. I partitioned my NTFS hard drive and am now dual booting XP and Hardy Heron. 

That said, after installing Ubuntu I am planning on using it as the primary OS and only keeping XP to manage my iPhone 16gb 3G. It runs fantastically, in my opinion, but I just want to make sure I'm not overloading the Main CPU and the video card of my GPU.

Specs for Computer:

Sony Vaio VGN-SZ280P
Ubuntu 8.04.1 LTS
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3
Memory: 2.0Gib
Swap Memory: 1.0GiB
Processor 0: Genuine Intel T2500@2.00GHz
Processor 1: Genuine Intel T2500@2.00GHz

Graphics Card Specs:
nVidia GeForce Go 7400
Memory: 128MB
GPU Clock:450 MHz
Memory Clock: 700MHz

With THAT said, please, I don't want to hear all the "ha, I would be surprised if that graphics card would play Minesweeper," or whatever, I know it's not a top-of-the-line Graphics Card, but it came with the laptop, which was given to me, so please give me a break.

Alright, as for everything else, I have Compiz Fusion installed and running (which runs as smooth as butter), Desktop Cube runs 100%, Wobbly Windows could be better but I still get the effect, the Fire Close option runs (after tweaking). Everything is great.

Now for my question: What percentage of my CPU should be being used at idle? Right now its right at 20%-load on each processor and only will peak and stay at 100% when I am using my My Book Essential Edition external HD (which is still an unsolved problem). I dont know how to check my GPU use-percentage but NVIDIA X Server Settings shows my core temp at 46 C when Idle and in the low 50's when rotating my cube/using graphic-stuff.



In sumation -
Is 20% CPU use(20% on CPU0@2.00GHz/20% on CPU1@2.00GHz) too high at Idle?

Is my Graphics Card going to crap out on me in a month from compiz fusion?

What is a safe frequency to overclock my GPU if above answer is "yes"?

My computer says it has 2.0GiB of Memory (of which about 700MB is usually used) and 1 GiB of Swap Memory. What is Swap Memory and why is it never used?

Can I overclock my T2500 CPU's? If so, would it be desirable to do so?

If anyone can answer ALL these questions:) I would greatly apperciate it

Thank you,

Scavallo

---

### Post by MJWitter on 2008-08-26
I can´t answer all of your quesions, but as to CPU and GPU usage: 

They are made to be used.  I have my CPU going at almost 100% all the time processing in a distributed computing network and have no problems(wouldn´t recommend on a laptop as it will kill your battery :) ). 

Also a GPU is made ready for playing games for hours on end, so compiz should be fine.

As to temperature, low 50´s if fine.  My desktop GPU(also a Geforce) sits in the high 60´s when playing games).

I may be corrected, but an easy way to think of Swap memory is like backup RAM. So when your Ram is full, Ubuntu will start storing program data on your hard drive in the Swap memory.  As long as you have free Ram available, you should never need to use the Swap memory.

Hope this helped,
Michael

---

### Post by philinux on 2008-08-26
If you're using system monitor this itself can use up resources. Try the command 

top

in a terminal.

Also check if trackerd is running this can consume resources while it's indexing. I have trackerd disabled.

---

