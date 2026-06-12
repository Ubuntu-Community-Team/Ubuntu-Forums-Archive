---
title: "battery indication can't see"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by abhirajtk on 2011-10-09
i installed ubuntu 10.04 version. on power management i can't see battery option.

on the screen ac power and general option can see but can't see "on battery power".

i think battery power can't detect. how can i solve this?

also in panel i can see a battery indication. from there i couldn't get any information.i want to show current battery level, charging or discharging.&#65279;

 

my system is L650-I5310

 

please help me.

---

### Post by mikejonesey on 2011-10-09
the battery does not show by default anymore... go to power management there is a setting to say always display...

---

### Post by vajorie on 2011-10-10
what's the output of ```
dmesg | grep batt
cat /proc/acpi/battery/*/*
```

I'm thinking you got hit by [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703302"), which has a workaround [here]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html").

---

### Post by abhirajtk on 2011-10-12
abhirajtk@abhirajtk-Satellite-L650:~$ dmesg | grep batt
[    0.692802] ACPI: Battery Slot [BAT1] (battery absent)
abhirajtk@abhirajtk-Satellite-L650:~$ cat /proc/acpi/battery/*/*
present:                 no
present:                 no
present:                 no
abhirajtk@abhirajtk-Satellite-L650:~$

---

### Post by vajorie on 2011-10-14
> **abhirajtk said:**
> abhirajtk@abhirajtk-Satellite-L650:~$ dmesg | grep batt
[    0.692802] ACPI: Battery Slot [BAT1] (battery absent)
abhirajtk@abhirajtk-Satellite-L650:~$ cat /proc/acpi/battery/*/*
present:                 no
present:                 no
present:                 no
abhirajtk@abhirajtk-Satellite-L650:~$

Yup, ubuntu is not seeing your battery at all. try the second link in my above post...

---

