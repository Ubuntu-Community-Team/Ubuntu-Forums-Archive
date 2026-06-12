---
title: "[SOLVED] Gnash Problems"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Circular-Reasoning on 2008-05-25
Hi. I'm new to these forums, and to Linux, and just recently had a run-in with the Firefox plug in Gnash (for Ubuntu version 7.10). What happened was, after I rebooted my computer post-install, my mouse and keyboard would randomly stop interacting with my desktop. My mouse cursor would still move, but neither it nor my keyboard could interact with Ubuntu in any way. Every time I would log in, this would happen 10-15 seconds after, without fail. This happened after two installs, and only after I had just installed Gnash and rebooted. 

In an attempt to fix this problem, I logged in using the failsafe terminal and used the command:

sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash

But the problem persisted. So finally, I logged in and unplugged both my mouse and keyboard (both USB), and then plugged them back in. After I did that, everything worked fine. I rebooted and everything is still working fine right now.

I didn't know if this was the appropriate place, but I wanted to post this just in case the same thing happened to someone else.

---

