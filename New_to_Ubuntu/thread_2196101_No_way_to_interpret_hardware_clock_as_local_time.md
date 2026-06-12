---
title: "No way to interpret hardware clock as local time"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by v3ga on 2013-12-27
[COLOR=#333333][FONT=UbuntuRegular]I dual boot windows XP sp3 and ubuntu 12.04.3 LTS. Since windows interprets hardware clock as local time, I want to make ubuntu interpret the hardware clock as local time. But none of the methods I've tried works.[/FONT][/COLOR]

[LIST=1]
[*]First, I edited /etc/default/rcS and set UTC=no. It didn't work.
[*]Then I edited /etc/adjtime and replaced UTC with LOCAL. This too did not work.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]Please suggest any way that works. Thanks.

PS: Sorry, the second method did work and synced the time across windows and ubuntu. I just didn't set the clock after that. Closed[/FONT][/COLOR]

---

### Post by fantab on 2013-12-28
If Ubuntu sees Windows at the time of installation it normally sets itself up at Local Time only. 
I wonder why you had to force Local time....

---

