---
title: "Google Gadgets package problem"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by cocopeanut on 2008-10-04
I'm trying to install google gadgets. When I went to getdeb.net and tried to install the debian file, it warned me that the libpango package is insatiable?

So I tried instead to do this:
[PHP]
sudo apt-get install google-gadgets[/PHP]

and it gave me the following error:

[PHP]The following packages have unmet dependencies:
  google-gadgets: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages[/PHP]

So I went to synaptic package manager and tried to reinstall the libpango packages and also installed the dev packages and anything else that was related.

I tried to apt-get command again, but got the same issue.

Finally, I tried to select "Fix Broke Packages" from synaptic, but it didn't work either.

I'm at a loss? :)

-=-Oscar-=-

Note: I'm running ubuntu 8.04 that was upgraded from 7.10.

---

### Post by phidia on 2008-10-04
If you want to turn your system into gOS then you will need to change your repos, update and then upgrade.
Whether that kind of upgrade will work is another question.

Maybe I don't understand what you're asking though. AFAIK google gadgets is another name for gOS which is a distro based on hardy but it uses different repos.

---

### Post by cocopeanut on 2008-10-04
> **phidia said:**
> If you want to turn your system into gOS then you will need to change your repos, update and then upgrade.
Whether that kind of upgrade will work is another question.

Maybe I don't understand what you're asking though. AFAIK google gadgets is another name for gOS which is a distro based on hardy but it uses different repos.

I don't understand what you're saying. But I'll try to clarify.

I installed Ubuntu 7.10 from a Ubuntu CD that was mailed to me earlier in the year. After I installed it, the update manager upgraded me automatically to the latest version of Ubuntu 8.04. Once that was all complete, I started installing the software I wanted.

I saw Google Gadgets was available for Ubuntu OS on [http://www.getdeb.net](http://www.getdeb.net). But when I try to install it, it gave me the errors I listed in the original post. I'm just trying to figure out what I need to do next.

fyi... I'm a newbie, so I'm not familiar with some Linux terminology or acronyms.

Thanks,

-=-Oscar-=-

---

### Post by Flynn555 on 2008-10-04
i think this might be what you are looking for

[http://ubuntuforums.org/showthread.php?t=821478](http://ubuntuforums.org/showthread.php?t=821478)

---

### Post by cocopeanut on 2008-10-04
> **Flynn555 said:**
> i think this might be what you are looking for

[http://ubuntuforums.org/showthread.php?t=821478](http://ubuntuforums.org/showthread.php?t=821478)

Thank you, but that doesn't help. The debian installer says:

Error: Dependency is not satisfiable: libpango1.0-0

Guys, I really think the issue with with that package. I just don't know what to do besides what I have already tried.

Thanks,

-=-Oscar-=-

---

