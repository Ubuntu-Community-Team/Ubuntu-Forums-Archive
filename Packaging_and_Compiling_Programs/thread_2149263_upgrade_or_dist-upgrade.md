---
title: "upgrade or dist-upgrade?"
date: 2013-05-28
forum: Packaging and Compiling Programs
---

### Post by HansMeiser2 on 2013-05-28
Hello,

only a short question. In which way are Packages marked so apt-get offers them only when using dist-upgrade and not when using only upgrade?
I have a Package adopted which should be installable just bei apt-get upgrade, currently i have to use dist-upgrade. This adopted package updates an existing package and removes some obsolete packages. May be this is the reason?

Thanks,
Hans

---

### Post by sudodus on 2013-05-28
In general kernel upgrades need dist-upgrade. But there are cases when there are conflicts between packages, and dist-upgrade has a 'smart' way to solve them. See ```
man apt-get
```

>            dist-upgrade in addition to performing the function of upgrade, also intelligently handles
           changing dependencies with new versions of packages; apt-get has a "smart" conflict
           resolution system, and it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade command may remove some
           packages. The /etc/apt/sources.list file contains a list of locations from which to
           retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.


---

### Post by HansMeiser2 on 2013-05-28
Thanks, just like expected.

---

