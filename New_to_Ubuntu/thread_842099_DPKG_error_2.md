---
title: "DPKG error 2"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by kiterguy on 2008-06-27
I have just rnu update manager and while its gone through all of the motions, it comes up with an error saying "DPKG: failed to open package info file '/var/lib/dpkg/available' for reading: no such file or directory.  E: sub-process '/usr/bin/dpkg' returned and error code:(2). A package failed to install.

It then says none of my packages have been installed and they all need to be...

Any one able to shed some light?  and yes I have tried reinstalling dpkg.

---

### Post by iaculallad on 2008-06-27
Cache is corrupted. To fix this issue, open your terminal and issue the command below:

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by kiterguy on 2008-06-27
You're a legend... thanks heaps mate!! :popcorn:

---

