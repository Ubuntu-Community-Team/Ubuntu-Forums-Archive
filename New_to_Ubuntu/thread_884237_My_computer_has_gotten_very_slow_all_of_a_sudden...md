---
title: "My computer has gotten very slow all of a sudden..."
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-08-08
- topic -

What do I do to fix this??

---

### Post by LowSky on 2008-08-08
maybe a little more explanation..

in terminal type top and post it here

---

### Post by Bigbob22 on 2008-08-08
```

top - 19:02:05 up  4:25,  2 users,  load average: 3.12, 3.11, 2.60
Tasks: 132 total,   2 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.3%us, 62.6%sy,  0.0%ni, 14.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1034184k total,   983024k used,    51160k free,    19208k buffers
Swap:  3028212k total,    33888k used,  2994324k free,   321020k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1491 root      15  -5     0    0    0 R  100  0.0  26:00.55 khubd              
 5644 root      20   0  263m 101m  22m S   32 10.1  22:07.11 Xorg               
 6124 sanat     20   0 28572  20m 6952 S   31  2.1  27:31.41 compiz.real        
16657 sanat     20   0  298m  97m  26m S    5  9.7   1:12.09 firefox            
17588 sanat     20   0 74520  21m  11m S    1  2.1   0:01.30 gnome-terminal     
17621 sanat     20   0  2308 1124  852 R    1  0.1   0:00.20 top                
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.16 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.54 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.72 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper              


```

---

### Post by scotcella on 2008-08-08
Seems like khubd is eating up your CPU- running at 100% judging by your output.

I have no idea what that would be, but what applications are you running? That might be the culprit.

---

### Post by Bigbob22 on 2008-08-08
I figured it out. It was the screenlets that i had up. I never used them anyway so i took them off using sessions under preferences and uninstalled screenlets.

---

### Post by sharks on 2008-08-08
use basic theme,dont use docks and dont use compiz

---

### Post by pparks1 on 2008-08-08
Thanks for letting us know what it was.  It's funny, because while I often screw around trying to get the eye candy stuff to work, in the end, it often kills performance and thus I turn them off.   I don't even know why I bother trying to get it working :)

---

### Post by Crafty Kisses on 2008-08-08
> **Bigbob22 said:**
> - topic -

What do I do to fix this??

I'd also like to know your system specs.

---

### Post by scotcella on 2008-08-08
> I figured it out. It was the screenlets that i had up. I never used them anyway so i took them off using sessions under preferences and uninstalled screenlets.

> **pparks1 said:**
> Thanks for letting us know what it was.  It's funny, because while I often screw around trying to get the eye candy stuff to work, in the end, it often kills performance and thus I turn them off.   I don't even know why I bother trying to get it working :)

I am the same as well..  I tried Cairo dock a while back and it ate up both my CPU's at 100%.

Compiz for me is fine but Cairo is not..

:)

Only way to learn is to try I guess :guitar:

Oh and don't forget to mark your thread as solved...

---

