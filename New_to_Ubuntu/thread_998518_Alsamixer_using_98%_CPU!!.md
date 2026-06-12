---
title: "Alsamixer using 98% CPU?!?!?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by firebirdworks on 2008-11-30
Lately I've been having problems with my ubuntu machine.  It is incredibly quiet, even though ALL settings are at 100%.  Today, I ran the top command, and this was the result:

```
top - 21:53:02 up 3 days, 17:47,  2 users,  load average: 2.41, 2.37, 2.30
Tasks: 147 total,   2 running, 144 sleeping,   0 stopped,   1 zombie
Cpu(s): 96.7%us,  3.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%
Mem:   1033432k total,   924560k used,   108872k free,     9052k buffers
Swap:  3028212k total,   121164k used,  2907048k free,   198324k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND        
 5814 mburke    20   0 2582m  18m 2588 S   93  1.9   5209:37 FahCore_81.exe 
20652 root      20   0 78820 2108 1752 R   92  0.2   4726:07 alsamixer      
  310 mburke    20   0  315m 161m  28m S    6 16.0  56:40.42 firefox        
 5211 root      20   0  463m 113m  26m S    5 11.3  26:14.32 Xorg           
 5634 mburke    20   0 21960 5352 4288 S    1  0.5   0:49.70 gnome-screensav
 6982 mburke    20   0 92596  22m  12m S    1  2.2   0:00.72 gnome-terminal 
 7002 mburke    20   0  2428 1172  888 R    1  0.1   0:00.06 top            
 1945 root      15  -5     0    0    0 S    0  0.0   1:46.48 scsi_eh_0      
 5623 mburke    20   0 29568  20m 7588 S    0  2.0   2:25.09 compiz.real    
 5638 mburke    20   0 26872  14m 9180 S    0  1.4   0:41.29 gtk-window-deco
 5715 mburke    20   0 2594m 6508 4656 S    0  0.6   0:35.04 fah.exe        
    1 root      20   0  3060 1368  520 S    0  0.1   0:01.54 init           
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd       
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.14 migration/0    
    4 root      15  -5     0    0    0 S    0  0.0   0:24.30 ksoftirqd/0    
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.40 watchdog/0     
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/1    

```

Anyone know what is going on?

---

### Post by binbash on 2008-11-30
what is FahCore_81.exe ? this maybe wine bug

---

### Post by firebirdworks on 2008-11-30
> **binbash said:**
> what is FahCore_81.exe ? this maybe wine bug

Its folding@home.

[http://folding.stanford.edu]("http://folding.stanford.edu")

---

### Post by firebirdworks on 2008-11-30
From past experiences, rebooting/powercycling doesn't help any either, and it's been going on for quite a while.

I'm not sure if they are related, but whenever I go to play video, it flashes alot.  The video is barely playable because of it.  It all started when I downloaded some codec.

---

