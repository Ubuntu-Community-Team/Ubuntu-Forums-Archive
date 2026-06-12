---
title: "How to make ubuntu wake an XP machine over LAN"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by DBrocks on 2008-05-08
Hey guys.

I've decided to do something that would make my family's computing much more efficient: Wake my XP machine from my Ubuntu server on my network. Like, to boot it up at a bout 6 in the morning on week-days for my mom, and at 2:15 before we get home from school. I've configured WOL on my XP machine. Now, how can I make ubuntu send the WOL message to my XP machine? 

Thanks!

~Dan

---

### Post by quelx on 2008-05-08
What you want is almost certainly covered in this thread
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

For the scheduling check out crontab
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

---

### Post by DBrocks on 2008-05-08
followed that. Still doesnt work. when I do

```
wakeonlan 00-07-E9-C0-F5-0E
```
(my xp mac address)

I get  "00-07-E9-C0-F5-0E is not a hardware address and I could not resolve it as to an IP address."

---

### Post by DBrocks on 2008-05-08
figured it out. Stupid windows listed the MAC with hyphens, not colons. Thanks!

---

