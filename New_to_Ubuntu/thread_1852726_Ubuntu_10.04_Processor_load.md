---
title: "Ubuntu 10.04: Processor load"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by ShawnxBuntu on 2011-09-30
Hello everyone.. im hav ing a very hard time.. understanding why My CPU is being eatting alive by Firefox.bin aka FireFox.. when i do
                                            uname -r 2.6.32-34-generic Which is what kernel im running.. when i do top..
```
 top - 18:11:52 up 13 min,  2 users,  load average: 1.14, 0.90, 0.60
Tasks: 232 total,   2 running, 230 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.9%us,  0.3%sy,  0.0%ni, 98.4%id,  0.3%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   6107652k total,  1019956k used,  5087696k free,    32960k buffers
Swap: 17890296k total,        0k used, 17890296k free,   467684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1374 root      20   0  135m  43m  19m S    4  0.7   0:31.15 Xorg               
 2149 shawn     20   0  206m  14m  10m R    2  0.2   0:00.55 gnome-terminal     
 2056 shawn     20   0  669m 102m  32m S    2  1.7   0:32.18 firefox-bin        
 2220 shawn     20   0 19348 1512 1064 R    1  0.0   0:00.07 top                
    1 root      20   0 23696 1960 1276 S    0  0.0   0:02.20 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/3

               Thats with fire fox running but not on YouTube.. now watch..
  shawn@shawn-laptop:~$ uname -r
2.6.32-34-generic
shawn@shawn-laptop:~$ top

top - 18:14:26 up 16 min,  2 users,  load average: 1.23, 1.01, 0.68
Tasks: 232 total,   2 running, 230 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.9%us,  0.5%sy,  0.0%ni, 96.4%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6107652k total,  1057728k used,  5049924k free,    33252k buffers
Swap: 17890296k total,        0k used, 17890296k free,   475812k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2084 shawn     20   0  673m  67m  25m S   18  1.1   0:17.51 plugin-containe    
 1374 root      20   0  136m  44m  20m S    3  0.7   0:36.40 Xorg               
 1605 shawn      9 -11  336m 6032 4432 S    2  0.1   0:02.06 pulseaudio         
 2056 shawn     20   0  669m 107m  32m S    1  1.8   0:38.58 firefox-bin        
 2149 shawn     20   0  207m  14m  10m S    1  0.2   0:01.39 gnome-terminal     
 1603 shawn     20   0  165m  10m 8696 S    1  0.2   0:01.13 metacity           
 2220 shawn     20   0 19348 1512 1064 R    0  0.0   0:00.70 top                
    1 root      20   0 23696 1960 1276 S    0  0.0   0:02.20 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/2        
```


its more plugin-container.. i deleted npwrapper because the npviewer.bin was takin all my cpu up.. i have aintel core i7.. 4 cores 8 logical cores? would it make diff?..

---

### Post by MG&amp;TL on 2011-09-30
Try a different browser (it doesn't have to be permanent) and see if it's firefox, or a problem with flash. And your kernel's not going to change with your web activity y'know....;)

---

### Post by acrazyplayer on 2011-10-01
I think you now understand why so many people don't like adobe flash. As was already said try a different browse, google crhome comes with its own version of flash player and also handles things differently, it is also harder to pin point becuase it will create quite a few different things of the same name in "top" but it still may be of help. good luck

---

