---
title: "sysmonitor- indicator"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by asmolinski on 2014-01-31
I installed the sysmonitor indicator through the ppa, it won't run.  I am running ubuntu 13.10
when I enter the command into my terminal indicator-sysmonitor. This is what it tells me.

Traceback (most recent call last):
  File "/usr/bin/indicator-sysmonitor", line 27, in <module>
    import appindicator
ImportError: No module named appindicator

---

### Post by grahammechanical on 2014-01-31
What PPA? Is that utility available for Ubuntu 13.10? According to this there does not seem to be a version later than June 2012. I could be wrong.

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

Regards.

---

### Post by asmolinski on 2014-01-31
ppa:noobslab/indicators

I found how to install the indicator on a site that shows indicators. It does say that it is available for 13.10

---

### Post by stinkeye on 2014-02-01
Installs and runs here on 13.10. 

In a terminal, run....
```
sudo apt-get install python-appindicator
```

Then try to run indicator-sysmonitor again.

---

### Post by asmolinski on 2014-02-01
Thank you! That fixed it

---

