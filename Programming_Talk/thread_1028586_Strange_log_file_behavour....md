---
title: "Strange log file behavour..."
date: 2009-01-02
forum: Programming Talk
---

### Post by PryGuy on 2009-01-02
Good day to you all and Happy New Year!
I'm really confused now... I wrote a script that reads my /proc/net/dev and takes the ppp0 traffic value, then stores it into a log file... It updates the log file every 30 seconds. But sometimes after reboot I notice that there are old values in the log file. It looks like the cache flushes on shutdown and *sometimes* overwrites the data that is in the log file with the old data. That's the only explanation I have so far... I'll keep inspecting it, but do you have any comments please?

---

### Post by dwhitney67 on 2009-01-02
It's hard to know what is going on without seeing the code of your script.

Out of curiosity, are you using logrotate to manage your log file(s)?

---

