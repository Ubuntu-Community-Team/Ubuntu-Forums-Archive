---
title: "Problem with....firefox?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by jjstein on 2008-07-07
I really have no idea how to address this problem because honestly I really don't know what it is.  Let me explain the best I can.

About 50% of the times that I watch a video on youtube, I get a "firefox is not responding" error.  I would have to click "end process" and then restart firefox.  Also, in addition to this, occasionally I would have to completely end the process before firefox would work again because I was getting a "process is already running, close the current operation before opening another one etc..." error.  That was happening on gutsy and I just kind of ignored it hoping it would be corrected with an update.

Now, I (for whatever reason) upgraded to hardy.  In addition to the previously mentioned issues, now every time I watch any form of video, the audio goes out as soon as I navigate away from that page.  If I'm lucky, that's all that happens but 9 times out of 10 everything just freezes up completely and I have to restart(by first pressing ctrl+alt+backspace, then restarting from the login menu).   It's gotten to the point where I'm restarting my system every couple minutes which is ridiculous.


I don't know if this is one single problem or a multitude of problems but it is rather frustrating.  Any help would be incredibly appreciated.  Oh and also, my graphics drivers are installed and everything says they are working so I don't believe that is the problem.

---

### Post by mjwhitfield on 2008-07-07
> **jjstein said:**
> Now, I (for whatever reason) upgraded to hardy.Just to clarify, did you upgrade, or so a fresh install?

If you did upgrade, what method did you use?

---

### Post by jjstein on 2008-07-07
I upgraded by pushing the "upgrade to hardy" button in the update manager.

---

### Post by OldGrey on 2008-07-07
My personal experience is that upgrading is often problematic, resulting in a number of anoying bugs. Better if you can to back up all your important data and do a fresh install. Better still if you have a separate /home partition so you can fresh install without losing your settings.

---

### Post by jjstein on 2008-07-07
I don't think that is the problem though considering a lot of this was already happening before I upgraded.

---

### Post by philinux on 2008-07-07
I would try safe mode first.

In a terminal run

firefox -safe-mode

See if that stops the crashes.

---

### Post by jjstein on 2008-07-07
well I tried safe mode and it didn't really change that much.  It prevented me from having to restart my system but firefox still crashed after I watched a couple videos.

---

