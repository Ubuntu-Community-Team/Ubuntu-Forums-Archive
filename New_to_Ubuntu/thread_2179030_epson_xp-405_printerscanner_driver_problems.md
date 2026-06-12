---
title: "epson xp-405 printer/scanner driver problems"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by stefan10 on 2013-10-06
Hello,

I have some problems with the installation of my drivers. 

When using the Ubuntu Software Center for the installation I get this message: cannot install lsb. 

What should I do?

I am using Ubuntu 12.04 LTS 32 bit

Thanks

---

### Post by DuckHook on 2013-10-07
[lsb]("http://www.linuxfoundation.org/collaborate/workgroups/lsb/about") is Linux Standard Base, a set of core system services/utilities/calls that third parties can use to write apps that should then be portable across all Linux Distros. Do:```
sudo apt-get update && sudo apt-get install lsb
```This should install lsb. I know nothing about your specific drivers, but try installing them again after you have successfully installed lsb.

---

