---
title: "running an (almost) invisible process."
date: 2015-02-17
forum: New to Ubuntu
---

### Post by berkbw on 2015-02-17
This is almost a rerun of an earlier post.  I want to run >&#65279;watch -n 1 "awk 'NR==3 {print \"WiFi Signal Strength = \" \$3 \"00 %\"}''' /proc/net/wireless"< .  "**watch**, supposedly located in procps is not found.  Now this used to work.  Then didn't.  Effect of updates?  How to fix?

Thanks,
b-

---

### Post by ian-weisser on 2015-02-17
Works great for me in 14.10, once you fix the syntax error.

FYI, Network Manager emits the changed signal strength over dbus. You can listen for that, too.

---

