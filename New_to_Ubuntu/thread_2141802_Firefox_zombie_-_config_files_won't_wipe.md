---
title: "Firefox zombie - config files won't wipe"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by JamButty on 2013-05-03
I have tried many times to completely deinstall Firefox including all configuration files, bookmark files etc., but every time I reinstall, I get it back with all my old setup - addons, bookmarks etc. After deinstalling, there is no trace of any file called firefox (other than within Tor directory), but somehow all the old data is being reinvoked. Where does it get it from and how can I wipe it entirely? I have used both Synaptic and Software Center to deinstall and the result is the same. Using 12.10 quantal .  thanks.

---

### Post by coffeecat on 2013-05-03
Open your home folder and press ctrl-H to shows hidden files. You will see a folder called .mozilla. That contains all your personal firefox configurations.

---

### Post by JamButty on 2013-05-03
Thanks, that did it. I keep un-hiding files and forget it keeps reverting to hidden.

---

