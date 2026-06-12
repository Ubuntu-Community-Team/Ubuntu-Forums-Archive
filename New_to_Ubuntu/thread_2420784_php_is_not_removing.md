---
title: "php is not removing"
date: 2019-06-11
forum: New to Ubuntu
---

### Post by pratap73 on 2019-06-11
sudo apt-get purge `dpkg -l | grep php| awk '{print $2}' |tr "\n" " "`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package php7.2-readline needs to be reinstalled, but I can't find an archive for it.

---

