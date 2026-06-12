---
title: "High CPU, &quot;top&quot; CPU% doesn't add up"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Petebacher on 2008-06-17
Installed ubuntu hardy about a week ago. Switched from Gnome over to XFCE to gain some speed on my older Dell laptop. Recently installed Conky and was surprised to see CPU% at 80%+ with only conky, Firefox, and an idle term running.

Below are a couple of "top" outputs. In the first one, when I add up the CPU% of the individual processes, I get 22.8%, not 87.7%. Similar for the second one.  What gives?  

Box is a 550Mhz Dell PIII laptop w/ 512MB RAM.

Thanks!

-Pete

----------
Tasks:  91 total,   1 running,  89 sleeping,   0 stopped,   1 zombie
Cpu(s): 87.7%us,  7.3%sy,  0.0%ni,  4.7%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    515492k total,   506236k used,     9256k free,    14496k buffers
Swap:   738948k total,        0k used,   738948k free,   280240k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5697 peter     20   0  155m  57m  19m S  4.0 11.5   1:17.38 firefox            
 5332 root      20   0 33112  15m 7116 S  3.0  3.0   0:57.40 Xorg               
 5375 root      20   0  7948 4412 1436 S  1.3  0.9   0:09.92 daemon.py          
 5025 messageb  20   0  2816 1200  792 S  0.7  0.2   0:04.22 dbus-daemon        
 5710 peter     20   0 22232  12m 7548 S  0.7  2.4   0:09.60 tray.py            
 6238 peter     20   0 73372  21m  10m S  0.7  4.2   0:04.64 gnome-terminal     
10025 root      20   0  2304 1092  852 R  0.7  0.2   0:03.08 top                
16586 root      20   0     0    0    0 Z  0.7  0.0   0:00.02 sh <defunct>       
    1 root      20   0  2976 1824  544 S  0.0  0.4   0:02.94 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             

-------------------

Tasks:  91 total,   2 running,  88 sleeping,   0 stopped,   1 zombie
Cpu(s): 54.3%us,  4.3%sy,  0.0%ni, 41.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515492k total,   506364k used,     9128k free,    14560k buffers
Swap:   738948k total,        0k used,   738948k free,   280260k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5697 peter     20   0  155m  57m  19m S  3.3 11.5   1:20.67 firefox            
 5332 root      20   0 33244  15m 7116 S  2.7  3.0   1:00.67 Xorg               
 5025 messageb  20   0  2816 1200  792 S  0.7  0.2   0:04.42 dbus-daemon        
 5375 root      20   0  7948 4412 1436 S  0.7  0.9   0:10.44 daemon.py          
 5710 peter     20   0 22232  12m 7548 R  0.7  2.4   0:10.08 tray.py            
 6238 peter     20   0 73372  21m  10m S  0.7  4.2   0:05.18 gnome-terminal     
17008 root      20   0  2304 1088  852 R  0.7  0.2   0:00.10 top                
17125 root      20   0     0    0    0 Z  0.7  0.0   0:00.02 sh <defunct>       
    1 root      20   0  2976 1824  544 S  0.0  0.4   0:02.94 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.28 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

---

### Post by prostar on 2008-07-02
Running top as yourself would only show your processes.  Try ```
sudo top
``` to see system level processes as well.  For more fun try htop (found in synaptic).

---

### Post by hyper_ch on 2008-07-02
> **prostar said:**
> Running top as yourself would only show your processes.

Why are root-owned processes then shown?

---

