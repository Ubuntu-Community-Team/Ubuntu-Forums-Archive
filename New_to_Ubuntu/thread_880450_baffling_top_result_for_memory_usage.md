---
title: "baffling top result for memory usage"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-08-05
I have 2 GB of RAM and I don't have too many programs running just now.. certainly nothing to come close to using 2 GB. 

When I run top, I see 
Mem:   2074528k total,  2020144k used,    54384k free,    19856k buffers

Does that really mean almost 95% memory usage??

But when you look at the actual usage in the top list below, the applications clearly aren't using up all the memory.. what is going on??
Is my computer being hacked?


I've marked out the MEM% numbers with :KS below..
top - 01:12:01 up 15:04,  6 users,  load average: 1.24, 0.98, 0.67
Tasks: 163 total,   2 running, 160 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.9%us,  0.4%sy,  0.0%ni, 73.3%id, 25.0%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   2074528k total,  2020144k used,    54384k free,    19856k buffers
Swap:  5020304k total,    39784k used,  4980520k free,  1499880k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU             %MEM    TIME+  COMMAND            
 5807 gkrellmd  20   0 12416 1516 1276 S    2    :KS    0.1  20:51.24 gkrellmd           
 1241 root      20   0  878m  65m  10m S    2    :KS      3.2   8:47.76 Xorg               
 1425 avin    20   0 78292  38m  11m S    2       :KS        1.9   3:33.53 compiz.real        
 1433 avin    20   0 37580  12m 8444 S    1        :KS       0.6   2:32.33 gkrellm            
 4489 avin    20   0  286m 138m  26m S    1        :KS     6.8   1:33.54 firefox            
 8983 avin    20   0 95348  33m  14m S    1       :KS      1.6   0:37.98 brasero            
 6139 root      20   0 54724 1644 1128 S    0      :KS       0.1   3:01.44 collectd           
 1559 root      15  -5     0    0    0 S    0               0.0   0:01.94 ata/0              
 1566 root      15  -5     0    0    0 S    0               0.0   0:02.00 ata/3              
 2078 avin    20   0 69844  19m  10m S    0              1.0   0:01.46 gnome-terminal     
10645 avin    20   0  2308 1148  852 R    0              0.1   0:00.20 top                
    1 root      20   0  2844 1692  544 S    0              0.1   0:01.18 init

---

### Post by hyper_ch on 2008-08-05
run
```

free -m
 
```

and when you post any command or output of file or command output use [noparse]```

```[/noparse] brackets around it.

---

### Post by spin2cool on 2008-08-05
This is normal on a linux system.  A few searches will turn up the hows and whys, but rest assured, your system is not running out of RAM.  If your RAM was all allocated, you'd using far more of your swap.

---

### Post by spin2cool on 2008-08-05
Here are some more details about what's going on with your system:

[http://www.novell.com/coolsolutions/feature/18990.html](http://www.novell.com/coolsolutions/feature/18990.html)

> What actually is happening here is that Linux has cleverly used my free memory to cache the system disk and speed up the system. However, as application needs arise, this memory will be re-allocated to those applications. So in reality, the memory really is "free" for use.

---

### Post by ramjet_1953 on 2008-08-05
Those who write Linux have the attitude that unused memory is wasted memory.

Linux dynamically uses memory for caching and by doing this, your applications will run faster.

Regards,
Roger :cool:

---

### Post by ingrid_ozikem on 2008-08-05
```
             total       used       free     shared    buffers     cached
Mem:          2025       1974         51          0         29       1381
-/+ buffers/cache:        563       1462
Swap:         4902         38       4863

```

Wow.. I learnt a lot in this thread! 

1. Linux expands to take up all the RAM .. not sure how this can help but doesn't sound impossible.

2. free -m shows the actual memory in the buffered row

3. I should use ```

```!!

---

### Post by jimv on 2008-08-05
Basically when you open and close a program, Ubuntu caches it in the RAM in case you open it again later.  If the cache fills up your RAM, Ubuntu clears it out as needed automatically so you don't notice any performance hits.

---

### Post by prshah on 2008-08-05
> **ingrid_ozikem said:**
> 
1. Linux expands to take up all the RAM .. not sure how this can help but doesn't sound impossible.

Not really; your programs use only a part of the memory; the rest of the memory, (usually upto 95%) is used for caching. Caching stores common data in the memory, so that the (relatively slow) disk does not have to be accessed for common data again and again. This results in a speed boost.  That means that the instant more memory is needed by programs, a partial cache part of memory is freed up. This is called a dynamic cache.

Prior to Windows XP, (Windows NT?) the cache was fixed; not dynamic. Dynamic caching is thus not very new; in fact, Vista does it too. XP does it from SP2 onwards. 

Vista also has a feature called ReadyBoost; this moves the caching part to a usb stick, so that RAM is freed up for programs with minimal effect on the cache.

With 2Gb memory, linux will never really run out of memory. Relax and enjoy.

---

### Post by hyper_ch on 2008-08-05
unused ram = wasted ram

in the cli you could use htop instead of top.. that one also shows what is actual memory used, what is cache etc.

---

### Post by fixitdude on 2008-11-30
Install and use "gkrellm" find it on your synaptic package manager.

I like to keep it in the upper right corner, and set it to appear on all desktops.

It will also show CPU usage and ethernet use.

---

