---
title: "Battery Initially Undetected by xfce-power-manager"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by james_mckay2 on 2014-07-10
Hello!

New to the forums and new to Lubuntu. I've got 14.04 installed on an old Acer Aspire One, with xfce-power-manager running and set to autostart. Problem is that if I startup the laptop unplugged, my battery is unrecognized (it doesn't show up initially in the preferences window). After I plug in, however, the systray icon appears and remains after I unplug from AC power, showing charge remaining, etc; and the battery is recognized.

FYI: I have the power manager set to show icon when the battery is present.

Hope this is clear; I know enough about Linux to fix basic problems on my own, but I'm still a relative noob.

---

### Post by ajgreeny on 2014-07-10
> I have the power manager set to show icon when the battery is present.Have you tried setting that to show all the time instead of when a battery is present?

---

### Post by james_mckay2 on 2014-07-10
Thanks for your reply! Yes, I have tried that setting. It does make the systray icon appear all the time, but it doesn't give any information on whether or not the battery is charging; the power manager still basically thinks I'm running a plugged-in desktop.

---

### Post by bapoumba on 2014-07-11
Prefs > System profiler & benchmark > does it see your battery there ?
Mine says not battery present, but the battery is dead so that makes sense :)

```
upower -e
/org/freedesktop/UPower/devices/line_power_ADP1

```
Should show you where your battery is. As you see, mine is not recognized.
Then running upower -i with the battery file it found previously should show you what the system actually knows. 
```
upower -i /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              ven. 11 juil. 2014 09:09:19 CEST (495 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

```

acpi is not installed here.

---

### Post by james_mckay2 on 2014-07-11
I am now unable to duplicate the problem . . . :confused: My battery's not fully charged, so I'm going to wait until I get a full charge on it and then see if I can duplicate it again. If not . . . problem solved! Somehow.

---

### Post by bapoumba on 2014-07-12
/me invokes *magic* :)

---

