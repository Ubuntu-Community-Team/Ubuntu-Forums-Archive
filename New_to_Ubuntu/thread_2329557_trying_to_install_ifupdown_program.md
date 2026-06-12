---
title: "trying to install ifupdown program"
date: 2016-07-03
forum: New to Ubuntu
---

### Post by evanvhere on 2016-07-03
Hello: 

I am trying to install a program called ifupdown which is required by git and nokogiri (rails dependency). I keep getting errors trying to install it namely: 
ifupdown : Breaks: systemd (< 228-3~)
            Breaks: systemd:i386 (< 228-3~)

Seems like ifupdown cannot work with systemd. Anyone else had this problem and have any insights on how to fix? Searched the web for a while to no avail...

---

### Post by jeremy31 on 2016-07-03
Welcome to the forums, please post the results for ```
lsb_release -a
```

---

### Post by evanvhere on 2016-07-04
Hi. Thanks glad to be here. Here are the results of lsb: 

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

---

### Post by grahammechanical on 2016-07-04
On my 16.04 install ifupdown is already installed. It is at version 0.8.10. And systemd is at version 229.

I can only guess that the version of ifupdown that you want to install needs a lower version of systemd than that in 16.04.

---

