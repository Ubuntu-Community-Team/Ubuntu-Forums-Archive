---
title: "Software updater in 15.04 does not find updates"
date: 2015-10-20
forum: New to Ubuntu
---

### Post by matsmohlin on 2015-10-20
I have just migrated or installed Ubuntu desktop 15.04 and now when I try to use Software Updater it comes back and says that I need to check my internet access that works properly.
From another Ubuntu 14.04 on the same network Software Updater works OK.
Any advice ? 
Mats Mohlin
Stockholm Sweden

---

### Post by grahammechanical on 2015-10-20
You might have a URL to a repository that is inaccurate. This often happens with Personal Package Archives (PPA). They are useful for installing software but many are not able to give updates to the software and so they should be disabled to avoid error messages like this.

You can run these two commands and watch the printout for error messages as to which URLs are not giving a connection

```
sudo apt-get update
sudo apt-get upgrade
```

Here is a similar thread. It might explain your problem.

[http://ubuntuforums.org/showthread.php?t=2298441](http://ubuntuforums.org/showthread.php?t=2298441)

I run the development version of the next release of Ubuntu and I update daily and I often see this type of error message because during the 26 week development period some of the repositories are not active until just before release day. That situation never stops the actual update/upgrade from continuing. I live with the situation rather than editing the sources.list file.

Regards

---

### Post by marcus_s on 2015-10-22
If you are in a corporate environment, you might also want to check for proxy connections. Or if there are some kind of other firewalls active.

---

