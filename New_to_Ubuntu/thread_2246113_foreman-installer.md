---
title: "foreman-installer"
date: 2014-09-28
forum: New to Ubuntu
---

### Post by mia3 on 2014-09-28
Hello,

I'm installing foreman on ubuntu 12.04 but once I run following command it gives error.

apt-get update && apt-get install foreman-installer

The error is "unable to locate package foreman-installer"

Before it I've run following commands to install the repository and it had been done successfully.
echo "deb [http://deb.theforeman.org/](http://deb.theforeman.org/) precise 1.6" > /etc/apt/sources.list.d/foreman.list
echo "deb [http://deb.theforeman.org/](http://deb.theforeman.org/) plugins 1.6" >> /etc/apt/sources.list.d/foreman.list

Any help would be appreciate.

Thanks,

---

### Post by Old_Grey_Wolf on 2014-09-28
Here is the installation  instructions from their website [http://theforeman.org/manuals/1.6/quickstart_guide.html](http://theforeman.org/manuals/1.6/quickstart_guide.html). Looks like you left out a step.

---

