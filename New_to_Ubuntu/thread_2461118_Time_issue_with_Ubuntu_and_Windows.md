---
title: "Time issue with Ubuntu and Windows"
date: 2021-04-24
forum: New to Ubuntu
---

### Post by danezeq2 on 2021-04-24
i've just installed Ubuntu and every time i switch between them the clock is moving 3 hours ahead.
they both set to the same time zone. 
A much as i understand the bug is within Ubuntu and not Windows because i can see right after closing Ubuntu that the time has been changed on the boot setup menu.

I've tried to turn off automatic time update, didn't help either.

---

### Post by Bashing-om on 2021-04-24
danezeq2 ; Well -

Thing is that Windows expects time as "local" whereas linux does UTC.

See: [http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/](http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)
for a resolution.

[INDENT][INDENT]-ways to beat Windows-[/INDENT][/INDENT]

---

### Post by coley9225 on 2021-04-24
When I first started using a linux system, I had the same problem. The suggestion I got, which solved my issue, is ,in a terminal, run '[COLOR=#000000] [/COLOR][COLOR=#000000]sudo timedatectl set-local-rtc 1 --adjust-system-clock'. That  should get your time troubles fixed.[/COLOR]

---

