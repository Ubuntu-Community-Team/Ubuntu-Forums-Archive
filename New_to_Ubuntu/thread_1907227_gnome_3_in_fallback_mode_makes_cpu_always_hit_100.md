---
title: "gnome 3 in fallback mode makes cpu always hit 100"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2012-01-11
i tryed to google it.  but i didnt get any results. can you guys help me out. my computer dosent seem slow at all. but its always consuming 100 cpu

---

### Post by carl4926 on 2012-01-11
Can you open a terminal and run : top

what do you see

---

### Post by ilikelinuxitisthebest on 2012-01-11
```
top - 22:05:15 up 1 day,  3:08,  1 user,  load average: 2.70, 3.01, 2.62
Tasks: 150 total,   3 running, 145 sleeping,   0 stopped,   2 zombie
Cpu(s): 49.0%us, 50.5%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   2061972k total,  1849920k used,   212052k free,    53084k buffers
Swap:  2096124k total,     2460k used,  2093664k free,  1459068k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10013 waffles   20   0  109m  37m  18m R  100  1.8  12:28.96 docky              
 8758 waffles   20   0  122m  41m  18m R   88  2.1 105:32.28 docky              
11459 root      20   0 79636  15m 8488 S    5  0.8   0:50.34 Xorg               
12089 waffles   20   0 79192  14m  10m S    4  0.7   0:01.35 gnome-terminal     
11679 waffles   20   0  110m  37m  19m S    1  1.9   0:25.59 docky              
  827 root      20   0  3420  612  464 S    1  0.0   0:14.81 irqbalance         
10581 root      20   0     0    0    0 S    1  0.0   0:02.62 kworker/0:2        
11646 waffles   20   0  118m  13m 9572 S    1  0.6   0:05.79 metacity           
12147 waffles   20   0  2820 1160  860 R    1  0.1   0:00.16 top                
11766 waffles   20   0 84312  30m  10m S    0  1.5   0:06.48 ubuntuone-syncd    
    1 root      20   0  3332 1676 1120 S    0  0.1   0:01.60 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:10.24 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1  
```

---

### Post by carl4926 on 2012-01-11
You can see then
Also 2 Zombie processes

Reboot will likely clear it up

---

