---
title: "Swap is not use"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by akina_ian on 2011-12-19
**Why is it the swap is not in use, Is this a problem. **

[IMG]http://i.lulzimg.com/e4b4637a57.png[/IMG]

---

### Post by Lars Noodén on 2011-12-19
It's not a problem.  It just means that you have plenty of RAM.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by akina_ian on 2011-12-19
> **Lars Noodén said:**
> It's not a problem.  It just means that you have plenty of RAM.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


One thing more my CPU usage always go ups , sometimes its loggy . but I'm just browsing.

---

### Post by Frogs Hair on 2011-12-19
It does look a little high for browsing . Type the following command in the terminal to view your processes . This will use less resources than the opening the  system monitor which can cause CPU use to jump .
```
top
```

---

### Post by akina_ian on 2011-12-19
> **Frogs Hair said:**
> It does look a little high for browsing . Type the following command in the terminal to view your processes . This will use less resources than the opening the  system monitor which can cause CPU use to jump .
```
top
```


**This what it show** ,** what do i need to do?**

```
top - 00:15:57 up 25 min,  2 users,  load average: 0.44, 0.38, 0.31
Tasks: 144 total,   3 running, 140 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.4%us,  3.4%sy,  0.0%ni, 93.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1015660k total,   741860k used,   273800k free,    43868k buffers
Swap:   975868k total,        0k used,   975868k free,   381676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                            
 1085 root      20   0 50696  15m 8076 R  5.3  1.6   1:31.62 Xorg                                               
top - 00:17:13 up 26 min,  2 users,  load average: 0.13, 0.29, 0.29
Tasks: 144 total,   1 running, 142 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.7%us,  2.0%sy,  0.0%ni, 94.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1015660k total,   736552k used,   279108k free,    44004k buffers
Swap:   975868k total,        0k used,   975868k free,   376596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                
 1085 root      20   0 50972  15m 8076 S  2.7  1.6   1:35.48 Xorg                                                                   
 2885 ian       20   0 53892  21m  12m S  1.3  2.2   0:09.85 gnome-about                                                            
 2909 ian       20   0 92152  14m  10m S  1.3  1.4   0:01.79 gnome-terminal                                                         
 1385 ian       20   0 56456  13m 8984 S  0.7  1.3   0:22.27 compiz                                                                 
 1704 ian       20   0  491m 108m  31m S  0.3 11.0   3:05.69 firefox-bin                                                            
 2968 ian       20   0  2632 1144  860 R  0.3  0.1   0:00.20 top                                                                    
    1 root      20   0  2920 1812 1276 S  0.0  0.2   0:00.59 init                                                                   
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                               
    3 root      20   0     0    0    0 S  0.0  0.0   0:05.28 ksoftirqd/0                                                            
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                            
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                                 
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                                                                  
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                                                            
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                                            
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd                                                            
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd                                                                

```

---

### Post by Frogs Hair on 2011-12-19
Under %CPU  it doesn't  appearer to be high at all in the terminal output .  Top is just a monitoring tool you can use to check what processes are using the most resources .

---

### Post by Slim Odds on 2011-12-19
Your main memory is only 40% used, why do you think that swap should be used?

Don't panic, linux knows what it's doing.

---

### Post by collisionystm on 2011-12-19
top and gnome sys monitor show completely different results with CPU usage.
I could not tell you which is actually correct. Even if you leave the 2 running at the same time you will see discrepancies.

I suggest you install htop and run that

sudo apt-get install htop

htop

---

### Post by akina_ian on 2011-12-19
> **collisionystm said:**
> top and gnome sys monitor show completely different results with CPU usage.
I could not tell you which is actually correct. Even if you leave the 2 running at the same time you will see discrepancies.

I suggest you install htop and run that

sudo apt-get install htop

htop

 htop  what is this sir?

---

### Post by Lars Noodén on 2011-12-20
> **akina_ian said:**
> htop  what is this sir?

[htop](http://manpages.ubuntu.com/manpages/oneiric/en/man1/htop.1.html) is like 'top' but with scrolling and a few other features.

---

### Post by jwbrase on 2011-12-20
No need to have him looking at top or htop. The question I have is what the machine specs are. From the amount of RAM he has, and the fact that the CPU is single-core, I suspect he has an old machine or a netbook.

akina: What kind of computer do you have? In particular, what kind of CPU does it have? Also, as others have said, don't worry that it isn't using swap. Computers only use swap if the programs that are running need more RAM than the computer has. Swap is a lot slower than RAM, so it's actually a good thing not to be using it if all the programs that are running will fit into RAM.

---

### Post by guyver_dio on 2011-12-20
A side question while we're on the subject of the swap partition, how big do people usually make it? Or does it depend on amount of ram you have?

I have 2GB of ram and I thought a 2GB partition would do?

---

### Post by wildmanne39 on 2011-12-20
Hi, 2 gigs of ram is plenty for you.

---

### Post by jwbrase on 2011-12-20
If you want to hibernate, you need at least as much swap as RAM. Otherwise, how much you need depends on how much RAM you have and what kind of programs you expect to be running. On a machine with lots of RAM, you might not need any swap at all.

Back in the day, when RAM was more expensive, it was actually fairly typical to allocate twice as much swap as RAM.

---

### Post by Hellweek on 2011-12-20
> **guyver_dio said:**
> A side question while we're on the subject of the swap partition, how big do people usually make it? Or does it depend on amount of ram you have?

I have 2GB of ram and I thought a 2GB partition would do?


The rule of thumb, your swap file should be 2x your memory.  However, many times machines have so much ram you will never hit the swap file.

---

### Post by CoffeeRain on 2011-12-20
Hi, looking at this person's top output, I checked mine, and I thought it would be nice to know if this was normal. Sorry for the format, but when I formatted it, it still came out bad. Here it is--

```

Processes: 133 total, 2 running, 1 stuck, 130 sleeping, 328 threads    08:26:18
Load Avg: 0.17, 0.30, 0.46  CPU usage: 16.73% user, 11.42% sys, 71.83% idle
SharedLibs: 74M resident, 2164K data, 4860K linkedit.
MemRegions: 12352 total, 291M resident, 16M private, 156M shared.
PhysMem: 460M wired, 559M active, 183M inactive, 1202M used, 78M free.
VM: 82G vsize, 437M framework vsize, 520108(0) pageins, 135504(0) pageouts.
Networks: packets: 4286669/2911M in, 3806533/2513M out.
Disks: 773882/10G read, 777084/13G written.

PID    COMMAND      %CPU TIME              #TH  #WQ  #POR #MREG RPRVT  RSHRD  RSIZE
15056  top                 16.8 00:01.85       1/1  0    22   35    776K   268K   1292K 
15055  mdworker     0.0  00:00.26 3     1      47   63    880K   6368K  2280K 
15054  PubSubAgent  0.0  00:00.68      4      2    71   68    3792K  5564K  8232K 
15038  bash              0.0  00:00.03         1      0    17   26    316K   268K   992K 
15037  login              0.0  00:01.47         1      0    20   55    408K   268K   1104K 
15033  Terminal       27.6 00:06.58        5      1    107- 109   2504K+ 12M    7368K+
15027  mdworker     0.0  00:01.28         3      1    48   77    2144K  7448K  7232K 
14973  TextWrangler 0.0  00:02.87       3      1    106  230   7408K  21M    23M 
14894  webfilterctl   0.0  00:00.04         1      0     16   25    176K   280K   752K 
14856  natd               0.0  00:25.69         1      0     8    30    252K   268K   384K 

```

---

### Post by dFlyer on 2011-12-20
I have 4 gig ram and a 8 gig swap partition on my laptop. I use the laptop for my photography and seldom ever use any swap space even if the computer has been up for a month or more. Linux knows how to use memory and I wouldn't worry about it.

---

### Post by BC59 on 2011-12-20
From Ubuntu Community Documentation

> [How much swap do I need]("http://https://help.ubuntu.com/community/SwapFaq")?
As a base minimum, it's highly recommended that the swap space should be equal to the amount of physical memory (RAM). Also, it's recommended that the swap space is twice the amount of physical memory (RAM) depending upon the amount of hard disk space available for the system (although this "recommendation" dates back from a time when physical RAM was very expensive and most Unix systems ran with many processes in swap space - a situation that hardly applies in most situations these days, but ancient Unix/Linux myths like this "recommendation" tend to survive well past their "use by" dates). In reality, if you use hibernation you need what was outlined in the relevant paragraph above, otherwise you need as much swap space as your system will use - which actually may be very little in a modern hardware setup. The only downside to having more swap space than you will actually use is the disk space you will be reserving for it.

---

### Post by grahammechanical on 2011-12-20
Another thing to keep in mind when looking at System Monitor is that you are seeing the amount of Memory allocated not the amount of memory used. 

Linux allocates memory as it is needed. As the memory usage increases it allocates more memory so that it always has spare capacity. If there is an increase in memory usage then Linux will keep the allocation of memory higher even though the need has gone to reduce the time lag should the need for more memory be repeated.

Just start opening some programs and you will see the memory allocation increase with even swap memory being allocated. Close those programs and then wait to see how long it takes for the memory allocation to decrease.

As regards CPU usage, what video card do you have? Does it have much of its own memory? Your CPU might be having to do work that the video card cannot do. So, this might explain why it seems that CPU usage increase even though you are not opening and using more programs.

Regards.

---

### Post by jwbrase on 2011-12-20
> **CoffeeRain said:**
> Hi, looking at this person's top output, I checked mine, and I thought it would be nice to know if this was normal.

That all depends on what your machine specs are.

---

### Post by akina_ian on 2011-12-21
> **jwbrase said:**
> No need to have him looking at top or htop. The question I have is what the machine specs are. From the amount of RAM he has, and the fact that the CPU is single-core, I suspect he has an old machine or a netbook.

akina: What kind of computer do you have? In particular, what kind of CPU does it have? Also, as others have said, don't worry that it isn't using swap. Computers only use swap if the programs that are running need more RAM than the computer has. Swap is a lot slower than RAM, so it's actually a good thing not to be using it if all the programs that are running will fit into RAM.

yeah your right its an old acer aspire 4310 , Intel Celeron Processor , 1.6GHZ Single core , 512MB DDR2 of ram , 120GB HDD.

---

### Post by jwbrase on 2011-12-21
> **akina_ian said:**
> yeah your right its an old acer aspire 4310 , Intel Celeron Processor , 1.6GHZ Single core , 512MB DDR2 of ram , 120GB HDD.

According to the System Monitor, you have more than 512MB of RAM.

Anyways, for a 1.6 GHz single core, I don't think the CPU loads you're experiencing are at all unusual. You just have a slow machine.

---

### Post by collisionystm on 2011-12-21
Something that will help your CPU....

Install compiz-config-settings-manager

run it

click on OpenGL

uncheck, sync to VBLANK

set filter to FAST

exit

log out of ubuntu and back in

you will notice a huge difference.

---

