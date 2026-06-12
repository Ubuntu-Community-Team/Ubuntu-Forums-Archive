---
title: "High Cpu usage"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by lillypop on 2008-07-09
My cpu usage is running very high even with no apps open my computer is slow .
I my pc specs are intel celeron 2.00GHz cpu 756.6 mb ram nvidia geforce 6200 128mb graphics card 40 gb and 20 gb hard drive.

i have the nvidia glx new drivers installed. I'm running hardy heron 8.04 lts

Heres some info on my cpu usage.

laurie@laurie-desktop:~$  top | head -n20

top - 08:37:03 up  1:18,  3 users,  load average: 3.46, 3.14, 3.21
Tasks:  87 total,   4 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.1%us, 45.4%sy, 21.9%ni, 14.8%id,  1.7%wa,  0.1%hi,  2.0%si,  0.0%st
Mem:    774768k total,   416524k used,   358244k free,    13468k buffers
Swap:  1566296k total,    38668k used,  1527628k free,   202220k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+       COMMAND            
   45 root      15  -5     0    0    0 R 65.9  0.0  29:04.66       kacpi_notify       
 4819 haldaemo  20   0  6188 4020 3388 S  7.7  0.5   2:39.70       hald               
 5150 root      20   0  2456 1428  692 S  7.7  0.2   2:57.52       acpid              
 4906 haldaemo  20   0  2204  980  848 S  5.8  0.1   2:00.32       hald-addon-acpi    
 5009 root      20   0 45980  35m  10m S  3.9  4.6   2:38.89       Xorg               
 5459 laurie    20   0 15236 2588 1688 S  3.9  0.3   0:08.78       gnome-screensav    
 5895 syslog    30  10  1936  644  512 R  3.9  0.1   1:01.90       syslogd            
 6002 laurie    20   0 73952  19m  10m S  3.9  2.6   0:01.04       gnome-terminal     
 6022 laurie    20   0  2304  996  764 R  3.9  0.1   0:00.02        top                
 5227 root      20   0  1872  536  444 S  1.9  0.1   0:39.81        dd                 
 5604 laurie    20   0  204m  71m  24m R  1.9  9.5   3:25.90       firefox            
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.58        init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00        kthreadd           
laurie@laurie-desktop:~$  top | head -n20



top - 08:37:50 up  1:19,  2 users,  load average: 3.51, 3.20, 3.23
Tasks:  83 total,   4 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.2%us, 45.7%sy, 21.7%ni, 14.6%id,  1.7%wa,  0.1%hi,  2.0%si,  0.0%st
Mem:    774768k total,   354596k used,   420172k free,    13700k buffers
Swap:  1566296k total,    38668k used,  1527628k free,   201972k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   45 root      15  -5     0    0    0 R 70.1  0.0  29:34.11 kacpi_notify       
 5150 root      20   0  2456 1428  692 S  7.8  0.2   3:00.52 acpid              
 4819 haldaemo  20   0  6188 4020 3388 S  5.8  0.5   2:42.37 hald               
 4906 haldaemo  20   0  2204  980  848 S  5.8  0.1   2:02.35 hald-addon-acpi    
 5009 root      20   0 43076  32m 8160 S  3.9  4.3   2:41.01 Xorg               
 5229 klog      20   0  3740 2652  424 S  3.9  0.3   0:26.82 klogd              
 6024 laurie    20   0  2304  996  764 R  3.9  0.1   0:00.02 top                
 5227 root      20   0  1872  536  444 S  1.9  0.1   0:40.47 dd                 
 5895 syslog    30  10  1936  644  512 R  1.9  0.1   1:02.93 syslogd            
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.58 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
laurie@laurie-desktop:~$  top | head -n20



top - 08:38:02 up  1:19,  2 users,  load average: 3.43, 3.19, 3.22
Tasks:  83 total,   3 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.2%us, 45.8%sy, 21.6%ni, 14.6%id,  1.7%wa,  0.1%hi,  2.0%si,  0.0%st
Mem:    774768k total,   355068k used,   419700k free,    13728k buffers
Swap:  1566296k total,    38668k used,  1527628k free,   202464k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   45 root      15  -5     0    0    0 R 74.0  0.0  29:42.67 kacpi_notify       
 4819 haldaemo  20   0  6188 4020 3388 S  7.8  0.5   2:43.15 hald               
 5150 root      20   0  2456 1428  692 S  7.8  0.2   3:01.39 acpid              
 4906 haldaemo  20   0  2204  980  848 S  5.8  0.1   2:02.94 hald-addon-acpi    
 5895 syslog    30  10  1936  644  512 R  3.9  0.1   1:03.24 syslogd            
 6026 laurie    20   0  2304  996  764 R  3.9  0.1   0:00.02 top                
 5009 root      20   0 41844  32m 8160 S  1.9  4.3   2:41.38 Xorg               
 5227 root      20   0  1872  536  444 S  1.9  0.1   0:40.66 dd                 
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.58 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
laurie@laurie-desktop:~$ 

First one says i have 3 users ? i'm the only user on my system.

anyone think of a way i can lower my cpu usage so i can actually run programs without hangs and freezes.

TIA

---

### Post by aktiwers on 2008-07-09
Hi,

You can type in :
```
who
``` to see what users are logged on. 

I normally only have 2 users running (I think that is default) but maybe you also have a root running now?

About your CPU problem, it is kacpi_notify that is eating your CPU. I found this thread for you, that has some different solutions to the problem.
[http://ubuntuforums.org/showthread.php?t=399619](http://ubuntuforums.org/showthread.php?t=399619)

Good luck :)

---

### Post by lillypop on 2008-07-09
Thanks i'm going to try turning acpi off see if that helps.

---

### Post by aktiwers on 2008-07-09
Great! Let us know how it goes ;)

---

### Post by lillypop on 2008-07-09
can only boot on the recovery kernal otherwise it doesn't detect my graphics card or monitor :/

---

