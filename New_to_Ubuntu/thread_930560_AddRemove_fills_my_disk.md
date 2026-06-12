---
title: "Add/Remove fills my disk"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by rvabdn on 2008-09-26
I have a Asus eeepc 901 on which I have installed [ubuntu eee]("http://www.ubuntu-eee.com/") on the 4gig ssd(actually 3.75G reported by gparted).

The clean install took up around 1.8gigs of disk space.  I have installed tuxguitar which takes up less than 10MB and sun java 6 runtime.  Suddenly I find my disk usage has jumped up to 3.57 gigs.

I'm confused as to whats taking up all that extra space.  I used the add/remove program to install java and it did download lists of available software.  Is it possible this has filled my disk?

---

### Post by Orange_and_Green on 2008-09-26
Hello rvabdn! :)

I think it's very possible as java has a lot of dependencies, so to install that, you have to install loads of other packages before...

To clean up a little space, you can run
```
sudo aptitude clean
```

which will empty the apt-get downloaded package cache.

Good luck:KS

[EDIT]When you want to install something, try using System->Administration->Synaptic package manager, it will give you a much better overview of what you install. I don't know if add/remove uses apt-get or not, so I cannot tell you for sure if "aptitude clean" will have any effect.

---

