---
title: "Static in my Sound"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Archform on 2008-08-19
I just installed ubuntu 8.04.1. Everything seems really awesome except I can't get my sound working properly. I tried Kubuntu and there wasn't any issue. I tried several walk threws here in the forums and a couple from the web and still was not able to find a solution. Is this a normal problem and is there a solution out there.

---

### Post by jbrown96 on 2008-08-19
Not sure if you have tried this. The static could be caused by unused channels, especially inputs. In a terminal, ```
alsamixer
``` and use the arrow keys and "m" to mute all channels but the ones that you need.

---

### Post by Epetai on 2008-08-27
I just wanted to say I had exactly the same problem and this fixed it.  I'm also running Ubuntu 8.04 and both speakers constantly poured out static whenever they were switched on.  Didn't matter whether music was playing or not.  Very annoying.

I opened a terminal and typed ```
alsamixer
``` like jbrown96 said.  For me, mute didn't work, but when I increased the "Master" to 100 (by using the "up" arrow) my static magically stopped.  So, thank you.

---

