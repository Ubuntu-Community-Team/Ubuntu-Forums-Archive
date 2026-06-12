---
title: "How To Display WAN IP In Conky"
date: 2007-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by tturrisi on 2007-04-18
Here's a real simple way to grab the wan ip using wget and display in Conky:
*2007-04-29 - modified & improved version.*

**Save as /home/scripts/.wan-ip & make it executable.**
```
#!/bin/sh
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

**Add this line to your .conkyrc.**
```
Wan IP:$alignr${execi 600 /home/scripts/.wan-ip}
```

**What it does:**
Grabs your wan ip address from a Web page at dydns.org using wget.

**Example:**

---

### Post by derekguy on 2007-05-22
Cheers for the tip. Conky is quite fun to play around with.

---

### Post by kevdog on 2008-02-07
How about just this:

```
wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'
```

---

