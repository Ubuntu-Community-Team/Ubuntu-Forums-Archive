---
title: "&quot;invalid problem report&quot;???"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by alabamatoy on 2013-03-19
I keep getting a popup that says "Invalid Problem Report could not determine the package or source package name".  The only choice is close, it goes away, then after a while I get it again.

Any suggestions on how to troubleshoot?

Is there a system event log?

---

### Post by ibjsb4 on 2013-03-19
Maybe

```
sudo rm /var/lib/apt/lists/*
 sudo apt-get update
```
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1052927](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1052927)

more here
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Invalid+Problem+Report+could+not+determine+the+package+or+source+package+name&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Invalid+Problem+Report+could+not+determine+the+package+or+source+package+name&sa=Search&cof=FORID:9)

---

