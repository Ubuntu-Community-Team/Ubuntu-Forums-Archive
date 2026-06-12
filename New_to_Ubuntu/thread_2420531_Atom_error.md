---
title: "Atom error"
date: 2019-06-06
forum: New to Ubuntu
---

### Post by pvsw123 on 2019-06-06
Hello.I have a problem. When I start Atom my computer turns off.I already uninstalled and installed again, did not solve the problem.

---

### Post by Holger_Gehrke on 2019-06-07
Your post is a bit sparse on details ... What version of Ubuntu, what version of atom, is atom installed from a .deb or from a snap, what are the specs of the machine you're running it on  ?
You should take a look at the logs. Either use 'journalctl --since="YYYY-MM-DD HH:MM:SS" --until="YYYY-MM-DD HH:MM:SS"' and substitute a date and time for each of the "YYYY-MM-DD HH:MM:SS" (a few minutes before the crash for --since, a bit after the crash for --until) or look in '/var/log/syslog'.
atom - being an electron application - is extremely hungry for memory. Running it with the [memusg script]("https://ubuntuforums.org/showthread.php?t=2304020") shows that it uses more than 500 Megabytes of RAM just opening and closing it. Even emacs - which is considered heavy for an editor - uses only a tenth of that.

---

