---
title: "Firefox not working after upgrade"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by OisinT on 2008-04-24
Just installed 8.04 and at first no internet was working.
Reset modem and restarted a few times and I am able to connect to the internet, but firefox isn't working at all.
Would appreciate help in getting it up and running again as it's my favourite browser.
Also, just noticed while typing this that my num pad doesn't seem to be working either. (lol yes - i checked to make sure num lock was on!)

---

### Post by Mazza558 on 2008-04-24
How is it not working? Does it not start up at all?

What does running "firefox" in the terminal show?

---

### Post by Oldsoldier2003 on 2008-04-24
> **OisinT said:**
> Just installed 8.04 and at first no internet was working.
Reset modem and restarted a few times and I am able to connect to the internet, but firefox isn't working at all.
Would appreciate help in getting it up and running again as it's my favourite browser.
Also, just noticed while typing this that my num pad doesn't seem to be working either. (lol yes - i checked to make sure num lock was on!)

For the Firefox issue try opening a terminal and typing firefox. The first time you run it it will attempt to import and install your bookmarks (configure itself), after that you should be able to run FF from a menu or launcher with no problems

---

### Post by spiderbatdad on 2008-04-24
[http://ubuntuforums.org/showthread.php?t=765092](http://ubuntuforums.org/showthread.php?t=765092)

[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

Its broken. Get iceape and seamonkey packages from synaptic or try to fix firefox using work-arounds suggested on launchpad.

---

### Post by OisinT on 2008-04-24
> **Mazza558 said:**
> How is it not working? Does it not start up at all?

What does running "firefox" in the terminal show?

> **Oldsoldier2003 said:**
> For the Firefox issue try opening a terminal and typing firefox. The first time you run it it will attempt to import and install your bookmarks (configure itself), after that you should be able to run FF from a menu or launcher with no problems

when I do that firefox opens and doesn't attempt to load anything - it just displays "server not found..." 
and does that on every webpage I attempt to visit.  It's acting as if I'm not connected to the internet.

---

### Post by Mazza558 on 2008-04-24
> **OisinT said:**
> when I do that firefox opens and doesn't attempt to load anything - it just displays "server not found..." 
and does that on every webpage I attempt to visit.  It's acting as if I'm not connected to the internet.

Try 

```
ping www.google.com
```

In the terminal. I'm not sure your net connection's working properly.

---

### Post by OisinT on 2008-04-24
```
oisint@OisinT1:~$ ping www.google.com
PING www.l.google.com (66.249.93.99) 56(84) bytes of data.
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=1 ttl=246 time=51.3 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=2 ttl=246 time=47.2 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=3 ttl=246 time=46.9 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=4 ttl=246 time=49.4 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=5 ttl=246 time=48.4 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=6 ttl=246 time=49.9 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=7 ttl=246 time=47.8 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=8 ttl=246 time=48.0 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=9 ttl=246 time=47.6 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=10 ttl=246 time=47.8 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=11 ttl=246 time=47.3 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=12 ttl=246 time=48.8 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=13 ttl=246 time=49.0 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=14 ttl=246 time=48.4 ms

```



it's just odd to me that opera is working and it seems ktorrent and pidgin is too.
it might be important to note that after the first restart post upgrade nothing was working properly.
I just checked thunderbird and it seems to be working too.

---

### Post by OisinT on 2008-04-24
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=765092](http://ubuntuforums.org/showthread.php?t=765092)

[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

Its broken. Get iceape and seamonkey packages from synaptic or try to fix firefox using work-arounds suggested on launchpad.


all versions of firefox are broken?
my internet connection also seems slower than it was before the upgrade too.

---

### Post by OisinT on 2008-04-25
I understand that my question in why Firefox isn't working may be a difficult one to answer, but does anyone know how to fix my number pad?  I'm amazingly missing it a lot.

---

