---
title: "Lengthy Boot time for new Hardy install"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by opm595 on 2008-07-11
Hi Guys,
I have just upgraded a laptop from Gutsy to Hardy and all seemingly went well. However, the system takes forever to boot and/or restart  - in the vicinity of about 15 minutes, when it usaully only take about 3 to 5 etc.

More then likely, a BIOS prob I'd imagine. BIOS is around circa 2005, on a Toshiba M70 lappy, approx 3 years old. So, in theory all should be fine. 

Any takers on this one? Or should I start again with a fresh re-install with 8.04

Thanks in advance,
Rob

---

### Post by hyper_ch on 2008-07-11
you could install bootchart to see how much time processes take to boot up (up to the x server). You will get a graph in /var/log/bootchart

---

### Post by markbuntu on 2008-07-11
Look in the kern.log and syslog for long lags between time stamps or for hanging/failing processes.

---

