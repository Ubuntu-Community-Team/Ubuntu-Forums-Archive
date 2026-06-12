---
title: "Detect app running in wine, close it and restart it from cron?"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by jason_gibson2 on 2015-08-03
I have tried killing ids from ```
ps ax
``` yet the window still stays open. How can I close a running wine program from the command line??

Solved. I was looking for the wrong thing. Added this to my manager script and fire it at 2 am every morning. In this case I was looking for playonlinux to find the pid, I should have looked for the exact executable. In this case the process was named ```
wtlibrary.exe
```

```
kill $(pgrep wtlibrary.exe)
sleep 1
kill $(ps aux | grep .py | grep playonlinux | awk '{print $2}')
sleep 1
playonlinux --run Watchtower\ Library\ 2014
```

---

