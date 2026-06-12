---
title: "Browser issues?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-06-20
Is anyone else having browser issues with Hardy?

Firefox 3 seems to randomly close completely every now and again and Opera 9 is running a lot smoother but still somewhat slow and every now and again freezes up and it takes a few minutes before I can close it and start again. 

Known issues or just me?

---

### Post by tjwoosta on 2008-06-20
the firefox3 issue is well known here on the forums (just search firefox 3 and youl probably find a bunch of threads)

the opera 9 issue is not so well known (ive never heard of it anyway)

have you tried the new opera 9.50 ?

thats what i use and it works great for me

---

### Post by highlyevolved on 2008-06-20
Ok

I've just looked at the system monitor and CPU is at like 99% and memory is at 85%.

I'm only running Opera 9.5 and rhythm box.

I've got 512 mb of ram I can't understand why this would be happening.
XP didn't use that much CPU..

---

### Post by tjwoosta on 2008-06-20
yea that doesn't sound right

my other computer has 512mb and it usually is at like 10% to 15%

open a terminal and do ```
top
```

that should open a better system monitor and you can see what is using all the cpu and memory

---

### Post by sailor2001 on 2008-06-20
with that size ram, i'd suggest using a lighter weight browser, such as seamonkey

---

### Post by highlyevolved on 2008-06-20
topadam@adam-laptop:~$ top

top - 02:46:29 up 15 min,  2 users,  load average: 0.58, 1.19, 0.92
Tasks: 112 total,   4 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.1%us,  2.0%sy,  0.0%ni, 74.5%id,  2.7%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    507068k total,   499020k used,     8048k free,     1972k buffers
Swap:  1485972k total,    55928k used,  1430044k free,    67148k cached

5845 adam      20   0  268m  58m  16m R 74.3 11.8   1:20.96 opera              
 5134 root      20   0  420m  55m  10m S 10.6 11.3   0:14.56 Xorg               
 5918 adam      20   0 39200  19m  12m R  6.0  3.9   0:04.16 gnome-system-mo    
 5834 adam      20   0  148m  40m  20m S  5.0  8.2   0:07.24 rhythmbox          
 5508 adam      20   0 30552 6000 3528 S  1.3  1.2   0:01.78 pulseaudio         
 5591 adam      20   0 21652  13m 5832 R  1.3  2.8   0:02.80 compiz.real        
 5872 adam      39  19 58868  11m 8396 R  0.7  2.3   0:01.28 operapluginwrap    
 5984 adam      20   0 74080  20m  10m S  0.7  4.1   0:00.70 gnome-terminal     
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:01.14 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid  

Screen shot of system monitor.

[http://i30.photobucket.com/albums/c316/rough_diamonds/Screenshot-2.png](http://i30.photobucket.com/albums/c316/rough_diamonds/Screenshot-2.png)

Seems to be back to around 25-40 as I post this.

---

### Post by tjwoosta on 2008-06-20
yea ok it does look like opera is causing the problem


you probably should try using a lighter weight web browser like sailor2001 advised

---

### Post by philinux on 2008-06-20
You've got plenty of ram to run Firefox

---

### Post by mivo on 2008-06-20
FF3 works well on my laptop (Xubuntu, 512 MB) and on my desktop (Ubuntu, 3 GB). It never crashed on me so far. Not everyone is so lucky it seems, though.

---

### Post by TimGS on 2008-06-21
I'm having the same Opera issue, just since yesterday - whats changed, I don't know. I've been running Hardy for a while now, and it has been fine with Opera before.

I had Opera 9.5. I purged it and installed 9.27 from the repos. No change.

I have 2GB RAM and a hyper threading Pentium. Hardly low spec, and Opera is hardly a hungry browser. Opera occupies 50% of CPU time when loading i.e. 100% of one of my CPUs, and takes a minute or so to appear.

I like Opera. I use Firefox for web developing, because it has better web development tools (not used Opera Dragonfly yet), but for day to day use, I like Opera.... which is a long winded way of saying 'use Firefox' is not a solution!

-- Tim.

Edit: see [http://ubuntuforums.org/showthread.php?t=810473](http://ubuntuforums.org/showthread.php?t=810473) Maybe not just Opera, maybe Hardy.

---

### Post by justinhj on 2008-06-21
I'm using Opera 9.50 Beta 2

on an AMD Athlon 2400 with 512M of ram. 

I found FF3 very sluggish, with occasional lock ups. Opera has been blindingly fast with no errors so far. You can try tuning you security settings perhaps. Some of the security stuff does a lot of work these days.

---

### Post by lobo-tuerto on 2008-06-23
I think is a general problem with Ubuntu 8.04, maybe a driver-hardware issues.

I have a similar problem with Firefox. My [thread]("http://ubuntuforums.org/showthread.php?t=831456").

---

