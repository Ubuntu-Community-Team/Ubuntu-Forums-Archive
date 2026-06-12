---
title: "apt-get upgrade gives &quot;403 forbidden&quot; error"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by elang on 2013-10-17
I'm running Ubuntu 13.04 64b, and **sudo apt-get update** works fine
But when I run **sudo apt-get upgrade**:
```

Err http://archive.ubuntu.com/ubuntu/ raring-updates/main python3.3-minimal amd64 3.3.1-1ubuntu5.2
  403  Forbidden
Err http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/ raring/main gimp amd64 2.8.6-0raring1~ppa
  403  Forbidden
Err http://archive.ubuntu.com/ubuntu/ raring-security/main python3.3-minimal amd64 3.3.1-1ubuntu5.2
  403  Forbidden
Err http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/ raring/main gimp-help-en all 1:2.8-0raring16~ppa
  403  Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python3.3/python3.3-minimal_3.3.1-1ubuntu5.2_amd64.deb  403  Forbidden
Failed to fetch http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/pool/main/g/gimp/gimp_2.8.6-0raring1~ppa_amd64.deb  403  Forbidden
Failed to fetch http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/pool/main/g/gimp-help/gimp-help-en_2.8-0raring16~ppa_all.deb  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
Running sudo apt-get upgrade --fix-missing installs some updates, but the above errors still show

The software update app shows the error
[ATTACH=CONFIG]247016[/ATTACH]

and when I press continue, I get the error "check your internet connection", even though the internet is working fine (apt-get update and web browsing work)

It is not a server problem. This has been bothering me for almost a month. How do I fix it?

---

### Post by sandyd on 2013-10-17
Have you setup a proxy, or are behind one?

---

### Post by elang on 2013-10-18
Yes, I am working behind a proxy.

But there seems to be no problem with update, install or web browsing.
Software Center also works like a charm

---

