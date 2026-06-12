---
title: "Used Computer Janitor and now several programs are malfunctioning..."
date: 2012-12-12
forum: New to Ubuntu
---

### Post by gypsygraver on 2012-12-12
Is there any way I can restore my system to before it screwed things up? The programs I'm having issues with are LibreOffice Impress and Transmission BitTorrent Client. I already tried un-installing them and reinstalling them using the software center but no dice. Any help would be much appreciated!

---

### Post by mastablasta on 2012-12-12
when you uninstall them use the purge command to remove all traces

---

### Post by ibjsb4 on 2012-12-12
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install -f
```

That is a repair command that may help and in the future to clean house use bleachbit, its safe and located in the software center.

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

