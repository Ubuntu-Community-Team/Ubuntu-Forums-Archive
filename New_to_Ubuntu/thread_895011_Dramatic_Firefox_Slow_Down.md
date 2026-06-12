---
title: "Dramatic Firefox Slow Down"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by berencamlost on 2008-08-19
I've been having some pretty serious speed issues with Firefox. It seems to have started some time after i installed Tor, Privoxy, and Azureus . Everything worked fine until then. A few days after that Firefox slowed down to a near halt. On my 5 meg connection it takes Firefox around 5 to ten seconds just to load the Google start page. I've tried editing about:config settings (pipelining disabling ipv6 etc), uninstalling tor/privoxy, uninstalling/reinstalling Firefox, and now i just reformatted and reinstalled Ubuntu 8.04. After reinstalling Ubuntu i figured the issue would disappear but Firefox remains so slow it's practically unusable. When i boot XP Firefox works at it's normal speed. I've checked my Down and Up speeds and they are completely fine. I am at a *complete* loss as to whats wrong and what can be done to fix it. 
Any help is appreciated...

---

### Post by Pro-reason on 2008-08-19
Did you install other stuff too?  A new kernel update?  A video card drive update?  A Flash update?

I've seen Flash slow Firefox down (even on pages without Flash).

---

### Post by berencamlost on 2008-08-19
I have flash installed yes but right after i reinstalled Ubuntu i tried firefox with out any plugins and didn't see a difference

---

### Post by Crafty Kisses on 2008-08-19
> **berencamlost said:**
> I have flash installed yes but right after i reinstalled Ubuntu i tried firefox with out any plugins and didn't see a difference

When Firefox is running, post the following output:
```
top
```

---

### Post by berencamlost on 2008-08-19
Here...

```
top - 19:02:07 up 17 min,  2 users,  load average: 0.07, 0.23, 0.16
Tasks: 125 total,   1 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.2%sy,  0.0%ni, 98.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2075292k total,   497632k used,  1577660k free,    14256k buffers
Swap:   453120k total,        0k used,   453120k free,   284316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5626 root      20   0  291m  27m 7196 S    2  1.4   0:37.81 Xorg                                                            
 5897 home      20   0 20816  11m 7404 S    1  0.6   0:01.48 metacity                                                        
 6321 home      20   0 73864  19m  10m S    1  1.0   0:00.20 gnome-terminal                                                  
 6342 home      20   0  2308 1132  856 R    1  0.1   0:00.04 top                                                             
 6223 home      20   0  152m  62m  20m S    0  3.1   0:19.35 firefox                                                         
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.24 init                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                      
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2                                                     
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2                                                     
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2                                                      
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3                                                     
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3                                                     
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3                                                      
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                        
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                        
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/2                                                        
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/3                                                        
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                       
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                       
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/2                                                       
   59 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/3                                                       
   62 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                          
   63 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                    
  155 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                         
  205 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
```

---

### Post by berencamlost on 2008-08-19
bump

---

### Post by Pro-reason on 2008-08-20
Firefox doesn't seem to be using too much in the way of resources.

Try another browser (Epiphany, Konqueror, Opera...) to see whether the problem is specific to Firefox.

Try the Ubuntu live CD to see if the problem is specific to your installation.

Run a speed test (e.g. [http://www.zdnet.com.au/broadband/speedtest.htm](http://www.zdnet.com.au/broadband/speedtest.htm)) to see whether your connection speed is slow, or just the interface.

Try disabling all add-ons, to see if one is slowing you down.

---

### Post by silkstone on 2008-08-20
Close FF and Thunderbird.

Open a terminal and enter

firefox -safe-mode

That will disable add-ons and let you find if one of them is causing a problem.

---

