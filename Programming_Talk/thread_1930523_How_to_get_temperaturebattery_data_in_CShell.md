---
title: "How to get temperature/battery data in C/Shell"
date: 2012-02-23
forum: Programming Talk
---

### Post by idedTea on 2012-02-23
Hello,

I'm interested in making a small C/Shell command line utility to display information about computer temperature and battery life. 

I am pulling my hair out trying to find example code or information on how to do this online. Can anyone point me in the right direction?

Thanks!

---

### Post by ofnuts on 2012-02-24
The info you need is likely somewhere under /proc. On my computer:

```

>>>cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      6549 mAh
present voltage:         12376 mV

>>>cat /proc/acpi/thermal_zone/THM0/temperature 
temperature:             46 C

```among other things. The full ACPI spec is [here]("http://www.acpi.info/") but it doesn't tell how this maps to /proc/acpi even if most of it can be guessed. You will also find moderately outdated info in the [original sourceforge project]("http://acpi.sourceforge.net/documentation/").

---

### Post by alegomaster on 2012-02-24
You may find this thread interesting. It has a bash script which displays the battery. I believe some modification is needed, but that is the best thing I could find. 

[linky]("https://bbs.archlinux.org/viewtopic.php?id=1809")

---

### Post by doobrie on 2012-02-25
> **idedTea said:**
> Hello,

I'm interested in making a small C/Shell command line utility to display information about computer temperature and battery life. 

I am pulling my hair out trying to find example code or information on how to do this online. Can anyone point me in the right direction?

Thanks!

Hi,

I've written a small C++ app that gets the battery state and displays it in a window.  You may find the code interesting and it should be fairly easy to understand.  You can get it from:

[https://github.com/doobrie/battery-status/](https://github.com/doobrie/battery-status/)

---

