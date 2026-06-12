---
title: "Synaptic Updater problems"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Pnkmaggt on 2008-04-27
I just had a serious comp meltdown and had to start over from scratch.  After checking off all the options in my software sources I went into my synaptic updater and tried to install all of the upgrades.  But, not only will in not use the "mark all upgrades" button, but if i try and select all of them with a shift+click kind of thing, the program freezes and wont start back up without a system reboot.

Any suggestions?

P.S.  me = noob!

ty!

---

### Post by fredwilby on 2008-09-20
Did you Refresh after?

You Could try

```
sudo apt-get update
sudo apt-get upgrade
```

from the command line and post any errors

---

### Post by zvacet on 2008-09-20
After you click on **mark all upgrades** try to click on **apply**.or in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

