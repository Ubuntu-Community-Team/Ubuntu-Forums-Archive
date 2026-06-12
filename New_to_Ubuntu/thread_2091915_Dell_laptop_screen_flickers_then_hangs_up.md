---
title: "Dell laptop screen flickers then hangs up"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by dohc97 on 2012-12-06
I have no luck installing Ubuntu 12.10 in my 5 month old HP laptop.  I installed it the other night in my 6 year old Dell laptop.  Got it to run.  After about 5 minutes of using it, the screen flickers and then hangs up.  At this point, I have no recourse but to do a hard shutdown.  It happened everytime I restarted the laptop.

---

### Post by dannyboy79 on 2012-12-06
sounds like a graphics card driver issue. do you know what kind of graphics card you have? have you installed any drivers for it? can you boot to a live cd, then mount the your / partition, then look at /var/log/Xorg.0.log? Also look at syslog and kern.log?

---

