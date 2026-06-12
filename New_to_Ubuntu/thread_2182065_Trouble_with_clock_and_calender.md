---
title: "Trouble with clock and calender"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by jayeshsan on 2013-10-20
Hi,

I recently upgraded to Ubuntu 13.10 and then onwards my laptop clock and calender are not working fine. It shows me wrong time and the calender is in my native language. I tried change it in settings and after a reboot it is the same wrong time. Please help

---

### Post by skleist29s on 2013-10-26
Same problem here. After upgrade from 13.04 to 13.10 my BIOS clock is set 2 hours back when I boot Ubuntu 13.10. When I afterwards boot Windows 7 on the same PC the time is 2 hours wrong :-(  The problem did not exist with Ubuntu 13.04.
It seems that starting with Ubuntu 13.10 my BIOS clock is set to UTC when I boot Ubuntu 13.10 instead of local time CET (UTC+2). From today UTC+1 (end of DST).

---

### Post by mishafljin on 2013-10-26
Same problem also. Upgraded to 13.10, calender working fine but clock not. When i go to Date & time settings, shows real time and date in that window, but on desktop menu bar other time :/  Right now clock in menu bar is 10min late.  I don't recall bigger time changes. Either problem started today, or it's here since i've upgraded os.

EDIT: ok, clock in menu bar stopped completely. But the one in date & time settings window is still correct.

---

### Post by vanadium on 2013-10-27
To turn off setting the computer time on UTC, edit /etc/default/rcS and change "UTC=yes" to "UTC=no".

---

