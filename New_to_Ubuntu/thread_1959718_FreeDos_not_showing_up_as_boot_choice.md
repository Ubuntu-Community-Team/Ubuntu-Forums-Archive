---
title: "FreeDos not showing up as boot choice"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by Homeground on 2012-04-16
I installed Ubuntu 10.04 alongside Windows XP a few weeks back, then today I shrank the Windows partition by 1 Gb and installed Freedos between them. But it doesn't show up when the boot menu comes up. I've got Ubuntu generic, Ubuntu recovery and Windows XP, but no Freedos. Any ideas?

---

### Post by audiomick on 2012-04-16
open a terminal and try
```
sudo update-grub
```

I think that should do it.  That causes grub to go looking for installs and update it's list.

---

### Post by Homeground on 2012-04-16
^That did it. Thanks for the tip.

---

