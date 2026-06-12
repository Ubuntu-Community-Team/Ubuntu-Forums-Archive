---
title: "&quot;Percentage done&quot; progress in Bash"
date: 2012-07-06
forum: Programming Talk
---

### Post by EonsNearby on 2012-07-06
I wrote a bash script that repeatedly runs nmap on different IP addresses, and I would like to output a "Percentage done" progress counter.  However, I don't want it to output a new percentage while the old one is still on screen.  I would like it to overwrite the previously output percentage and put the new percentage in its place.  Basically, I don't want it to do the following:
-> 0%
1%
2%
3%

I want it to first output 0%
->0%
And then when the next percentage is calculated, I want it to output the next percentage where the previous percentage was, so
->1%
Then when the next percentage is calculated:
->2%

Can someone help me with this?

---

### Post by cipherboy_loc on 2012-07-06
```

 echo -e -n "0%"; sleep 1 ; echo -e -n "\b\b1%" ; sleep 1 ; echo -e -n "\b\b2%"

```


**Edit: no need to run as root, artifact from terminal session. Tested on particular desktop I was connected to over breakfast.**

Cipherboy

---

### Post by sisco311 on 2012-07-07
BashFAQ 034 & 044 (link in my signature).

---

