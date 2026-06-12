---
title: "Firefox constantly hangs (Grays out)"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by prototype_angel on 2008-07-21
I use ubuntu hardy with firefox 3, on a core 2 duo desktop with 2gb ddr2 ram, and a powerful nvidia graphics card. a modest system by all means.

I installed ubuntu freshly on a new machine.

When I run firefox(and only firefox), and start using it, it starts to go gray, and is not responding, and System monitor reports high cpu usage(though not by firefox), and top also does the same.

Is there a fix to prevent firefox from graying out everytime? I didn't see any output on stdout and stderr, and running it through a profiler indicates no major memory problems, and RAM isn't being used fully.

Thanks for your reply

---

### Post by philinux on 2008-07-21
Whats the graphics card and what's the process thats eating resources.

Best way to show the process is run the command 

top

in a terminal

---

### Post by Joeb454 on 2008-07-21
Disable compiz and try again :)

---

### Post by prototype_angel on 2008-07-21
This happens when a page finishes loading, and disabling compiz doesen't help eiher.

The output of top is:
```

anirudhs@deepthought:~$ top

top - 23:53:12 up 1 day,  1:25,  2 users,  load average: 1.43, 0.48, 0.19
Tasks: 119 total,   1 running, 118 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.9%us,  3.9%sy,  0.0%ni, 48.5%id, 23.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035348k total,   785828k used,   249520k free,    32228k buffers
Swap:  1951856k total,    57744k used,  1894112k free,   451512k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17584 anirudhs  20   0  124m  48m  19m S   47  4.8   0:06.26 firefox            
17454 anirudhs  20   0 67348  28m 9428 S    6  2.8   0:02.82 compiz.real        
17280 root      20   0 85524  31m 8000 S    5  3.1   0:04.44 Xorg               
    1 root      20   0  2844  288  236 S    0  0.0   0:01.30 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.20 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.50 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.46 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.28 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   47 root      15  -5     0    0    0 S    0  0.0   0:02.30 kblockd/0          
   48 root      15  -5     0    0    0 S    0  0.0   0:00.86 kblockd/1          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             

```

I have an nvidia 7600gt and I can play high end videogames on it.
Firefox slows when I try to enter text, open a new page, etc.

---

### Post by boppp on 2008-07-25
I have partly the same problem, altough Firefox does not turn grey (but it does hang some times when i click on a link).

Every time i click on a link in firefox or open a page or what else my CPU gets hotter en htop tells me tat firefox is using 75 to 100% of my CPU. But when all the pages are loaded inside firefox it only uses 1%. 

I have this since a few weeks but hoped that it would be fixxed in the next firefox update, but it unfortunately wasnt :( Anyone know any fixes or anyone else has the same problem?

> 
bob@bob-laptop:~$ uname -a
Linux bob-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

> 
bob@bob-laptop:~$ firefox -v
Mozilla Firefox 3.0.1, Copyright (c) 1998 - 2008 mozilla.org


---

