---
title: "Fresh virtual install of 13.10 with SSH... running at 5gb ram usage after an hour?"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by lukasgrove on 2013-12-04
I recently setup Unbuntu 13.10 as a virtual machine within Hyper-V on Win8 to start working through my understanding of linux in general. After installation I updated the system, installed ssh so I could connect remotely, and let the system sit to go read on what to do to setup some software I was going to try out. After about a half hour I went back and opened the system monitor (having just looked up how to check resource usage) and noticed it was at an astounding 6gb of the 8gb I allocated it. Now I know this isn't a bare-bones build, so it's not gonna be like the 20mb ram usage builds that people put on their phones and what not, but to be using 6g after having done nothing seemed ridiculous. I rebooted the system and checked to find it back at about 500mb, which seemed more than reasonable, but after about half an hour it was back to about 5g.


I've looked through the list of what running, nothing says it's using more than the 118mb for compiz (which from my understanding is effectively the graphical explorer of the system), and the sum of everything else is actually less than 300mb, so I'm trying to figure out where the other 4.7g is being used.

I can provide whatever might be useful for figuring this out, logs and what not, but I dunno where to actually begin since my background is in windows systems.

---

### Post by r-senior on 2013-12-04
What do you get if you run 'free -m' in a terminal?

```
you@yourmachine:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       3760        193          0        270       1709
-/+ buffers/cache:       1780       2173
Swap:         3905         18       3887
```

You might also want to read this:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by lukasgrove on 2013-12-04
```
$ sudo free -m
             total       used       free     shared    buffers     cached
Mem:          7788       4719       3069          0        186        683
-/+ buffers/cache:       3849       3939
Swap:         7999          0       7999


```

It seems that based off that website I still am using about 4g? Maybe I read it wrong, what would I check after?

---

### Post by drmrgd on 2013-12-04
Yeah, it does look like you're currently using a lot of RAM.  Maybe run top (or even nicer htop - have to install it first) to find out what's consuming all that memory.  What shows up in system monitor should be accurate, but perhaps you'll find something else with htop as it's a bit more granular.

---

### Post by lukasgrove on 2013-12-04
Sorted by memory, should I have that many compiz...?


[IMG]http://i.troll.ws/cd4646c3.png[/IMG]

---

