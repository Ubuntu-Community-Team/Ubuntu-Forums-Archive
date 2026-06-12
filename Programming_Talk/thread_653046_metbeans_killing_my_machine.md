---
title: "metbeans killing my machine"
date: 2007-12-29
forum: Programming Talk
---

### Post by t_ras on 2007-12-29
Hi
I'm using Kubuntu 7.10 on AMD64 with 512MB and Gforce (128mb)
I installed Netbeans 6.0 and of course all java6 related packages.
The problem is that NetBeans works extremely slow and hangs my system.

It seems to be using the right Java and I tried also through sudo, no an do...

Any Idea how to solve it?

---

### Post by t_ras on 2007-12-29
Hi
I'm using Kubuntu 7.10 on AMD64 with 512MB and Gforce (128mb)
I installed Netbeans 6.0 and of course all java6 related packages.
The problem is that NetBeans works extremely slow and hangs my system.

It seems to be using the right Java and I tried also through sudo, no an do...

Any Idea how to solve it?

---

### Post by t_ras on 2007-12-29
Hi
I'm using Kubuntu 7.10 on AMD64 with 512MB and Gforce (128mb)
I installed Netbeans 6.0 and of course all java6 related packages.
The problem is that NetBeans works extremely slow and hangs my system.

It seems to be using the right Java and I tried also through sudo, no an do...

Any Idea how to solve it?

---

### Post by stuffelse on 2007-12-30
I just put netbeans on my machine, and it runs great, but i've got 1.25GB ram. 

My *professional opinion* is that you need more RAM if possible. Not that I have any real basis for this theory, but I think Gutsy is WAY heavier than former distros.

---

### Post by samjh on 2007-12-30
At what point does it hang your system?  From startup, or when you're trying to do something specific?

Check the following:

1. Are you running Compiz-Fusion, Compiz, or Beryl?  If so, turn them off.

2. How did you install Netbeans?  Did you use the OS independent zip, or the official installer script from Netbeans?  If you tried one method, have you tried another?

3. Try running Netbeans from the command-line.  Are there any errors or other messages displayed?

---

### Post by t_ras on 2008-04-18
OK,
I added another GB of RAM to my machine (so now it is 1.5 GB).
I tried fomr commend line, booth as normal user and root. 
It still uses 400MB of memory.
In my vista laptop (1.7GHz dual core 1GBRAM) it takes 150MB and runs much faster.

---

### Post by themusicwave on 2008-04-18
Just installing the Sun Java packages is not enough.  You have to tell Ubuntu to use them instead of the GNU version.

Run
sudo update-alternatives --config java

Make sure Sun Java is selected.

If that doesn't work my other questions are:

1) How fast is that AMD64?

2) What else is running when Netbeans is running?

3) Are you stopping all the Java processes you start properly or leaving them running?  Check system monirot and see if you have a bunch of java entries.

---

### Post by t_ras on 2008-04-18
I tried sun-6 and sun-1.5 (which works halite faster), but it is still slow and takes still 450MB.
My CPU is Athalon 64bit 3000+
No other Java processes are running before I open or keep running before I close Netbeans.
I have Thunderbird and mail/web/SQL servers. all together use less then 1GB memory.
I like Netbeans, this problem is frustrating.  I'll try with NB 6.1...

Thanks for the help!

---

### Post by themusicwave on 2008-04-18
You still didn't mention how fast that AMD64 CPU in the machine is, that can make a pretty big difference.

The Sun JVM is definitely faster than the GNU one so that will help you some.

You mention your Vista machine is a Dual core, comparing a dual core's performance to a single core is a pretty dramatic difference.  I'm not sure if that is the case though.

I am wondering if the AMD 64 is just too slow to run Netbeans. 

You do have a decent number of other things running along with Netbeans.  When you stop them does it run better?  Even though they only use 1GB of RAM(which is quite a bit really), what are they doign to the CPU?  You can't just look at the RAM.

Not knowing the PC's Speed and cores makes it hard to really tell how much is too much stuff running at once is too much.

---

### Post by t_ras on 2008-04-18
It is 1GHrz clock (one core), ti is suposed to be equibalent to Intels 3GHz. 
Average load without netbeans is less then 1%. with NB running it is just a litle higher, but it has lots of peaks taking it to 80%, actuly every time I change tab (between already opens tabs) it does it. 
Right now with the aditional memory it came to the situaltion that after it finishes loading every thing it work slow, but at leats I can work with it, previewsly it was unworkable.

---

### Post by themusicwave on 2008-04-18
> **t_ras said:**
> It is 1GHrz clock (one core), ti is suposed to be equibalent to Intels 3GHz. 
Average load without netbeans is less then 1%. with NB running it is just a litle higher, but it has lots of peaks taking it to 80%, actuly every time I change tab (between already opens tabs) it does it. 
Right now with the aditional memory it came to the situaltion that after it finishes loading every thing it work slow, but at leats I can work with it, previewsly it was unworkable.


The extra RAM is definitely needed, Netbeans does use a nice chunk of it and 512 is pretty low.  Ubuntu realistically needs about 256 then you add in Compiz and even more is needed.


I think the CPU speed is the big hold up now.  Even with the overclock, it is "supposed" to be equivalent to a 3GHZ, but it may not be.  Even if it is 3 Ghz, it is still a single core.

You're essentially comparing a 1.7Ghz Dual Core to a 1-3Ghz Single Core.  That's a speed difference of 2-4 times, depending on the overclocks results and such.

At this point you probably either need to reduce the number of processes running or upgrade the machine.  

You mentioned you had several servers running, those all require CPU.  Also if Compiz is running it takes a good chunk of your CPU and RAM.  Try killing of some processes to get to the point where it is usable.  You may just have to turn off Compiz when you run netbeans.

That's really all I can think of right now.

---

### Post by stuffelse on 2008-04-18
FWIW, the newest distro of Netbeans is such a pig, and on top of that I'm using EE to do Java Server Faces projects with Glassfish server, neither of my single core machines runs it well anymore, 3200+ Athlon with 1.5gb and 1.8 Turion64 with 1.12 gb.

Time for an upgrade :-)

---

### Post by pmasiar on 2008-04-18
I have no idea if you use 64 bit code, but if you do, you have another problem: 64bit code in many places uses twice the memory of 32 bit code. I have no idea how exactly JVM works on AMD64, and I do not plan to move to 64 bits myself any time soon (I don't have huge datasets requiring this much virtual memory, so I don't have use for that). Just another thing to think about.

---

### Post by t_ras on 2008-04-20
OK, I took down just a few modules (mainly the web ones) and it works substatialy faster now.

---

