---
title: "lxde slower than KDE?"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Shmook on 2011-09-19
My comp's somewhat old (P4 2.5Ghz, 1.5G RAM) so I've been trying out appropriate desktop environments and have long been a fan of xfce. I decided to try lxde as it's supposedly less resource-demanding. Oh let me also say that GNOME and KDE run fine, but after playing with Puppy linux and enjoying Openbox I'm experimenting with these more stripped-down DE's. 

My trouble is that lxde seems to be having trouble -- while simultaneously watching a youtube vid (using firefox) and running the Ubuntu Software Center EVERYTHING clogs down. Switching desktops or programs takes a few seconds and the video on firefox is super-choppy. Now I'm doing the same activities using KDE (to my knowledge the most resource-heavy DE out there) and it's all going much smoother. :confused:

Has anyone else run into this? Do certain programs simply not react well under lxde? I'm still happy with xfce but would like to play with lxde.

ALSO on a totally unrelated topic: is GNUstep worth learning how to use? I've attempted it a few times and given up very quickly LOL -- thanks in advance

---

### Post by MG&amp;TL on 2011-09-19
If you use "system monitor" you can see whether it's the RAM or cpu that is running out.

Also run 

```
top
```

in a terminal, and you can see what's being the hog.

Although if your computer can run KDE, it's maybe not worth it?

---

### Post by Shmook on 2011-09-19
^sure, just the super-nerd in me needs to understand what's going on here; plus the spartan appearance of DE's like lxde openbox & icewm have for some reason become appealing to me. Thanks for the tips though :)

---

### Post by MG&amp;TL on 2011-09-19
Sorry, that wasn't what I meant...:)

could you post the results of *top* here, that way we can see what is making lxde run so slow.

---

### Post by Shmook on 2011-09-19
Sorry for the wait had to reenact the situation before:

```
top - 03:04:34 up  4:47,  2 users,  load average: 2.04, 1.42, 0.97
Tasks: 115 total,   2 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 81.9%us, 18.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1542848k total,  1267856k used,   274992k free,   146924k buffers
Swap:   931764k total,      232k used,   931532k free,   744948k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
 7230 root      20   0 92640  66m 9764 R 68.5  4.4   0:19.35 update-apt-xapi     
 7124 eric      20   0  234m  62m  36m S 10.9  4.2   0:38.19 software-center     
 6865 root      20   0  267m  19m 7528 S  9.2  1.3   0:11.49 Xorg                
 7168 eric      20   0  143m  13m  10m S  8.6  0.9   0:02.68 lxterminal          
 6997 eric      20   0  7016 2496 1760 S  0.7  0.2   0:00.60 xscreensaver        
 7005 eric      20   0  7016 2492 1760 S  0.7  0.2   0:00.43 xscreensaver        
 6311 root      20   0     0    0    0 S  0.3  0.0   0:01.88 kworker/0:1         
 7100 eric      20   0  467m 124m  31m S  0.3  8.2   0:31.29 firefox-bin         
 7225 eric      20   0  2624 1108  848 R  0.3  0.1   0:00.45 top                 
    1 root      20   0  3056 1740 1232 S  0.0  0.1   0:01.48 init                
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd            
    3 root      20   0     0    0    0 S  0.0  0.0   0:03.36 ksoftirqd/0         
    5 root      20   0     0    0    0 S  0.0  0.0   0:01.47 kworker/u:0         
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0         
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset              
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper             
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns               
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.08 sync_supers         
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default         
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd     
```

---

### Post by Shmook on 2011-09-19
Here's another -- this one with a youtube vid running:
```
top - 03:18:29 up  5:01,  2 users,  load average: 3.41, 3.69, 2.63
Tasks: 115 total,   3 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s): 89.4%us, 10.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1542848k total,  1328496k used,   214352k free,   149448k buffers
Swap:   931764k total,      232k used,   931532k free,   792644k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 7227 eric      20   0  207m  45m  19m S 29.6  3.0   3:02.57 plugin-containe   
 7562 eric      20   0  210m  39m  18m R 18.8  2.6   0:06.26 software-center   
 7569 eric      20   0 68812  41m   9m R 18.8  2.8   0:02.56 update-software   
 6865 root      20   0  269m  21m 8476 S  9.5  1.4   1:03.65 Xorg              
 7100 eric      20   0  506m 133m  32m S  8.9  8.8   2:42.71 firefox-bin       
 5894 eric       9 -11  165m 5520 4108 S  7.6  0.4   3:38.71 pulseaudio        
 7004 eric      20   0  245m  17m  13m S  3.0  1.2   0:12.15 lxpanel           
 7489 eric      20   0  142m  13m  10m S  1.6  0.9   0:01.58 lxterminal        
 6997 eric      20   0  7016 2496 1760 S  1.0  0.2   0:03.23 xscreensaver      
 7005 eric      20   0  7016 2492 1760 S  0.7  0.2   0:02.29 xscreensaver      
 7547 eric      20   0  2628 1112  848 R  0.7  0.1   0:01.14 top               
    1 root      20   0  3056 1740 1232 S  0.0  0.1   0:01.48 init              
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S  0.0  0.0   0:03.53 ksoftirqd/0       
    5 root      20   0     0    0    0 S  0.0  0.0   0:01.47 kworker/u:0       
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0      
```

---

### Post by Lisiano on 2011-09-19
update-apt-xapi is actually apt-xapian-index - maintenance and search tools for a Xapian index of Debian packages
Next one looks to me like it is just updating and "plugin-container" which I'm assuming is Flash related is using a bit too much CPU. 
But I wonder. Why do you have 2 screensavers running?

---

### Post by Shmook on 2011-09-20
...great question^ I generally disable all screensavers anyway so...funk if I know; I'll look into it thanks

---

### Post by Shmook on 2011-09-22
BUMP one more thought/question; is there ANYTHING outside of the results of *top* that would affect the speed of a desktop env.? 

And also -- any opinions on GNUstep? still curious. thanks

---

### Post by Lisiano on 2011-09-22
```
iotop
```
I once had a java app that went rogue with I/O blocking. Never knew it until I ran iotop.

As for gnustep, I don't use it nor heard of it (Scripting and network security, not programming) but you could try googling for "gnustep alternative" or the likes.

---

### Post by amjjawad on 2011-09-22
Don't want to be rude but LXDE is slower than KDE? you gave me a heart attack, do you know that? :D

With Firefox 6.0.2 and Chromium (latest) opened with tons of active tabs ... my RAM Usage wouldn't even reach 400MB on Lubuntu 11.04.

NO WAY LXDE could be slower unless there is something massively wrong.

---

### Post by gnuskool on 2012-01-06
I too have been 'regressing' in terms of pc hardware and have got lubuntu on an HP Thinkpad 1GHz, 256MB RAM.
I watch youtube with the update manager working fine -not great admittedly - especially multitasking during that time, but certainly not choppy video.
Recently I've become interested in seeing how little resources can a usable system use and have also tried puppy and DSL with awesome results.

---

