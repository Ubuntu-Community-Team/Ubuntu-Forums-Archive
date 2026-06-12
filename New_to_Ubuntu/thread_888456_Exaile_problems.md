---
title: "Exaile problems"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-08-13
So I got tired of Rhythmbox and gave Exaile a try. The player is very nice and have most of the things I want from a player. But after a few minutes running time Exaile pushes my processor to almost 100%. Seems that there is some issues with Python (not sure I spelled that right) running above 80% even though the system monitor says it's sleeping. Can anyone provide a solution for this so I can continue using Exaile?

---

### Post by Crafty Kisses on 2008-08-13
Not sure if there is a fix for this, but I know a lot of people are having similar problems just like you, have a look at this link > [https://bugs.launchpad.net/exaile/+bug/162226](https://bugs.launchpad.net/exaile/+bug/162226)

That looks like it was from 2007, but I'm not sure if anyone has fixed this or there is a workaround, post the following output:
```
top
```
There could be a couple of things wrong.

---

### Post by peakshysteria on 2008-08-13
Thanks for the link man. It looks like there might be some issues with the automatic rescanning of the library. Default the scanning is set to scan every 25 minute. I'll post back as soon as I have been able to recreate the problem.

Seems strange that this bug which more than me have problems with isn't rated as critical.

---

### Post by Crafty Kisses on 2008-08-13
> **peakshysteria said:**
> Thanks for the link man. It looks like there might be some issues with the automatic rescanning of the library. Default the scanning is set to scan every 25 minute. I'll post back as soon as I have been able to recreate the problem.

Seems strange that this bug which more than me have problems with isn't rated as critical.

Yeah, I remember I had some issues with Exaile kind of similar to these back when I used to use Dapper, but I haven't experienced any problems thus far, but I guess it's a problem for a lot of people.

---

### Post by peakshysteria on 2008-08-13
Every 25 minutes CPU spikes:

top - **11:50:02** up 1 day, 21:27,  2 users,  load average: 1.21, 0.85, 0.59
Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 82.3%us, 17.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3097452k total,  3015468k used,    81984k free,   330932k buffers
Swap:  7960168k total,    41868k used,  7918300k free,  1724396k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17562 peaks     20   0  756m 276m  24m S **88.9  9.1   2:53.57 python**             
 6064 peaks     20   0  146m 6656 3780 S  5.7  0.2  17:56.33 pulseaudio         
 5769 root      20   0  156m  68m  11m S  1.3  2.3  43:51.24 Xorg               
17691 peaks     20   0  535m 111m  27m S  1.3  3.7   0:31.47 firefox            
 4371 root      20   0 22892 7804  644 S  1.0  0.3   2:17.16 mount.ntfs-3g      
 8314 peaks     20   0  493m  55m  19m S  1.0  1.8  29:17.00 deluge             
17617 peaks     20   0  260m  24m  11m R  0.7  0.8   0:01.36 gnome-terminal     
    1 root      20   0  4020  876  592 S  0.0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.64 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.30 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.92 kblockd/0          
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       


top - **12:15:32** up 1 day, 21:53,  2 users,  load average: 1.66, 1.01, 0.65
Tasks: 130 total,   2 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s): 34.9%us,  5.3%sy,  0.0%ni, 59.5%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3097452k total,  3052016k used,    45436k free,   366492k buffers
Swap:  7960168k total,    41868k used,  7918300k free,  1668084k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17562 peaks     20   0  764m 284m  24m S **99.9  9.4   5:45.25 python**             
 6064 peaks     20   0  146m 6668 3792 S  4.3  0.2  19:10.27 pulseaudio         
 5769 root      20   0  157m  68m  12m S  2.0  2.3  44:57.06 Xorg               
 4371 root      20   0 22892 7804  644 S  1.7  0.3   2:25.06 mount.ntfs-3g      
 8314 peaks     20   0  493m  55m  19m S  1.3  1.8  29:36.83 deluge             
17638 peaks     20   0 18992 1272  932 R  0.7  0.0   0:06.16 top                
17691 peaks     20   0  569m 136m  27m S  0.7  4.5   2:22.57 firefox            
    1 root      20   0  4020  876  592 S  0.0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.66 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.32 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.92 kblockd/0          
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       


So it looks like it's related to the library scanning. What's the difference of Collection and Files. And those it really mather if I set library scanning to 0 (to disable the function)? If my music folder is updated all files are visible if I choose the files three anyway. Or am I wrong?

---

### Post by metasolaris on 2008-08-13
Amarok is the one I use in Hardy. Its supposed to be simular to Exaile and runs very nicely with my system (better than iTunes!)

---

### Post by peakshysteria on 2008-08-13
Amarok doesn't have the looks :) Rhythmbox is my default player. But I would like to change this to Exaile since there are a few issues with Rhythmbox. It seems to constantly list the songs from folders wrong. It lists them as records/folders but in the wrong sequel. Anyways, Exaile is all I need. Looking forward to this Python/library scanning issue is fixed. And really looking forward to people making new themes for it. It would be nice to see the same possibilities with themes as Foobar2000 on windows have (the only thing I miss about windows).

---

