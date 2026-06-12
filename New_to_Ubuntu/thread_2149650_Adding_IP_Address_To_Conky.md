---
title: "Adding IP Address To Conky?"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by wpwend42 on 2013-05-29
How do I go about adding a line to my Conky that displays my current IP address? I looked around online and have not found a solution that worked. I am connecting to the internet via wireless. Thanks!

---

### Post by CatKiller on 2013-05-29
Mine's got a slightly hacky ask-a-website solution to this problem. I'll check the line for you when I get home.

---

### Post by deadflowr on 2013-05-29
You could try adding this line

```
${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
```

Though, I've seen others use what'smyip.

---

### Post by CatKiller on 2013-05-29
Having checked it, my line's remarkably similar to deadflowr's above. I use pre-exec rather than execi though, since my IP address doesn't change very often.

---

### Post by stinkeye on 2013-05-29
```
${curl ifconfig.me}
```
May need to install curl.

Goto **ifconfig.me** in your web browser for other options.

From man conky...
> **curl url (interval_in_minutes) **
 Download data from URI using Curl at the specified interval. The interval may be a floating point value greater than 0, otherwise defaults to 15 minutes. Most useful when used in conjunction with Lua and the Lua API. This object is threaded, and once a thread is created it can't be explicitly destroyed. One thread will run for each URI specified. You can use any protocol that Curl supports.

---

### Post by wpwend42 on 2013-05-30
The first one worked! Thanks!

---

