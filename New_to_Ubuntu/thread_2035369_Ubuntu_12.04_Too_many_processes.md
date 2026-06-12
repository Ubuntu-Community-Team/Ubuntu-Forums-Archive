---
title: "Ubuntu 12.04 Too many processes ?"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by easysid on 2012-07-30
Hi, 
I installed Precise on my laptop a few days ago. A thing that caught my attentions was the number of processes and the amount of ram being used when the desktop first appears. 


```

$ ps -e | grep -c '^'
170

$ free -m

     total       used       free     shared    buffers     cached
Mem:  2929      1316        1612          0      119        635

-/+ buffers/cache:562       2367

Swap:  1997          0       1997

```

Is this normal? 170 processes and 1.3 G Ram . I am not new to Linux, but I have been out of touch for past year or so. I noticed this only because I am new to Unity. 

Thanx.


Sony vaio - intel i3 - 3 GB Ram - ATI Radeon HD 5470 - Ubuntu 12.04

---

### Post by Frogs Hair on 2012-07-30
I haven't checked 12.04 since installing , but I have 157 on Unity 2D with opera running . If you want to see resource use for top processes use the following. ```
top
```

---

### Post by richpri on 2012-07-30
I am running 12.04 with Gnome-Fallback and this is what I get:

```
rich@rich2:~$ ps -e | grep -c '^'
151
rich@rich2:~$ top

top - 13:19:21 up  6:11,  1 user,  load average: 0.08, 0.21, 0.33
Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.7%sy,  0.0%ni, 97.7%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1802256k total,  1123888k used,   678368k free,   138276k buffers
Swap:  6141948k total,   141544k used,  6000404k free,   665748k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1949 rich      20   0 68120 5600 2768 S  0.3  0.3   1:06.93 compiz             
 3222 root      20   0     0    0    0 S  0.3  0.0   0:01.50 kworker/0:3        
 4502 rich      20   0  145m  14m  10m S  0.3  0.8   0:00.70 gnome-terminal     
 4569 rich      20   0  2836 1136  860 R  0.3  0.1   0:00.38 top                
    1 root      20   0  3640 1172  592 S  0.0  0.1   0:01.26 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:01.69 ksoftirqd/0        
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.47 kworker/u:0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.08 watchdog/0         
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper            
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs          
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns              
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.04 sync_supers        
rich@rich2:~$ 

```

I am wondering what compiz is.

---

### Post by lukeiamyourfather on 2012-07-30
> **easysid said:**
> 
Is this normal? 170 processes and 1.3 G Ram . I am not new to Linux, but I have been out of touch for past year or so. I noticed this only because I am new to Unity. 

That sounds about right if you include the cache. Ubuntu 12.04 LTS is pretty heavy, as are many other modern interfaces like KDE and GNOME. If you want something lighter try Xubuntu or Lubuntu.

---

### Post by Sandertje on 2012-07-30
> **richpri said:**
> I am running 12.04 with Gnome-Fallback and this is what I get:



I am wondering what compiz is.

Compiz is a windowing manager that Unity uses. It's supposed to be there ;-)

---

### Post by easysid on 2012-07-31
Regarding processes, there's isn't any difference in Unity/Unity 2d. Its same ~170. 

> **lukeiamyourfather said:**
> That sounds about right if you include the cache. Ubuntu 12.04 LTS is pretty heavy, as are many other modern interfaces like KDE and GNOME. If you want something lighter try Xubuntu or Lubuntu.

Ok. That settles it then. I just needed to clear it. If its normal than its alright. 
AFAIK xfce isn't light anymore. I used to run it over my LFS install and it was fine then. But I am not so sure about recent developments ( whatever one learns from blogs etc. :P )

Thanx for the responses. I'll mark this as solved.

---

### Post by lukeiamyourfather on 2012-07-31
> **easysid said:**
> 
AFAIK xfce isn't light anymore. 

Xfce isn't as light as it used to be but still light compared to Unity (default in Ubuntu now).

[http://mylinuxexplore.blogspot.com/2012/04/ubuntu-distros-ram-cpu-usage-of-ubuntu.html](http://mylinuxexplore.blogspot.com/2012/04/ubuntu-distros-ram-cpu-usage-of-ubuntu.html)

---

### Post by Cheesemill on 2012-07-31
From your 'free -m' output you are only using 562MB not 1316MB.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by easysid on 2012-08-05
> **Cheesemill said:**
> From your 'free -m' output you are only using 562MB not 1316MB.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

duh .. :oops: ..... thanks for clearing that. Had no idea.

---

