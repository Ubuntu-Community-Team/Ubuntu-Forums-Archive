---
title: "HOWTO: automatic updates"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by matid on 2005-04-11
I've just read about some people wanting to have their updates done automatically, so I made this simple HOWTO.
----
If you want to have your updates done automatically, follow these steps:
1. Download this file: [http://matid.emmatrade.pl/files/apt](http://matid.emmatrade.pl/files/apt)
2. Copy this file to **/etc/cron.daily**:
```
sudo cp apt /etc/cron.daily/
```
3. Append line: ```
APT:Periodic:Upgrade-Packages "1";
``` to **/etc/apt/apt.conf.d/10periodic**:
```
sudo -s
echo 'APT:Periodic:Upgrade-Packages "1";'>>/etc/apt/apt.conf.d/10periodic
exit
```
----
You're done! Now your system updates automatically!

---

### Post by XDevHald on 2005-04-13
And a job well done! made my updates go through automatically making it easy for me just apt-get and I am done :)

Nice work matid :)

---

### Post by gmc on 2005-04-13
Greetings,

    ...of course you could just install **cron-apt** and have it download the updates, then either automatically apply them or wait until you manually install them.

Gord

---

