---
title: "PC freezes and shuts down when resuming from suspend"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by themirror178 on 2012-04-25
I can't seem to resume from suspend on Ubuntu 11.10. When I press the power button (mouse and keyboard can't resume either), a purple screen comes on and I see the cursor (but can't move it), and after about 10 seconds the PC just shuts down.

Running a triple boot of Windows 7, Windows 8 CP, Ubuntu 11.10.

Motherboard is a GB-P67A-UD3R-B3 with an i7-2600k & nVidia GTX 460 (drivers installed for the graphics card). I installed Ubuntu yesterday and have updated everything.

Any ideas why I can't resume from suspend?

Thanks

---

### Post by jtarin on 2012-04-25
I assume you have no problems under Win7or 8?

Here's a [link ]("http://ubuntuforums.org/showthread.php?t=1866858")to contemplate.

---

### Post by themirror178 on 2012-04-25
Thanks a lot mate,

added

```
echo UAR1 > /proc/acpi/wakeup 
echo USBE > /proc/acpi/wakeup
echo enabled > /sys/devices/pci0000\:00/0000\:00\:1d.0/power/wakeup
```

to the file rc.local in /etc using gedit in sudo and worked a treat. Always wakes up from keyboard and mouse too! :)

Since I'm learning, could you explain what adding that did?

---

### Post by themirror178 on 2012-05-03
**[SIZE=3][PROBLEM UNSOLVED][/SIZE]**

Hi sorry to bring this up again. I updated to 12.04 and now about 3 seconds after resuming from suspend and entering my password, the system powers off instantly without any warning or anything. I tried a fresh install of 12.04 and still the same problem!

Any ideas?

Thanks

---

