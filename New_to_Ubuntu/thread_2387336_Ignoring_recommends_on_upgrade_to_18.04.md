---
title: "Ignoring recommends on upgrade to 18.04"
date: 2018-03-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2018-03-17
In preparation to upgrade my laptop and server, both running 16.04 LTS I have made this change in my /etc/apt/apt.conf.d/ directory. My goal is to not have the upgrade install unnecessary junk when I do my release upgrades in a few months.

[https://superuser.com/questions/615565/can-i-make-apt-get-always-use-no-install-recommends](https://superuser.com/questions/615565/can-i-make-apt-get-always-use-no-install-recommends)

Just want to check to make sure this does what I think it does. Last time I upgraded my server which direct boots to kodi it automatically installed a bunch of unity and gnome junk that I had to remove after the upgrade. I just want the installed packages upgraded, no miscellaneous crap.

---

