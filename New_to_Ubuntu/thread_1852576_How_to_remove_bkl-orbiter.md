---
title: "How to remove bkl-orbiter ?"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-09-30
I want to stop bkl-orbiter from running at startup.

However, I would like to start it whenever I choose to.

I tried:
(from another thread)
root@MusicStation> update-rc.d bkl-orbiter remove                     ~/scripts  Removing any system startup links for /etc/init.d/bkl-orbiter ... root@MusicStation> update-rc.d bkl-investigator remove                ~/scripts  Removing any system startup links for /etc/init.d/bkl-investigator ... root@MusicStation>
But it is not working i.e. bkl-orbiter runs whenever I boot Ubuntu. How should I prevent it from starting but still be able to run it whenever I want to?

---

### Post by An Sanct on 2011-09-30
Which version of Ubuntu are you using?

---

### Post by RobikShrestha on 2011-09-30
I am using 11.04

---

### Post by RobikShrestha on 2011-11-16
I did it by uninstalling bickley-daemons from synaptic manager.

---

