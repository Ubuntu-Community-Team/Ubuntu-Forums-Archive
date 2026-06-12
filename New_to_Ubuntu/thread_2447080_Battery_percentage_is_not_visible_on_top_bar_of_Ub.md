---
title: "Battery percentage is not visible on top bar of Ubuntu 20.04 LTS for Surface Pro (Su"
date: 2020-07-12
forum: New to Ubuntu
---

### Post by facelessgreyhat on 2020-07-12
I  have done a fresh installation of Ubuntu 20.04 LTS on Surface Pro  (Surface_Pro_1796) and it seems like there is some issue with battery  percentage which supposed to be displayed on top bar of GNOME desktop.  Did some research on this and tried the following without any success:


[LIST=1]
[*]I have no entry for battery under these directories /proc/acpi/battery or /sys/class/power_supply
[*]Ran **acpi -b** command - no output.
[*]Installed **GNOME Tweaks** and tried to enable batter percentage but it didn't help.
[*]Installed Linux Surface, but it didn't help as expected since I  don't see Surface Pro in the list of supported devices, but gave a try.
[*]Installed GNOME extension **Vitals** but it doesn't show any data of battery.
[/LIST]
 Any help on supportability of this Kernel for battery would be appreciated on Surface Pro.

---

### Post by kc1di on 2020-07-12
I can't be of help really.  But gnome tweaks works here no Problem.  May try rebooting see if that will work with gnome tweaks. Good luck.

---

### Post by facelessgreyhat on 2020-07-12
> **kc1di said:**
> I can't be of help really.  But gnome tweaks works here no Problem.  May try rebooting see if that will work with gnome tweaks. Good luck.

Rebooted multiple times, didn't help. Can you please loop somebody who can help me on this or atleast guide me as how to troubleshoot this issue ?

---

### Post by facelessgreyhat on 2020-07-16
Finally after doing lot of research and experiments I was able to solve this issue, check this for more info : [https://github.com/jakeday/linux-surface/issues/666]("https://github.com/jakeday/linux-surface/issues/666?fbclid=IwAR2jWkM8-ORrKJxytFFOquwDnScGdvwEViucGQe9PprMICJnOiy9e7bG4hc")

---

