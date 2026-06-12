---
title: "Rythmbox and other music player make laptop slow"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by kapi on 2012-07-12
I can songs through vlc and audacious fine. Infact as we speak I have Glen Miller playing no problem using audacious but I have been able to use rythmbox, clementine, banshee, amarok or any other media player. 

They all do the same thing. I select a song, it plays for about twenty seconds, then the screen goes dark and faded and everything freeze. Ultimately I end up having to re boot.

Any ideas?

---

### Post by cbennett926 on 2012-07-12
> **kapi said:**
> I can songs through vlc and audacious fine. Infact as we speak I have Glen Miller playing no problem using audacious but I have been able to use rythmbox, clementine, banshee, amarok or any other media player. 

They all do the same thing. I select a song, it plays for about twenty seconds, then the screen goes dark and faded and everything freeze. Ultimately I end up having to re boot.

Any ideas?


Shot in the dark here, but have you installed the restricted-extras?

```

sudo apt-get install ubuntu-restricted-extras


```

---

### Post by irv on 2012-07-12
What is your processor? How much memory do you have? Do you have a swap setup? There are a lot of things that could cause this. If you can give more information someone might be able to help. You can also run this at the command line to see some good information on what is happening. Then post the output. 
Just type in a terminal:
```
top
```
[ATTACH]221136[/ATTACH]

---

### Post by kapi on 2012-07-12
Hi Guys,

Thanks for the relpy. I have been using Ubuntu for the past four years and still loving it, never had this prob before though.

My current machine has 247GB HD and the processor is 2.2Ghz

Ram is 2GB though in system it comes up as 1.8

Cheers

---

### Post by irv on 2012-07-12
> **kapi said:**
> Hi Guys,

Thanks for the relpy. I have been using Ubuntu for the past four years and still loving it, never had this prob before though.

My current machine has 247GB HD and the processor is 2.2Ghz

Ram is 2GB though in system it comes up as 1.8

Cheers

That seem like a fast enough system, so do the Top command and see what is using up your memory or swap or CPU. This might tell you what your problem is. It could be something running in the background.

---

### Post by kapi on 2012-07-12
Top Command

Thanks again


craig@craig-Satellite-L300:~$ top

top - 23:27:58 up  3:52,  1 user,  load average: 2.41, 3.00, 1.99
Tasks: 185 total,   1 running, 184 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.6%us,  2.7%sy,  0.0%ni, 82.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1928204k total,  1734940k used,   193264k free,    89016k buffers
Swap:  1960956k total,    19256k used,  1941700k free,   621336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
  983 root      20   0 88216  23m 7288 S  4.0  1.2   5:06.71 Xorg                 
 1828 craig     20   0  302m  69m  20m S  3.7  3.7   2:48.61 compiz               
 2008 craig     20   0  426m 137m  33m S  2.3  7.3   2:28.90 chromium-browse      
 2629 craig     20   0  207m  19m  12m S  2.0  1.1   4:23.74 audacious            
 2646 craig     20   0  180m  52m  18m S  2.0  2.8   0:27.88 chromium-browse      
 1905 craig     20   0  103m  30m  10m S  1.3  1.6   0:16.19 unity-panel-ser      
 2257 craig     20   0  183m  54m  19m S  0.7  2.9   0:46.28 chromium-browse      
 2617 craig     20   0  186m  59m  20m S  0.7  3.2   0:37.53 chromium-browse      
 1801 craig     20   0  6864 3156  632 S  0.3  0.2   0:05.54 dbus-daemon          
 2253 craig     20   0  201m  64m  17m S  0.3  3.4   0:15.58 chromium-browse      
 3591 craig     20   0  172m  45m  18m S  0.3  2.4   0:46.09 chromium-browse      
 3614 craig     20   0  186m  53m  16m S  0.3  2.8   0:16.71 chromium-browse      
 3650 craig     20   0 91124  14m  10m S  0.3  0.8   0:00.54 gnome-terminal       
 3715 craig     20   0  2836 1184  880 R  0.3  0.1   0:00.13 top                  
    1 root      20   0  3640 1916 1212 S  0.0  0.1   0:00.56 init                 
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd             
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.47 ksoftirqd/0          
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0          
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.08 watchdog/0           
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset               
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs            
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.02 sync_supers          
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default          
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd

---

### Post by irv on 2012-07-12
To compare your top to mine, I am using on average 4 to 6% of my CPU you show 14.6%.
Your system memory looks to be just under 2gig, I have 4gig. You are using about ½ and so am I.
The swap is what bother me. I have mine set at 8gig you have your set at around 2gig. I am not using any swap, you are using ½. When you are using the swap, things will slow down.
With this information maybe someone could suggest some way to improve your performance. 
One thing I know that helped me was I added 2gig of memory to the 2gig I already had. I seen a real speed up. Memory has come down in price so it was a cheap way to speed things up.

---

### Post by LewisTM on 2012-07-12
Two suggestions for you (aside from adding more RAM):
1) Log into Unity 2D instead or install a lighter desktop environment (XFCE, LXDE). 
2) Install zram-config, an advanced memory manager with compression capabilities.

That should take care of performance. Whether that will ultimately solve your problem is uncertain. For a high performance music player with low overhead I would recommend you setup [MPD]("https://help.ubuntu.com/community/MPD") in combination with GMPC.

Cheers!

---

### Post by kapi on 2012-07-13
Thanks guys. I appreciate your help

---

