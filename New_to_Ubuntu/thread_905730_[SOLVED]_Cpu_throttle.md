---
title: "[SOLVED] Cpu throttle"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by lakersforce on 2008-08-30
How can I find out why my cpu is constant throttling?

"My laptop is suddenly very noisy!"

I tried to restart the machine, even tried to turn it off for a half-hour. It has not behaved like this before.

---

### Post by lakersforce on 2008-08-30
A picture of cpu graphs. This is in completely idle mode.

---

### Post by lakersforce on 2008-08-30
Again a screen of my laptop being completely idle!

---

### Post by lakersforce on 2008-08-30
60 seconds idle...

---

### Post by liquidfunk on 2008-08-30
What are your specs?

 And open a Terminal and type Top. How many processes are there? And what is at the top?

---

### Post by lakersforce on 2008-08-31
```
top - 12:10:59 up 8 min,  2 users,  load average: 0.15, 0.89, 0.60
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.2%us,  0.8%sy,  0.0%ni, 97.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2067220k total,   730692k used,  1336528k free,    17124k buffers
Swap:  6056464k total,        0k used,  6056464k free,   373040k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                           
 5415 root      20   0  364m  41m 8172 S    2  2.1   0:14.26 Xorg                                                                              
 6546 rune      20   0 68784  18m  10m S    1  0.9   0:00.88 gnome-terminal                                                                    
 6001 rune      20   0 23688  16m 7068 S    1  0.8   0:04.26 compiz.real                                                                       
 6569 rune      20   0  2308 1132  856 R    1  0.1   0:00.94 top                                                                               
 6018 rune      20   0 75172  30m  13m S    0  1.5   0:07.89 skype                                                                             
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.30 init                                                                              
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                          
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                       
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                       
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                        
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                       
    7 root      15  -5     0    0    0 S    0  0.0   0:00.46 ksoftirqd/1                                                                       
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                        
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                          
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                          
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                           
   46 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0    
```

---

### Post by Tom--d on 2008-08-31
DO not use System Monitor to see what % your CPU is at because there is a bug with system Monitor which causes your cpu to go higher.

Install htop
```
sudo apt-get install htop
```
Then, in terminal, type htop and post a screeny (if you want)

Also, 
post the outcome of
```
acpi -t
```

---

### Post by lakersforce on 2008-08-31
You are right. htop (and top) does not show the same figures as gnome system monitor. And my laptop is not as noisy right now as it was yesterday. I'll post the screenies if it starts to misbehave again.

---

