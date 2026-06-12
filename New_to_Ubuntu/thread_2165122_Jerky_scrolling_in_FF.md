---
title: "Jerky scrolling in FF"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by Norm24 on 2013-08-03
Can't say exactly when this started but I've noticed in the past week that when I scroll up/down on a web page FF is very "jerky",its always playing catch-up.Anyone else having this issue?

---

### Post by Vladlenin5000 on 2013-08-03
No, I can't say I'm having the issue. I had some similar behavior but it was related with the page's content.

---

### Post by tgalati4 on 2013-08-03
[http://about:config](http://about:config)  see if smooth scrolling is set on.  There may be a few other settings as well.  It could be a stuck flash or javascript in a background tab.  Try clearing the cache and history, shutting down ff and try again.  It could be that your cache/history is so large that your disk IO is causing a performance bottleneck.

Run *top* in a terminal and see if you have IO Waits (wa) or other performance problems.

---

### Post by MrSteve on 2013-08-03
i have the same problem on the odd occasion
just closing FF and then re-open FF seems to fix the issue ...

---

