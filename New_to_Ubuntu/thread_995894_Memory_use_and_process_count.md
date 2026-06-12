---
title: "Memory use and process count?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Felix_Akasaka on 2008-11-28
Hello Ubuntu Forums!

I just installed Ubuntu a few weeks ago, completely migrating from windows - it used my whole hard drive? Ubuntu uses 3.4 gigs. I heard that Ubuntu uses less system resources than XP on average, which is very good for my laptop (1.8 ghz dual core + 1 gig ram) but it seems to be using more memory. After start up, I'll be using about 180/944 mb. With Firefox and pandora - 315. It only went up to around 270 on XP. I did some searching for ways to reduce this, but I haven't found much. Any suggestions?

Also, there are 125 processes! What are these? How do I reduce this?

Finally, I have disabled usplash on bootup so I see the wall of text. And, I noticed that some services load twice. Is that supposed to happen?

---

### Post by skymera on 2008-11-28
RAM usage is different to XP. In XP not all the program is kept running in RAM. Ubuntu, it is. 

The task count seems normal, mine says 150.

And i believe the boot screen shows them twice is because it may be starting concurrent.

---

### Post by Michael.Godawski on 2008-11-28
I somewhere read that Linux system really use the ram it has; why being concerned? ram is there to be used, as long as it does not affect the working speed of your system...

Here some info about the usage of ram in linux:

[LIST]
[*][http://www.redhat.com/advice/tips/meminfo.html](http://www.redhat.com/advice/tips/meminfo.html)
[*][http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)
[*][http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)
[/LIST]

---

### Post by cmnorton on 2008-11-28
How are you determining process count and memory use?

Can you provide a summary of your hardware, specifically CPU and RAM?

---

### Post by Michael.Godawski on 2008-11-28
Would be nice to know what your top command says:
```

top
```

---

### Post by hyper_ch on 2008-11-28
or rather use "htop" :)

and in the terminal run:

```

free -m

```

that will show how much memory is really necessary being used and how much is cache.

---

### Post by Felix_Akasaka on 2008-11-28
My specs: 
AMD Turion 64 X2 Mobile TL-50 at 1.8ghz
1 gig ram
Running: Intrepid Ibex, Kernel 2.6.27-7-generic
Gnome 2.24.1

My top 
top - 14:13:40 up 28 min,  1 user,  load average: 0.90, 0.78, 0.58
Tasks:  96 total,   2 running,  94 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.5%us,  4.6%sy,  0.0%ni, 71.5%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:    967596k total,   592040k used,   375556k free,    16876k buffers
Swap:  2827400k total,        0k used,  2827400k free,   238484k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 6200 felix     20   0  382m 184m  31m R   40 19.6   8:45.91 firefox                                                                                         
 5376 felix     20   0 31940 4296 3248 S    8  0.4   1:13.11 pulseaudio                                                                                      
 5136 root      20   0 66296  43m  15m S    3  4.6   1:04.57 Xorg  
* A: PID        = Process Id                                                  * W: S          = Process Status                                               Current Fields:  AEHIOQTWKNMbcdfgjplrsuvyzX  for window 1:Def
Toggle fields via field letter, type any other key to return                  * N: %MEM       = Memory usage (RES)                                            0x00000001  PF_ALIGNWARNges countP)                                          * M: TIME+      = CPU Time, hundredths                                         * A: PID        = Process Id Function                                         * W: S          = Process Status Pid                                           Current Fields:  AEHIOQTWKNMbcdfgjplRsuvyzX  for window 1:Def
Toggle fields via field letter, type any other key to return                  * N: %MEM       = Memory usage (RES)                                            0x00000001  PF_ALIGNWARNges countP))                                         * M: TIME+      = CPU Time, hundredths                                         * A: PID        = Process Id Function                                         * W: S          = Process Status Pid                                           Current Fields:  AeHIOQTWKNMbcdfgjplRsuvyzX  for window 1:Def
Toggle fields via field letter, type any other key to return                  * N: %MEM       = Memory usage (RES)                                            0x00000001  PF_ALIGNWARNges countP))                                         * M: TIME+      = CPU Time, hundredths                                         * A: PID        = Process Id Function                                         * W: S          = Process Status Pid                                           Current Fields:  AEHIOQTWKNMbcdfgjplRsuvyzX  for window 1:Def
Toggle fields via field letter, type any other key to return                  * N: %MEM       = Memory usage (RES)                                            0x00000001  PF_ALIGNWARNges countP))                                         * M: TIME+      = CPU Time, hundredths                                          0x00000800  PF_MEMALLOCg in Function                                           b: PPID       = Parent Process Pid                                            0x00002000  PF_FREE_PAGES (2.5)ed.h>                                           c: RUSER      = Real user name                                                0x00008000  debug flag (2.5)/line(kb)                                          d: UID        = User Id                                                       0x00024000  special threads (2.5)kb)                                                                                                                         0x001D0000  special states (2.5)                                                                                                                             0x00100000  PF_USEDFPU (thru 2.4)

As for free -m
Which number corresponds with the amount of RAM being used by applications?

So, the large amount of processes shouldn't be a concern?

---

### Post by OutOfReach on 2008-11-28
The large number of process in Linux is different from the large number of proccess in Windows.
In Linux, those processes are actually useful (unlike Windows). And they usually do not use a lot of memory.
So, no you shouldn't really be concerned unless your computer is really slow.

---

### Post by hyper_ch on 2008-11-28
when asked to paste some output of a command or file content use [noparse]```

```[/noparse] brackets to make it simpler to read.

---

### Post by Dex73 on 2009-05-09
System Monitor in System/Administration/System Monitor provides some real time data.

---

