---
title: "[SOLVED] Urgent help needed after upgrade!"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by BSAB_80 on 2008-11-02
Hi there.

So my system upgraded my Kubuntu and it decided all by itself to give me KDE 4.1 instead of the 3.whatever i had before and always worked fine for me.

So now when i boot up, the font size is HUGE, as in a letter will be the size of a third of the screen, and i can't even access the menus or do stuff because i can't read anything!
(Currently typing this from an internet cafe, if you're wondering)

Please tell me there's a way of solving this.
I'm assumig that i can just boot up to the command line and then edit a file with graphic preferences or font preferences or something of the sort, but i jhave no idea where to begin.

HELP!!

---

### Post by Ron G on 2008-11-02
I don't know the answer to your problem, but who ever said it would be wise to wait a month or to, to upgrade, was correct. I upgraded with a clean install, and had so many problems, I have already went back to 8.04. I liked it fine, and have no idea why I was in such a big hurry to upgrade. I think I will leave the new one alone for a few weeks, and let all the bugs and fixes be taken care of for me. I dont want or need the headaches. It takes too much time to fix everything back to where I had it each time.

---

### Post by BSAB_80 on 2008-11-02
So i found something online after a bit of googling:
[http://kubuntuforums.net/forums/index.php?topic=3087975.msg98804#msg98804](http://kubuntuforums.net/forums/index.php?topic=3087975.msg98804#msg98804)

And apparently if i do this ```
(to be clear - this is in /etc/kde3/kdm/kdmrc)

It was obvious that the login screen wasn't any standard size (it's not like it was set to anything sane like 640x480) - so it dawned on me that it might be that the new driver misdetects the dpi - and surely enough, after changing the ServerCMD line to
Code:

ServerCmd=/usr/bin/X -br -dpi 100
```

That might solve my problem

But can anyone tell me how i do this from the command prompt?

---

### Post by BSAB_80 on 2008-11-02
Sorted.
VIM did the trick.

---

