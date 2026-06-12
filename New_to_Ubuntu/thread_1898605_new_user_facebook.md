---
title: "new user/ facebook ?"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by Acexxxoasis on 2011-12-21
Hey guys acexxxoasis here (you can call me dave if you like) recently installed 11.1 on my inspiron 1420 and THANK UBUNTU DEV! there were 0 hiccups normally with dells drivers aren't supported etc which is a pain in the butt however this one installed and works greatunity bar is a little not to my liking but ill keep it! now here is the one thing thats bothering me a little, everything works flawlessly except for facebook in firefox it will drop to a dark screen then come up but will not allow clicking on anything is this facebook? on vista it does not do that running firefox
thank you

---

### Post by wildmanne39 on 2011-12-21
Hi, the dark screen means it is busy and it usually returns in a couple of seconds when resources are freed up, but you may be having a problem where it is using to much resources you can type this into the terminal:
```
top
```
and see what is using your resources and how much.

The next questions is how much memory and cpu do you have?

Are you playng games or just talking on face book?
Thanks

---

### Post by Acexxxoasis on 2011-12-21
I have a inspiron 1420 with the core 2 duo 1.83GHz 2Gb of ram and 160GB partitioned for UBUNTU 
it is only when I open up facebook I can have nothing else running just firefox this is what comes up
I dont understand entirely all of what I'm seeing
mainly the pid PR NI VIRT RES SHR S etc but Im assuming top is like task mgr of sorts?
[QUOTE=computer]david@linxxxoasis:~$ top

top - 21:18:41 up  4:46,  1 user,  load average: 0.34, 0.15, 0.19
Tasks: 147 total,   3 running, 144 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.8%us,  5.5%sy,  0.0%ni, 78.7%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:   2060720k total,  1271320k used,   789400k free,    88688k buffers
Swap:  2086908k total,        0k used,  2086908k free,   655812k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  943 root      20   0  125m  78m 8388 R   29  3.9  12:54.51 Xorg               
 1779 david     20   0  559m 171m  30m S    6  8.5  28:58.17 firefox            
 1617 david     20   0  227m 130m  39m S    3  6.5   5:31.86 compiz             
 2679 root      20   0     0    0    0 S    2  0.0   0:00.08 kworker/0:2        
 2578 root      20   0     0    0    0 S    2  0.0   0:01.52 kworker/1:2        
 2618 david     20   0 74004  14m  10m R    1  0.7   0:00.97 gnome-terminal     
 1621 david     20   0  3524  772  636 S    0  0.0   0:08.22 syndaemon          
 2531 root      20   0     0    0    0 S    0  0.0   0:00.60 kworker/u:1        
 2678 david     20   0  2820 1156  864 R    0  0.1   0:00.22 top                
    1 root      20   0  3328 1948 1280 S    0  0.1   0:00.78 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:01.37 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:01.16 ksoftirqd/1        
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper
[/QUOTE]

---

### Post by Acexxxoasis on 2011-12-21
I was reading I could create swap memory I did create a 2g swap but could I possibly just need a larger swap?

---

### Post by mastablasta on 2011-12-22
no it's not swap. even with no swap you should be ok with so much RAM.
 
you could try 
 
installing flash aid app 
installing sun java instead of opensource java. -- it's porbably this that is causing the issues as i remember osme pages were not running propperly untill i installed the sun java. you might need to uninstall opensoruce java first before installing sun java

---

### Post by drmrgd on 2011-12-22
> **mastablasta said:**
> no it's not swap. even with no swap you should be ok with so much RAM.
 
you could try 
 
installing flash aid app 
installing sun java instead of opensource java. -- it's porbably this that is causing the issues as i remember osme pages were not running propperly untill i installed the sun java. you might need to uninstall opensoruce java first before installing sun java

+1 to trying installing Sun Java.  FB did something recently to their site that makes pages load oddly, and I suspect it has something to do with some javascript code they have in there somewhere.  For me on Google Chrome, the system doesn't hang like yours does.  But, most of the time, I get blank pages and have to hit the reload button to actually make the content display.  I think getting the proprietary java might help you (or at least be a step in the right direction).

---

### Post by Paqman on 2011-12-22
> **drmrgd said:**
> +1 to trying installing Sun Java.  FB did something recently to their site that makes pages load oddly, and I suspect it has something to do with some javascript code they have in there somewhere.

Javascript and Java are two completely different things. You don't need any kind of Java to render pages on Facebook.

---

### Post by MartijnNL on 2011-12-22
Please be aware the the SUN java packages are empty as of the day before yesterday. Installing them from the repositories would be useless.

See here: [http://ubuntuforums.org/showthread.php?t=1897885](http://ubuntuforums.org/showthread.php?t=1897885)

You would have to install the binaries from Oracle themselves. Which is more complicated.

Try the [Flash-Aid Firefox]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") extension first.

---

### Post by drmrgd on 2011-12-22
> **Paqman said:**
> Javascript and Java are two completely different things. You don't need any kind of Java to render pages on Facebook.

Oh?  Hmmm...my mistake.  Then I'm clueless as to why FB is not running well these days. Sorry for the bad advice!

---

### Post by mastablasta on 2011-12-22
what the ....!?
 
so they remove programmes i have installed before?? moving this to the other topic....

---

### Post by wildmanne39 on 2011-12-22
Hi, from what I can tell from the top information it looks okay, so I am not sure what is going on.
Thanks

---

### Post by Acexxxoasis on 2011-12-22
wow thank you everyone Ill try the suggestions. I've been busy today building a shelf for our windows 15Tb home server. Main thing is facebook just needs to stop "fixing" things its when facebook was updating a lot. But ill try tonight :)

---

### Post by Acexxxoasis on 2011-12-22
so I tried the flash-aid
and facebook did it again everything slows and pauses and its ALWAYS facebook that does it I don't get it? That is why is one website lagging my whole computer out even terminal lags out while its running I included TOP while it was doing it (as close as I can get it) it reminds me of myspace from back in the day with all the glittery backgrounds and 10 videos trying to load at one time. I mean I look at my top numbers from what I see I still have 1.2G of Ram available and 2G of swap still so its not like a memory run out (which happened OFTEN with vista)

[QUOTE=Linxxxoasis]david@linxxxoasis:~$ top

top - 19:45:49 up 7 min,  1 user,  load average: 0.51, 0.39, 0.22
Tasks: 149 total,   2 running, 147 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.4%us,  3.3%sy,  0.0%ni, 80.3%id,  1.8%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2060720k total,   836568k used,  1224152k free,    49252k buffers
Swap:  2086908k total,        0k used,  2086908k free,   363472k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  986 root      20   0  108m  65m 8380 S   30  3.3   1:36.12 Xorg               
   66 root      20   0     0    0    0 R    2  0.0   0:00.40 kworker/0:2        
 1641 david     20   0  219m 105m  41m S    2  5.3   0:13.18 compiz             
 2163 david     20   0 74116  14m  10m S    2  0.7   0:00.68 gnome-terminal     
 1974 david     20   0  376m 100m  29m S    1  5.0   0:31.32 firefox            
 2223 david     20   0  2820 1156  864 R    1  0.1   0:00.13 top                
   22 root      20   0     0    0    0 S    0  0.0   0:01.15 kworker/1:1        
 1095 root      20   0     0    0    0 S    0  0.0   0:00.03 flush-8:0          
    1 root      20   0  3324 1948 1280 S    0  0.1   0:00.77 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.76 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.16 kworker/0:1        
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset [/QUOTE]

---

