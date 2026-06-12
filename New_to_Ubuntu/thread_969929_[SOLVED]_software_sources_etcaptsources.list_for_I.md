---
title: "[SOLVED] software sources /etc/apt/sources.list for Intrepid 8.10"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by nhasian on 2008-11-03
during the upgrade from 8.04 to 8.10 several of my repos for third party software were disabled.

> # deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe
##GeeXboX package repository
# deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main
# deb [http://ppa.launchpad.net/bortis/ubuntu](http://ppa.launchpad.net/bortis/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/bortis/ubuntu](http://ppa.launchpad.net/bortis/ubuntu) hardy main
# deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main
# deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) hardy main


How can I update the software sources for intrepid versions?  Should i just uncomment the lines and change it to say "intrepid main" instead of "hardy main?"

---

### Post by zvacet on 2008-11-03
Yes,and after that 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by niccholaspage on 2008-11-03
Maybe not all the repositories have intrepid in yet. You can try above, But you may get an error.

---

