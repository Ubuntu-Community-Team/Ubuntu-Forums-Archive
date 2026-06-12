---
title: "Logging out after a set period of time"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by me (caleb) on 2008-04-29
Is there anyway to have a user log out after being logged in for a set amount of time?

Like say I want to limit myself to an hour of games a day max, so I set a special account to log me out automatically after an hour.

---

### Post by furtypajohn on 2011-07-01
Try this script:

```
#!/bin/bash
logged=`uptime | awk '{print $3}' | sed 's/,//'`
hour=`echo $logged | sed 's/:[0-9]\+$//'`
minute=`echo $logged | sed 's/^[0-9]\+://'`

# If we've been logged in for too long then we
# need to log out
if [ $hour -gt 2 ]; then
  gnome-session-save --logout  
fi
```

---

### Post by nothingspecial on 2011-07-01
*****Edit - doh, I replied to a 3/4 year old post

---

