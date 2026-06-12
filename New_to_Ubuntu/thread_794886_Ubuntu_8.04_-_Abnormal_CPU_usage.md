---
title: "Ubuntu 8.04 - Abnormal CPU usage"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by susiriss on 2008-05-15
Hello there,
         I installed the Ubuntu 8.04 recently and found that the system monitor as well as the "top" command reports an abnormally high CPU usage (in both cores of the CPU). According to "top" the culprits are "kacpid" and " kacpi_notify" (see below). A normal Internet search gives whole lot of regarding this problem with no specific solution. 

```
iTasks: 113 total,   4 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us, 33.3%sy,  0.0%ni, 55.3%id,  0.0%wa, 10.1%hi,  0.0%si,  0.0%st
Mem:   1024864k total,   556264k used,   468600k free,    13108k buffers
Swap:  4192924k total,        0k used,  4192924k free,   234640k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
   51 root      15  -5     0    0    0 R   69  0.0   3:04.11 kacpid                                                                                          
   52 root      15  -5     0    0    0 R   11  0.0   0:30.10 kacpi_notify                                                                                    
 5335 root      20   0  386m  38m 7092 R    3  3.9   0:08.00 Xorg                                                                                            
 5717 sampath   20   0 21648  14m 5840 S    1  1.4   0:02.40 compiz.real                                                                                     
 5858 sampath   20   0 83972  22m  11m S    1  2.3   0:00.76 gnome-terminal                                                                                  
 5625 sampath   20   0 28472 5736 3300 S    0  0.6   0:00.23 pulseaudio                                                                                      
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.26 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   47 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0                                                                                       
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
  132 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
  174 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  175 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  176 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                         
  217 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  218 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 1498 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1500 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd 
```

My CPU is an Intel Dual Core 1.8 GHz with 1MB cache.. has 1GB of RAM

Is this a bug with Ubuntu ????
Are there any soulutions ??? 

Thank You!

---

### Post by subzero316 on 2008-05-15
Well then disable it i think these 2 steps should do:
```
sudo gedit /boot/grub/menu.lst
``` 
then add

"acpi=off" and "apm=off" 

then your  kernel line must be something like this:

/boot/vmlinuz-2.6.22-14-generic root=UUID=dee9823a-db44-4ddd-9643-8cda262ef09c ro **acpi=off apm=off** quiet splash

---

