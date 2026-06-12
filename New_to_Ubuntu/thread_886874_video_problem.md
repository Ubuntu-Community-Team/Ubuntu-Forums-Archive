---
title: "video problem"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by cosine352 on 2008-08-11
Hi friends,
I have this problem :
video will not play smoothly. It is slow too. 

The video card is

>  *-display UNCLAIMED     
       description: VGA compatible controller
       product: XGI Volari XP5
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=8


If anybody knows how to solve this, please let me know.

Thanks

---

### Post by Crafty Kisses on 2008-08-11
> **cosine352 said:**
> Hi friends,
I have this problem :
video will not play smoothly. It is slow too. 

The video card is



If anybody knows how to solve this, please let me know.

Thanks

Is it a DVD or a Flash video?

---

### Post by cosine352 on 2008-08-11
any video.

---

### Post by Crafty Kisses on 2008-08-11
> **cosine352 said:**
> any video.

What are your system specs? If you have desktop effects enabled, take them off.

---

### Post by cosine352 on 2008-08-11
It is a 
> Dell inspiron 5160.
1 GB RAM
P4
CPU 2.8 GHz


No desktop effects are ON

---

### Post by Crafty Kisses on 2008-08-11
> **cosine352 said:**
> any video.

> **cosine352 said:**
> It is a 



No desktop effects are ON

When you're playing a video, go into Terminal and type:
```
top
```
Post the results here.

---

### Post by cosine352 on 2008-08-11
Playing in VLC

> Tasks: 130 total,   4 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.2%us,  1.1%sy,  0.0%ni, 95.5%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035184k total,   990636k used,    44548k free,    85268k buffers
Swap:   843372k total,      324k used,   843048k free,   479184k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5664 root      20   0 63292  50m  10m R   87  5.0  16:47.18 Xorg                                                            
**27554 ritesh    20   0  160m  33m  18m S   25  3.3   0:03.24 vlc**                                                             
 6331 ritesh    20   0  260m 125m  29m R   15 12.4  69:16.42 firefox                                                         
26744 ritesh    20   0 41960  21m  12m R   13  2.1   1:33.60 gnome-system-mo                                                 
27576 ritesh    20   0  2304 1036  764 R    4  0.1   0:00.02 top                                                             
 5988 ritesh    20   0 21952  13m 7404 S    2  1.3   2:56.92 metacity                                                        
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.76 init                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.18 migration/0                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.28 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.18 migration/1                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.34 ksoftirqd/1                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.64 events/0                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.68 events/1                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   46 root      15  -5     0    0    0 S    0  0.0   0:00.24 kblockd/0                                                       
   47 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/1                                                       
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                    
  126 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                         
  166 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                         
  167 root      20   0     0    0    0 S    0  0.0   0:01.36 pdflush                                                         
  168 root      15  -5     0    0    0 S    0  0.0   0:00.48 kswapd0                                                         
  209 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                           
  210 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                           
 1395 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                   
 1398 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                           
 1503 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                        
 1530 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                     
 1581 root      15  -5     0    0    0 S    0  0.0   0:01.24 ata/0                  

---

### Post by cosine352 on 2008-08-13
bump

---

