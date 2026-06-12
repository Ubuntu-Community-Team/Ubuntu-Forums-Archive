---
title: "Major system fault"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by Gnusboy on 2014-01-05
My Ubuntu 12.04 system has suddenly started freezing, going to dim screen and is very slow to respond to any input. I opened the system monitor and it showed it was using 2.7+++ gigs of ram - with only a couple of programs running.
It started in Firefox with a dim and freeze. I tried closing all programs except system monitor and it was still very slow. A "wait or force quit" window came up and the screen dimmed, then went back to normal, but every click by the mouse made it dim and freeze again.
I looked at the sys monitor and it showed that the system was using more than 2.7 GB of the 4 GB ram installed with just the monitor window open. I tried looking at the process list to see what the problem might be, but I have limited knowledge on reading it. I did see a process named "rtkid-daemon" running in addition to all the other processes.. I could not remember how to open the Sys Logfile, so I don't have a way to show the problem.
Another thing I saw while trying to see the problem was that the network is configured with a "loopback" interface, instead of "eth0"
My system is connected by wired DSL at a 5 to 7 mb download speed.

So, this is about the best I can explain my problem. If anyone has a solution I will appreciate the help.
The system is an older AMD quad-core 9450 black edition, with 4 GB ram large HDD

Thanks.

---

### Post by Impavidus on 2014-01-06
Find out which processes use most memory. You can use the system monitor, but it has a somewhat strange way of sorting its output. You can also open a terminal and run **top**. Hit > to sort according to memory usage and see which processes use most. Use q to close. An easy way is to run **top -b -n1** and simply past the output here (in [code] tags).

Don't worry about the network, I don't think the problem is there.

---

### Post by Gnusboy on 2014-01-06
Impavidus'

Here is the file you asked for.AS I said before, I don't know how to read this data, so any help will be appreciated. Thanks.

 ```
jess@Ranha:~$ top -b -n1
top - 09:19:08 up 48 min,  2 users,  load average: 0.42, 0.32, 0.24
Tasks: 173 total,   1 running, 172 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  1.0%sy,  0.2%ni, 95.2%id,  1.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3791532k total,  2186604k used,  1604928k free,   326560k buffers
Swap:  5261252k total,        0k used,  5261252k free,   722092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1015 root      20   0  224m  80m  15m S    6  2.2   1:12.79 Xorg               
 2978 jess      20   0  737m  63m  41m S    6  1.7   0:17.35 ksysguard          
 3025 jess      20   0 17336 1268  896 R    2  0.0   0:00.02 top                
    1 root      20   0 24468 2376 1268 S    0  0.1   0:00.79 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.09 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   15 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/2        
   16 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   19 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/3        
   20 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs          
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:1        
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers        
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   28 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd        
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd            
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff            
   31 root      20   0     0    0    0 S    0  0.0   0:00.02 khubd              
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                 
   33 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd         
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0            
   35 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd               
   36 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged         
   37 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark      
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea    
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto             
   47 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld           
   48 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
   50 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
   51 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3          
   53 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:3        
   78 root       0 -20     0    0    0 S    0  0.0   0:00.00 devfreq_wq         
  178 root       0 -20     0    0    0 S    0  0.0   0:00.00 firewire           
  224 root      20   0     0    0    0 S    0  0.0   0:00.02 scsi_eh_4          
  225 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5          
  244 root      20   0     0    0    0 S    0  0.0   0:00.09 jbd2/sda6-8        
  245 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit    
  335 root      20   0 17236  640  440 S    0  0.0   0:00.06 upstart-udev-br    
  337 root      20   0 21888 1660  780 S    0  0.0   0:00.05 udevd              
  434 root      20   0 21868 1192  320 S    0  0.0   0:00.00 udevd              
  435 root      20   0 21884 1224  336 S    0  0.0   0:00.00 udevd              
  539 root      20   0 15192  392  192 S    0  0.0   0:00.00 upstart-socket-    
  661 root       0 -20     0    0    0 S    0  0.0   0:00.00 edac-poller        
  662 root       0 -20     0    0    0 S    0  0.0   0:00.00 ttm_swap           
  676 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused          
  760 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0          
  787 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1          
  788 messageb  20   0 25108 2220  784 S    0  0.1   0:00.44 dbus-daemon        
  813 root      20   0 79044 3128 2328 S    0  0.1   0:00.02 modem-manager      
  815 root      20   0 21192 1680 1400 S    0  0.0   0:00.00 bluetoothd         
  824 root      20   0  232m 5216 4088 S    0  0.1   0:00.12 NetworkManager     
  825 syslog    20   0  243m 1420 1096 S    0  0.0   0:00.05 rsyslogd           
  830 avahi     20   0 32312 1692 1388 S    0  0.0   0:00.01 avahi-daemon       
  831 avahi     20   0 32184  468  216 S    0  0.0   0:00.00 avahi-daemon       
  833 root      20   0  191m 4172 2888 S    0  0.1   0:00.35 polkitd            
  853 root      20   0  102m 4684 3184 S    0  0.1   0:00.06 cupsd              
  860 colord    20   0  488m  11m 8808 S    0  0.3   0:00.14 colord             
  887 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd           
  927 root      20   0 19988  956  792 S    0  0.0   0:00.00 getty              
  935 root      20   0 19988  956  792 S    0  0.0   0:00.00 getty              
  944 root      20   0 19988  956  792 S    0  0.0   0:00.00 getty              
  947 root      20   0 19988  960  792 S    0  0.0   0:00.00 getty              
  953 root      20   0 19988  952  792 S    0  0.0   0:00.00 getty              
  969 root      20   0  4464  812  552 S    0  0.0   0:00.00 acpid              
  975 whoopsie  20   0  197m 5012 3664 S    0  0.1   0:00.02 whoopsie           
  977 root      20   0  264m 3456 2776 S    0  0.1   0:00.03 lightdm            
  982 root      20   0 19116  996  768 S    0  0.0   0:00.00 cron               
  983 daemon    20   0 16912  376  216 S    0  0.0   0:00.00 atd                
  984 root      20   0 15984  676  500 S    0  0.0   0:00.42 irqbalance         
 1155 root      20   0 19988  960  792 S    0  0.0   0:00.00 getty              
 1163 root      20   0  118m 3652 3000 S    0  0.1   0:00.06 accounts-daemon    
 1180 root      20   0 2042m 3744 2716 S    0  0.1   0:00.09 console-kit-dae    
 1294 root      20   0  214m 4280 3312 S    0  0.1   0:00.15 upowerd            
 1446 root      20   0  153m 3472 2760 S    0  0.1   0:00.03 lightdm            
 1493 rtkit     21   1  164m 1280 1052 S    0  0.0   0:00.02 rtkit-daemon       
 1510 root      20   0  7268 1500 1004 S    0  0.0   0:00.00 dhclient           
 1520 nobody    20   0 33024 1456 1204 S    0  0.0   0:00.08 dnsmasq            
 1640 root      20   0     0    0    0 S    0  0.0   0:00.07 flush-8:0          
 1688 root      20   0     0    0    0 S    0  0.0   0:16.80 kworker/0:2        
 1722 jess      20   0  360m 4456 2976 S    0  0.1   0:00.07 gnome-keyring-d    
 1733 jess      20   0  383m 9.8m 7328 S    0  0.3   0:00.31 gnome-session      
 1768 jess      20   0 12572  320    0 S    0  0.0   0:00.00 ssh-agent          
 1771 jess      20   0 26564  532  260 S    0  0.0   0:00.00 dbus-launch        
 1772 jess      20   0 27660 3216  580 S    0  0.1   0:02.04 dbus-daemon        
 1781 jess      20   0  665m  18m  12m S    0  0.5   0:01.38 gnome-settings-    
 1791 jess      20   0 52384 2396 1992 S    0  0.1   0:00.03 gvfsd              
 1793 jess      20   0  267m 2788 2244 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 1802 jess      20   0 1197m  91m  42m S    0  2.5   0:44.35 compiz             
 1810 jess      20   0 57836 3448 1948 S    0  0.1   0:00.14 gconfd-2           
 1816 jess       9 -11  426m 5832 3740 S    0  0.2   0:00.15 pulseaudio         
 1819 jess      20   0 46600 2604 1700 S    0  0.1   0:00.01 gvfsd-metadata     
 1822 jess      20   0 95960 2980 2292 S    0  0.1   0:00.00 gconf-helper       
 1824 jess      20   0  470m  10m 7792 S    0  0.3   0:00.14 bluetooth-apple    
 1825 jess      20   0 1322m  32m  17m S    0  0.9   0:02.20 nautilus           
 1826 jess      20   0  442m 8960 6584 S    0  0.2   0:00.10 gnome-fallback-    
 1829 jess      20   0  596m  14m  10m S    0  0.4   0:00.22 nm-applet          
 1831 jess      20   0  298m 8700 6444 S    0  0.2   0:00.10 polkit-gnome-au    
 1838 jess      20   0  212m 4036 3152 S    0  0.1   0:00.05 gvfs-gdu-volume    
 1842 root      20   0  188m 3844 2992 S    0  0.1   0:00.16 udisks-daemon      
 1845 root      20   0 45520  800  448 S    0  0.0   0:00.00 udisks-daemon      
 1849 jess      20   0 60340 2436 1872 S    0  0.1   0:00.00 gvfs-gphoto2-vo    
 1852 jess      20   0  138m 2512 2016 S    0  0.1   0:00.00 gvfs-afc-volume    
 1860 jess      20   0 57060 3300 2660 S    0  0.1   0:00.01 gvfsd-trash        
 1862 jess      20   0 52544 2556 2136 S    0  0.1   0:00.00 gvfsd-burn         
 1870 jess      20   0  382m  10m 7508 S    0  0.3   0:01.77 bamfdaemon         
 1889 jess      20   0  4404  588  488 S    0  0.0   0:00.00 sh                 
 1890 jess      20   0  310m  11m 8212 S    0  0.3   0:01.14 gtk-window-deco    
 1893 jess      20   0  577m  20m  11m S    0  0.6   0:02.15 unity-panel-ser    
 1895 jess      20   0  421m 6752 3344 S    0  0.2   0:00.42 hud-service        
 1911 jess      20   0  412m  10m 7576 S    0  0.3   0:00.08 indicator-print    
 1913 jess      20   0  517m 6868 5316 S    0  0.2   0:00.12 indicator-sound    
 1915 jess      20   0  588m 6012 4664 S    0  0.2   0:00.06 indicator-sessi    
 1916 jess      20   0  411m 4944 3888 S    0  0.1   0:00.07 indicator-appli    
 1925 jess      20   0  503m 6340 4740 S    0  0.2   0:00.13 indicator-messa    
 1927 jess      20   0  544m 7336 5704 S    0  0.2   0:00.04 indicator-datet    
 1957 jess      20   0 47864 2660 2212 S    0  0.1   0:00.02 geoclue-master     
 1959 jess      20   0  325m 6480 5208 S    0  0.2   0:00.04 ubuntu-geoip-pr    
 1968 jess      20   0  322m 9384 6928 S    0  0.2   0:00.12 gdu-notificatio    
 1971 jess      20   0  417m  10m 8408 S    0  0.3   0:00.11 telepathy-indic    
 1978 jess      20   0  313m 6276 5004 S    0  0.2   0:00.07 mission-control    
 1983 jess      20   0  390m  13m  10m S    0  0.4   0:00.04 goa-daemon         
 1994 jess      20   0  407m  11m 8108 S    0  0.3   0:00.57 unity-applicati    
 1996 jess      20   0  600m 6868 5324 S    0  0.2   0:00.17 unity-files-dae    
 1998 jess      20   0  722m  10m 6428 S    0  0.3   0:00.42 unity-music-dae    
 2000 jess      20   0  502m  16m 7812 S    0  0.4   0:00.39 unity-lens-vide    
 2018 jess      20   0  331m 4168 3072 S    0  0.1   0:00.22 zeitgeist-daemo    
 2027 jess      20   0 1218m 340m  49m S    0  9.2   2:28.35 firefox            
 2033 jess      20   0  230m 6408 4684 S    0  0.2   0:00.10 zeitgeist-fts      
 2035 jess      20   0  408m 6296 4492 S    0  0.2   0:00.15 zeitgeist-datah    
 2037 jess      20   0 11384  352  276 S    0  0.0   0:00.00 cat                
 2042 jess      20   0  301m 9048 6712 S    0  0.2   0:00.13 gnome-screensav    
 2060 jess      20   0  572m 4316 3504 S    0  0.1   0:00.06 unity-musicstor    
 2088 jess      20   0  267m 3064 2544 S    0  0.1   0:00.00 at-spi-bus-laun    
 2096 jess      20   0  546m  20m 9424 S    0  0.6   0:00.47 unity-scope-vid    
 2162 jess      20   0  473m  38m 8280 S    0  1.0   0:01.37 ubuntuone-syncd    
 2206 jess      20   0  395m  12m 9680 S    0  0.3   0:00.35 update-notifier    
 2261 jess      20   0  282m 3864 3140 S    0  0.1   0:00.03 deja-dup-monito    
 2274 root      20   0     0    0    0 S    0  0.0   0:00.00 jbd2/sda1-8        
 2275 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit    
 2386 jess      20   0 1161m  32m  22m S    0  0.9   0:03.18 gnome-control-c    
 2394 jess      20   0  121m  20m 5496 S    0  0.5   0:00.26 ubuntuone-login    
 2515 root      20   0     0    0    0 S    0  0.0   0:00.20 kworker/3:2        
 2519 jess      20   0  256m 2696 2052 S    0  0.1   0:00.00 dconf-service      
 2584 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/2:1        
 2675 root      20   0 95404  11m 5408 S    0  0.3   0:00.11 system-service-    
 2796 lp        20   0 52148 1696 1300 S    0  0.0   0:00.00 dbus               
 2873 root      20   0     0    0    0 S    0  0.0   0:00.06 kworker/1:0        
 2874 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/3:0        
 2879 jess      20   0  558m  15m  10m S    0  0.4   0:00.45 gnome-terminal     
 2886 jess      20   0 14792  804  644 S    0  0.0   0:00.00 gnome-pty-helpe    
 2887 jess      20   0 27296 4264 1628 S    0  0.1   0:00.19 bash               
 2946 root      20   0     0    0    0 S    0  0.0   0:00.11 kworker/2:2        
 2960 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/3:1        
 2967 root      20   0     0    0    0 S    0  0.0   0:00.12 kworker/1:2        
 2973 root      20   0     0    0    0 S    0  0.0   0:02.79 kworker/0:0        
 2975 root      20   0     0    0    0 S    0  0.0   0:00.07 kworker/2:0        
 2985 jess      20   0  9988 1284  844 S    0  0.0   0:00.77 ksysguardd         
 2991 jess      20   0  154m 6772 4652 S    0  0.2   0:00.05 kdeinit4           
 2994 jess      20   0  187m 9360 7184 S    0  0.2   0:00.02 klauncher          
 2996 jess      20   0  553m  20m  14m S    0  0.6   0:00.26 kded4              
 3006 root      20   0     0    0    0 S    0  0.0   0:00.02 kworker/1:1        
 3020 root      20   0     0    0    0 S    0  0.0   0:01.18 kworker/0:1
```

---

### Post by ghicksrn on 2014-01-06
I could be wrong, but I don't think memory would cause that problem. Linux uses RAM a lot different than Windows. Full RAM is not usually a problem with Linux systems. When you get that grayed, dim screen, it is usually an excessive load on CPU. Using the command ```
top
``` will sort programs by CPU usage and you can determine which process is using all the CPU. That will be the process on top of the list. Using the ```
kill *PID*
``` command with *PID* replaced by the actual number from top, will stop that process. Whatever that process did will then be stopped. If it is something you needed, it will not be working anymore until restarted.

---

### Post by Impavidus on 2014-01-06
Was this when you had a problem or when everything was still OK? Because your CPU load is low and whilst your memory usage is quite high (especially by Firefox), it's not so high that it would cause problems. Else, run top when your system is slow. It reports both memory and CPU usage, so in either case we would get useful information. Killing the offending process is the quick and *dirty* solution. Any unsaved information in the killed program may be lost. Best to find out why it's slowing your computer down.

How many tabs have you open in Firefox?

---

### Post by king.of.random on 2014-01-06
Have you checked your pc for dust? This can seriously affect performance over time. In fact over the Christmas holidays my daughter brought her laptop over complaining of the slowness and how hot it got. A quick blow with a compressed air can cleared a huge amount of gunk and now it runs like new. It is always an idea to pay special attention around the cpu and any graphics card.

---

### Post by Gnusboy on 2014-01-08
Good ideas all. I'll start working through the problem when I have more time and will back to you.
Thanks

---

