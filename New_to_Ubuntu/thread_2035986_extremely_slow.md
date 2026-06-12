---
title: "extremely slow"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by dri94 on 2012-07-31
I installed ubuntu 12.04.. ran the upgrade center, got my nvidia 560m card to cooperate roght. But unbuntu is extremely slow, it constantly hangs and android build times are an hour plus. I have the i7 990x processor in my laptip. Yes laptop and that is the right processor. Ubuntu takes three seconds just to register a click. Cansomeone help me :/

---

### Post by QIII on 2012-07-31
Would you enter the following in the terminal when the machine is idle as a baseline and copy and paste the results between code tags (the # symbol above will generate them)

```
top
```

---

### Post by dri94 on 2012-08-01
```

top - 11:44:01 up 3 min,  2 users,  load average: 1.21, 0.76, 0.33
Tasks: 216 total,   1 running, 215 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.6%us,  0.7%sy,  0.0%ni, 98.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  12297780k total,  2742208k used,  9555572k free,   931264k buffers
Swap:   262140k total,        0k used,   262140k free,  1077544k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1937 adrian    20   0 1278m 208m  48m S   11  1.7   0:08.35 compiz             
 1317 root      20   0  160m  44m  18m S    3  0.4   0:09.84 Xorg               
 2125 adrian    20   0  587m  83m  32m S    3  0.7   0:08.83 firefox            
 2364 adrian    20   0  505m  16m  10m S    0  0.1   0:00.40 gnome-terminal     
 2443 adrian    20   0 17448 1508 1072 R    0  0.0   0:00.07 top                
    1 root      20   0 24452 2388 1348 S    0  0.0   0:01.64 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.17 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0        
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
   11 root      20   0     0    0    0 S    0  0.0   0:00.22 kworker/0:1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1   

```

---

