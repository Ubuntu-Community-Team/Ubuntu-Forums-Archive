---
title: "AFTER security updates, sound won't work"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by erans on 2008-07-11
I just did a fresh installation of Ubuntu. When I first booted up, my sound was working. After installing the security updates, it doesn't work anymore. :\ I also did sudo apt-get build-essential after I installed the security updates and rebooted, so my sound wasn't working when I ran that command and it didn't help. 

Still a complete newbie, so I don't know where to start with this one. Any ideas?

---

### Post by spiderbatdad on 2008-07-11
I wonder if you updated more than security updates...the types of updates you receive can be configured in System>>Administration>>SoftwareSources>>Update.

I'm thinking you may have received a kernel update. I don't know if your menu.lst is set up to save previous kernels, or if the previous kernel was overwritten.

Check the file, /boot/grub/menu.lst and look for the section, ```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
```

See what number of kernels you have, not counting recovery. For example, above shows kernel 2.6.22-14. I imagine you will see 2.6.24-15 or so. But look for another lower kernel version, maybe the third listed...If you have the previous kernel, grub can be configured to use it.

---

### Post by erans on 2008-07-12
I managed to fix this problem by following the Sound Troubleshooting guide and reinstalling my sound stuff so it was all set to the default settings. Thanks!

---

