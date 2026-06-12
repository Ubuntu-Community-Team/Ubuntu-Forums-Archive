---
title: "[SOLVED] removing busybox"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by nekroskoma on 2008-08-06
awhile ago i added the debian repository to my source list i didn't install anything though, at least i though i didn't. it turns out that busybox got installed and now every time i boot my computer its slower then it used to be so my question is

how can i remove busy box and return to my pre-busybox state and not brick my system

---

### Post by ibuclaw on 2008-08-06
You can pin the Debian repository in such a way that all packages from it will be downgraded.


What is the line that ties you to the Debian Repository?

Regards
Iain

---

### Post by nekroskoma on 2008-08-06
> **tinivole said:**
> You can pin the Debian repository in such a way that all packages from it will be downgraded.


What is the line that ties you to the Debian Repository?

Regards
Iain

not sure what you mean

what happened is that busybox got install while i still have busybox-initramfs installed

i would like to get rid of the busybox while keeping the busybox-initramfs package but it wants me to uninstall alot of other stuff like grub and a couple linux images

---

### Post by ibuclaw on 2008-08-07
I mean that busybox in the ubuntu repo doesn't have such strong dependancies with the various packages that you say it does.
```
cat /etc/apt/sources.list | sed '/^#/d;/^$/d'
```
```
apt-cache policy busybox
```
```
sudo apt-get --simulate remove busybox
```

should give more than enough information about busybox and the original to get a workable solution.

And as for apt-pinning.
It is a useful tool for apt which allows you to add other repositories without your system wanting to upgrade everything immediately.
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)
Setting the debian repository to have a priority of -1 should downgrade all apps from that repo back to the ubuntu versions.

Regards
Iain

---

### Post by nekroskoma on 2008-08-07
i fixed it another way, though the apt-pinning will be very useful

---

