---
title: "Overheating - Fresh Ubuntu 16.04.1 LTS"
date: 2016-10-05
forum: New to Ubuntu
---

### Post by stylishdoggy on 2016-10-05
Hey Bros,

I have recently installed ubuntu in dualboot alongside windows 10 in my hp amd laptop. Lately i have been facing weird overheating issue with ubuntu. Once ubuntu selected from GRUB menu, fan goes crazy and laptops heats up like crazy. However, this is not the case with windows 10. Fans are behaving as it should be and heat at minimal while running windows. Please note that fans speed and heat in ubuntu are constant and no drops in both during operations.

Let me know what you bros think about this issue, hence to find the solution

---

### Post by Frogs Hair on 2016-10-05
There are sisters here as well. :)

If you run the following command in the terminal you should see the offending process/s . How exactly did you install Ubuntu ?
 ```
top
```

---

### Post by stylishdoggy on 2016-10-15
> **Frogs Hair said:**
> There are sisters here as well. :)

If you run the following command in the terminal you should see the offending process/s . How exactly did you install Ubuntu ?
 ```
top
```

Following is the output of top command:
```
top - 13:33:03 up 11 min,  1 user,  load average: 0.54, 1.22, 0.93
Tasks: 196 total,   1 running, 195 sleeping,   0 stopped,   0 zombie
%Cpu(s): 15.5 us,  3.4 sy,  0.0 ni, 80.8 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3507624 total,  1181196 free,  1378240 used,   948188 buff/cache
KiB Swap:        0 total,        0 free,        0 used.  1860140 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                           
 1490 kris      20   0 1690324 243848  73940 S  25.9  7.0   5:51.42 compiz                                                                            
  885 root      20   0  353356 103824  34912 S   7.3  3.0   1:17.40 Xorg                                                                              
 2813 kris      20   0  662904  36124  28048 S   3.3  1.0   0:01.45 gnome-terminal-                                                                   
 2182 kris      20   0 1657864 609104 108492 S   1.0 17.4   3:03.06 firefox                                                                           
  648 root      20   0    4400   1372   1280 S   0.7  0.0   0:01.08 acpid                                                                             
 1638 kris      20   0 3341308  73296  20272 S   0.7  2.1   0:02.32 java                                                                              
   14 root      20   0       0      0      0 S   0.3  0.0   0:01.46 kworker/1:0                                                                       
 1440 kris      20   0  208688   7772   7052 S   0.3  0.2   0:00.19 ibus-engine-sim                                                                   
 2830 kris      20   0   48868   3704   3096 R   0.3  0.1   0:00.17 top                                                                               
    1 root      20   0  119596   5672   3908 S   0.0  0.2   0:02.10 systemd                                                                           
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                                          
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.42 ksoftirqd/0                                                                       
    4 root      20   0       0      0      0 S   0.0  0.0   0:01.21 kworker/0:0                                                                       
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                      
    7 root      20   0       0      0      0 S   0.0  0.0   0:01.25 rcu_sched                                                                         
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                                                            
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0                                                                       
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0                                                                        
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1                                                                        
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/1                                                                       
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.53 ksoftirqd/1                                                                       
   15 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H                                                                      
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs                                                                         
   17 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns                                                                             
   18 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 perf                                                                              
   19 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd                                                                        
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback                                                                         
   21 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd                                                                              
   22 root      39  19       0      0      0 S   0.0  0.0   0:00.11 khugepaged                                                                        
   23 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto                                                                            
   24 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd                                                                       
   25 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset     
```

I have installed ubuntu as a dual boot by following these steps:
1. Created un-allocated space in windows 10 disk management
2. Made ubuntu livecd with universal usb installer
3. Booted into livecd and proceeded to install 
4. Made two ext4 journal partitions, one mounting at / for ubunutu and another for /home and installed ubuntu

Thanks for the reply :)

---

