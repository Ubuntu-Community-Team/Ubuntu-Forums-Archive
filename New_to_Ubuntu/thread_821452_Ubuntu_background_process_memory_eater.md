---
title: "Ubuntu? background process memory eater?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by rmx on 2008-06-07
Hello,

I fresh installed 8.04 some time ago.
I don't have compiz neither other memory eating programs (as soon I know)

So, right after system starts, without loading any other program that a terminal I noticed that ubuntu is using 510 MB.

I find this strange, as it was used to be 3.. MB on 7.10.

I think I'm having some kind of memory eating program on background.

but which??

```

top - 13:07:29 up  1:26,  2 users,  load average: 0.37, 0.31, 0.27
Tasks: 116 total,   1 running, 114 sleeping,   1 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.3%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1035372k total,   758736k used,   276636k free,    11076k buffers
Swap:  1156640k total,    36940k used,  1119700k free,   401784k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                 
 6522 rui       20   0 23748  11m 8192 S  0.7  1.1   0:00.88 cpufreq-applet                                                                                                                          
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.18 init                                                                                                                                    
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                                                
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                                             
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0                                                                                                                             
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                                                              
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0                                                                                                                                
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                                                                 
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 kblockd/0                                                                                                                               
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                                                                  
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                                                            
  122 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                                                                 
  153 root      20   0     0    0    0 S  0.0  0.0   0:00.32 pdflush                                                                                                                                 
  155 root      15  -5     0    0    0 S  0.0  0.0   0:00.56 kswapd0                                                                                                                                 
  196 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                                                                   
 1459 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                                                           
 1462 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                                                                   
 1493 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ata/0                                                                                                                                   
 1496 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                                                                
 1502 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                                                                 
 1575 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                                                             
 1578 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                                                               
 1580 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 scsi_eh_1                                                                                                                               
 2622 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 kjournald                                                                                                                               
 2846 root      16  -4  2408  956  380 S  0.0  0.1   0:00.28 udevd                                                                                                                                   
 3194 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                                                               
 3203 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                                                                                                 
 3212 root      15  -5     0    0    0 S  0.0  0.0   0:01.50 ipw2200/0                                                                                                                               
 3216 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                                                                   
 4184 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                                                             
 4592 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty                                                                                                                                   
 4593 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                                                                   
 4597 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                                                                   
 4598 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty                                                                                                                                   
 4600 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                                                                   
 4780 root      20   0  2456 1372  692 S  0.0  0.1   0:00.00 acpid                                                                                                                                   
 4814 syslog    20   0  1936  684  532 S  0.0  0.1   0:00.02 syslogd                                                                                                                                 
 4868 root      20   0  1872  536  444 S  0.0  0.1   0:00.02 dd                                                                                                                                      
 4870 klog      20   0  3648 2492  424 S  0.0  0.2   0:00.14 klogd                                                                                                                                   
 4892 messageb  20   0  3064 1576  796 S  0.0  0.2   0:02.44 dbus-daemon                                                                                                                             
 4908 root      20   0 29400 2400 1940 S  0.0  0.2   0:00.70 NetworkManager                                                                                                                          
 4922 root      20   0  3536 1324 1132 S  0.0  0.1   0:00.00 NetworkManagerD                                                                                                                         
 4935 root      20   0  4112 1112  908 S  0.0  0.1   0:00.00 system-tools-ba                                                                                                                         
 4955 avahi     20   0  2760 1432 1208 S  0.0  0.1   0:00.12 avahi-daemon                                                                                                                            
 4956 avahi     20   0  2760  468  288 S  0.0  0.0   0:00.00 avahi-daemon                                                                                                                            
 4977 root      20   0  4064 1648 1132 S  0.0  0.2   0:00.06 atieventsd                                                                                                                              
 5006 root      20   0  6044 2516 1900 S  0.0  0.2   0:00.00 cupsd                                                                                                                                   
 5012 root      20   0  2684  224  136 S  0.0  0.0   0:00.00 emifreqd                                                                                                                                
 5111 root      20   0  2020  904  776 S  0.0  0.1   0:00.22 dhcdbd                                                                                                                                  
 5130 haldaemo  20   0  6292 4392 3652 S  0.0  0.4   0:02.04 hald                                                                                                                                    
 5133 root      20   0  7884 2356 1604 S  0.0  0.2   0:00.22 console-kit-dae                                                                                                                         
 5195 root      20   0  3352 1196  996 S  0.0  0.1   0:00.32 hald-runner                                                                                                                             
 5222 root      20   0  3444 1320 1160 S  0.0  0.1   0:00.06 hald-addon-inpu                                                                                                                         
 5255 root      20   0  3428 1208 1060 S  0.0  0.1   0:00.00 hald-addon-cpuf                                                                                                                         
 5256 haldaemo  20   0  2204  960  828 S  0.0  0.1   0:00.00 hald-addon-acpi                                                                                                                         
 5284 root      20   0  3420 1148  992 S  0.0  0.1   0:00.04 hald-addon-stor                                                                                                                         
 5352 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                                                               
 5353 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                                                               
 5369 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                                                                
 5398 root      20   0 14060 1552  936 S  0.0  0.1   0:00.00 gdm                                                                                                                                     
 5407 root      20   0 14488 2932 2152 S  0.0  0.3   0:00.00 gdm                                                                                                                                     
 5426 root      20   0  207m  48m  12m S  0.0  4.8   1:13.29 Xorg                                                                                                                                    
 5437 daemon    20   0  1984  424  300 S  0.0  0.0   0:00.00 atd                                                                                                                                     
 5453 root      20   0  2104  892  712 S  0.0  0.1   0:00.00 cron                                                                                                                                    
 5853 root      20   0  207m  48m  12m S  0.0  4.8   0:00.00 Xorg                                                                                                                                    
 5897 root      20   0 13928 4868  636 S  0.0  0.5   0:00.00 timidity                                                                                                                                
 5916 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                                                                   
 6318 rui       20   0 28956 7516 6308 S  0.0  0.7   0:00.08 x-session-manag                                                                                                                         
 6367 rui       20   0  4480  532  268 S  0.0  0.1   0:00.00 ssh-agent                                                                                                                               
 6369 rui       20   0  7244 4304 1904 S  0.0  0.4   0:01.38 gconfd-2                                                                                                                                
 6379 rui       20   0 23032 6596 4752 S  0.0  0.6   0:00.18 seahorse-agent                                                                                                                          
 6382 rui       20   0 14340 2156 1744 S  0.0  0.2   0:00.02 gnome-keyring-d                                                                                                                         
 6385 rui       20   0  2696 1144  788 S  0.0  0.1   0:00.06 dbus-daemon                                                                                                                             
 6386 rui       20   0 60576  26m  10m S  0.0  2.7   0:01.86 gnome-settings-                                                                                                                         
 6401 rui       20   0 39096 8220 3300 S  0.0  0.8   0:02.00 pulseaudio                                                                                                                              
 6406 rui       20   0  5776 2252 1836 S  0.0  0.2   0:00.00 gconf-helper                                                                                                                            
 6416 rui       20   0 15304 2668 1776 S  0.0  0.3   0:02.40 gnome-screensav                                                                                                                         
 6417 rui       20   0 21652  12m 7860 S  0.0  1.3   0:08.06 metacity                                                                                                                                
 6419 rui       20   0 57352  28m  13m S  0.0  2.8   0:08.94 gnome-panel                                                                                                                             
 6424 rui       20   0  104m  43m  14m S  0.0  4.3   0:09.02 nautilus                                                                                                                                
 6426 rui       20   0 40476 3484 2444 S  0.0  0.3   0:00.20 bonobo-activati                                                                                                                         
 6437 rui       20   0 35848  15m 9860 S  0.0  1.5   0:01.46 update-notifier                                                                                                                         
 6438 rui       20   0 15304 5556 4704 S  0.0  0.5   0:00.02 tracker-applet                                                                                                                          
 6444 rui       20   0  5372 2092 1788 S  0.0  0.2   0:00.00 gvfsd                                                                                                                                   
 6445 rui       39  19 31508  10m 2292 S  0.0  1.0   0:00.02 trackerd                                                                                                                                
 6447 rui       20   0 34060  14m 8548 S  0.0  1.4   0:04.34 nm-applet                                                                                                                               
 6448 rui       20   0 24276  11m 7156 S  0.0  1.2   0:00.12 python                                                                                                                                  
 6451 rui       20   0 23828 8152 5612 S  0.0  0.8   0:00.66 gnome-power-man                                                                                                                         
 6458 rui       20   0 29048 1884 1492 S  0.0  0.2   0:00.00 gvfs-fuse-daemo                                                                                                                         
 6501 rui       20   0  5372 2132 1832 S  0.0  0.2   0:00.00 gvfsd-burn                                                                                                                              
 6505 rui       20   0 22132 2688 2208 S  0.0  0.3   0:00.03 gvfsd-trash                                                                                                                             
 6519 rui       20   0 27732  11m 7728 S  0.0  1.1   0:01.18 trashapplet                                                                                                                             
 6525 rui       20   0 49796  16m 9.8m S  0.0  1.6   0:01.42 mixer_applet2                                                                                                                           
 6741 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                                                               
 6892 root      20   0  3880 1552 1264 S  0.0  0.1   0:00.12 wpa_supplicant                                                                                                                          
 6923 dhcp      20   0  2440 1184  868 S  0.0  0.1   0:00.00 dhclient                                                                                                                                
 7056 rui       20   0  106m  27m  12m S  0.0  2.7   0:04.80 gnome-terminal                                                                                                                          
 7058 rui       20   0  2912  856  708 S  0.0  0.1   0:00.00 gnome-pty-helpe                                                                                                                         
 7059 rui       20   0  5728 3140 1448 S  0.0  0.3   0:00.16 bash                                                                                                                                    
 7228 root      20   0  4288 1708  712 S  0.0  0.2   0:00.44 mount.ntfs-3g                                                                                                                           
 7494 rui       20   0 83660  32m  20m S  0.0  3.2   0:14.33 kopete                                                                                                                                  
 7507 rui       20   0 25632 5476 3964 S  0.0  0.5   0:00.04 kdeinit                                                                                                                                 
 7512 rui       20   0 25444 4592 3440 S  0.0  0.4   0:00.02 dcopserver                                                                                                                              
 7515 rui       20   0 25476 6752 5540 S  0.0  0.7   0:00.04 klauncher                                                                                                                               
 7521 rui       20   0 29224  10m 8284 S  0.0  1.0   0:00.68 kded                                                                                                                                    
 7548 rui       20   0 26524 6056 4492 S  0.0  0.6   0:00.00 kio_file                                                                                                                                
 7574 rui       20   0 33692  10m 8224 S  0.0  1.0   0:00.20 knotify                                                                                                                                 
 7577 rui       20   0 11828 5692 4412 S  0.0  0.5   0:01.22 artsd                                                                                                                                   
 8175 rui       20   0 28520  13m 7384 S  0.0  1.4   0:00.44 notification-da                                                                                                                         
 9286 root      20   0     0    0    0 S  0.0  0.0   0:00.12 pdflush                                                                                                                                 
 9301 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                                                                                                               
 9302 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 usb-storage                                                                                                                             
 9467 rui       20   0 14372 3124 2344 S  0.0  0.3   0:00.04 gvfsd-computer                                                                                                                          
10211 rui       21   1  171m  68m  21m S  0.0  6.8   0:22.32 firefox                                                                                                                                 
11302 rui       20   0  2312 1104  844 T  0.0  0.1   0:00.06 top                                                                                                                                     
11571 rui       20   0  2312 1108  844 R  0.0  0.1   0:00.00 top         
```

```
rui@rmx:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035372     573296     462076          0        484     233016
-/+ buffers/cache:     339796     695576
Swap:      1156640      36948    1119692



```
This is with firefox, terminal and kopete on.

thanks

RMX

---

### Post by lostlinuxkiwi on 2008-06-07
Im not sure its necessarily anything to worry about. I have found the same thing with my kubuntu 7.10 and 8.04. 

"linux uses a lot of memory as cache. The memory is free if a program needs it, but if you close firefox for instance, linux keeps it in memory in case you start it up again."

I pinched that from another old post.

also [http://ubuntuforums.org/showthread.p...ghlight=memory](http://ubuntuforums.org/showthread.p...ghlight=memory)

---

