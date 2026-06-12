---
title: "my-weather-indicator not refreshing"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by JohnDillinger43 on 2013-05-01
Indicator-weather, which I used before, has become so buggy as of 12.04 that I had to stop using it.  I switched the my-weather-indicator, which is great so far.  The one problem I'm having is that it won't auto refresh.  It always says "Refresh weather (updated now)", but never actually updates.  If I click to refresh it, it refreshes just fine.  I tried different sources (open weather, yahoo) and had the same problem.  I found this bug: [https://bugs.launchpad.net/my-weather-indicator/+bug/1065884](https://bugs.launchpad.net/my-weather-indicator/+bug/1065884), which is labeled fixed as of last year, but I'm having this exact same problem right now, and I just installed the program a few days ago.

---

### Post by JohnDillinger43 on 2013-05-04
I've established that this is an intermittent problem: for the first couple hours after I reboot, it auto-refreshes, but after that it gets stuck on "Updated Now".  I've run apt-get update && apt-get upgrade, so I don't think it's a case of an outdated package, which is why I'm confused as to why this a known bug marked solved.

---

### Post by JohnDillinger43 on 2013-06-04
I've established that the failure to auto-refresh isn't a time issue.  It happens when you manually hit the "refresh weather" button.  After that it won't auto refresh again until you reboot.  This definitely seems like the same bug from before that was erroneously labeled fixed.

---

### Post by rburkartjo on 2013-06-04
working fine on my end running xubuntu 13.04. i have version 06.1.2quantal.1.

---

### Post by rburkartjo on 2013-06-04
do you have the ppa installed? you might try this

[http://www.noobslab.com/2013/01/install-my-weather-indicator-in-ubuntu.html](http://www.noobslab.com/2013/01/install-my-weather-indicator-in-ubuntu.html)

---

