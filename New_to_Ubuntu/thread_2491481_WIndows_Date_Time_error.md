---
title: "WIndows Date Time error"
date: 2023-10-10
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-10-10
windows time error, so on Linux its show the correct time, but when i reboot to windows or boot to windows. The time will change.
so everytime i boot to windows, i must manually re-sync the time.  Even the auto-time zone are enable.

---

### Post by Xian on 2023-10-10
Might take a look here: [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

---

### Post by TheFu on 2023-10-11
Both Windows and Linux use the same clock that is powered by the CMOS battery in most computers.  That clock is setup either in the old MS-DOS way, with local time and a timezone or with UTC time and a timezone.  Unix system have been using UTC time basically forever, since they need to communicate world-wide and have been doing that since the early 1970s.

So, what you need to do is to pick which time you want your BIOS to use, then tell all the OSes that you run which it is.  I'd say to go for UTC and tell MS-Windows to use that.  I think that has been possible about 20 yrs, but IDK. Some references:
[LIST]
[*][https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)
[*][https://ubuntuhandbook.org/index.php/2021/06/incorrect-time-windows-11-dual-boot-ubuntu/](https://ubuntuhandbook.org/index.php/2021/06/incorrect-time-windows-11-dual-boot-ubuntu/)
[*][https://answers.microsoft.com/en-us/windows/forum/all/dual-booting-windows-10-linux-can-i-tell-windows/a9914172-c857-451f-882f-cb06325eb39d](https://answers.microsoft.com/en-us/windows/forum/all/dual-booting-windows-10-linux-can-i-tell-windows/a9914172-c857-451f-882f-cb06325eb39d)
[/LIST]

---

### Post by rifqilubis on 2023-10-11
thanks for all your answers. really appriciate it

---

