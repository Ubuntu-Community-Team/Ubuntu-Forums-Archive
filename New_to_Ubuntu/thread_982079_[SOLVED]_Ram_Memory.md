---
title: "[SOLVED] Ram Memory"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by JuanIgnacioT on 2008-11-14
Hey everyone!!! well Im really new at this and ive been interested in ubuntu since i heard of it. Im using xubuntu right know and ive noticed that even when im not doing something, ram monitor is still showing me 296mb out of 1G being used. is that normal? is there a way to use less or cleaning the memory? ive got no idea about it.. plz help out a lil bit. thanx in advance... by the way, my laptop is an inspiron 1420 if it makes a difference. thanx...

---

### Post by mjwhitfield on 2008-11-14
unused RAM is wasted RAM.

---

### Post by lswest on 2008-11-14
> **JuanIgnacioT said:**
> Hey everyone!!! well Im really new at this and ive been interested in ubuntu since i heard of it. Im using xubuntu right know and ive noticed that even when im not doing something, ram monitor is still showing me 296mb out of 1G being used. is that normal? is there a way to use less or cleaning the memory? ive got no idea about it.. plz help out a lil bit. thanx in advance... by the way, my laptop is an inspiron 1420 if it makes a difference. thanx...

it may seem like you're not running anything, but the window manager and some other programs (network manager or so) will still need some RAM.  It really depends what you have running at startup (bluetooth, etc.).  And really...296MB of 1GB of RAM is nothing compared to Vista's 700MB/2GB of RAM on my laptop, or XP's roughly 300-400MB.  I wouldn't worry about it.

---

### Post by oldos2er on 2008-11-14
"ram monitor is still showing me 296mb out of 1G being used. is that normal?"

 Yes.

---

### Post by JuanIgnacioT on 2008-11-14
Hey thanx a lot, I was getting worried for nothing i guess... im surprised how quick the answer was. lol! Ill keep trying things in this laptop but so far xubuntu rocks!! now regarding a ram clean up or something? any idea?

---

### Post by LowSky on 2008-11-14
open a terminal and type ```
top
```
it will tell you what applications are using up your memory, If you like post the infor here and we can tell you how to either dislbe it or if it need to run. After you type top hit ctrl+c to have the program stop running. then you will be able to copy and paste. to copy in terminla you need to use CTRL+SHIFT+C, paste CTRL+SHIFT+V

---

### Post by JuanIgnacioT on 2008-11-14
thanx,
ok, here it is... well, i guess

```
top - 13:22:15 up  1:22,  2 users,  load average: 0.02, 0.06, 0.01
Tasks: 113 total,   1 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.5%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1024000k total,   499644k used,   524356k free,    14108k buffers
Swap:  2996080k total,        0k used,  2996080k free,   193864k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5239 root      20   0  344m  20m 9144 S    1  2.0   0:35.94 Xorg               
 4648 root      15  -5     0    0    0 S    1  0.0   0:00.38 kondemand/0        
 4969 haldaemo  20   0  6260 4252 3424 S    1  0.4   0:04.06 hald               
 5098 root      20   0  3440 1064  912 S    1  0.1   0:02.12 hald-addon-stor    
 9301 juan      20   0 90300  23m  10m S    1  2.3   0:00.58 xfce4-terminal     
 9361 juan      20   0  2416 1144  884 R    1  0.1   0:00.16 top                
 9148 juan      20   0  136m  56m  20m S    0  5.6   0:09.69 firefox            
    1 root      20   0  3056 1884  564 S    0  0.2   0:02.26 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.22 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1 
```

---

### Post by anjilslaire on 2008-11-14
> **JuanIgnacioT said:**
> now regarding a ram clean up or something? any idea?

what is it you're trying to 'clean up'. 256 used from a gig is nothing. Linux isn't like Windows where you need anything extra to free ram up...

---

### Post by LowSky on 2008-11-14
Juan from what I see everything that is running is ok. firefox is causing a good spike but that's normal. If Firefox seems to be running slow, google: **Firefox hacks**. It will show you some things you can do to speed up the browser.

---

### Post by bodhi.zazen on 2008-11-14
Linux is not windows, they handle ram much differently.

See these links for additional information :

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

    [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by JuanIgnacioT on 2008-11-14
Thanx everyone for everything, it has been of great help for me and hopefully for many beguiners that have just migrated from "the man" lol. i will be trying to help the community as much as you all did with me (as soon as i become fully capable of doing so, of course!) thanx again, xubuntu rules!

---

