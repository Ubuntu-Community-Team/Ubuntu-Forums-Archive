---
title: "Error inserting mac80211 module"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by ymsaputra on 2013-02-27
Dear All,

I modify a header file in include/linux and then "make modules" until the end. After that I "make modules_install".

And then I try to copy the .ko file to /lib/modules/3.5.0 directory, after that I remove the older module 

rmmod mac80211

and load new module 

modprobe -v mac80211

but after that the error occured "FATAL: Error inserting mac80211 (/lib/modules/3.5.0+/kernel/net/mac80211/mac80211.ko): Invalid argument"

what should I do? T_T

I usually use that method (from copy to modprobe) and there is no problem but today this problem occured.

Need your help

Thank you

---

### Post by DuckHook on 2013-02-27
Why are you installing the mac module this way rather than letting whatever wireless module you are installing pull it down from the repository as a dependency? If you build the module yourself, it is possible that it is either using mismatched dependencies in its build, or choking on mismatched libraries afterwards. I.e. 3.7 module on 3.5 libraries. We have no idea what version of mac module you were building (or why).

---

