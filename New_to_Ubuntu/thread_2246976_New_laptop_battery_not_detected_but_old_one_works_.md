---
title: "New laptop battery not detected but old one works fine."
date: 2014-10-04
forum: New to Ubuntu
---

### Post by abilly87 on 2014-10-04
I recently installed ubuntu on my laptop to replace a windows install. The old battery is the original that came with the computer and as such is about six years old. Other than only having 30-45 minutes of charge it works fine. I bought a new battery a few days ago and swapping them the new one isn't detected at all but the old one still works. I don't know that this is related to ubuntu because the laptop won't power on at all when I try with the new battery alone. It seems more like a problem between the battery and the laptop but I could be wrong. I'm new to linux so I don't know much about it. Also, pretty much anywhere else I've looked for a solution made the assumption that windows was the os being used.

Running "cat /proc/acpi/battery/BAT0/info" with the old battery gets:

present:                 yes
design capacity:         6000 mAh
last full capacity:      3104 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 162 mAh
design capacity low:     98 mAh
cycle count:          0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

With the new one it just say not present.

I'm using a pavilion dv9000. I know it's old, I'll replace it someday.

---

### Post by Vladlenin5000 on 2014-10-04
Non-original batteries are often a problem and it has nothing to do with the OS.
A BIOS update, if available, might help but don't keep your hopes high.

---

