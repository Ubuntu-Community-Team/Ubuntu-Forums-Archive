---
title: "conky configuration"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jlbr on 2008-10-18
hi, I got this conky running on my laptop, and it works fine, except for the battery indicator, when I run conky from the terminal, I get this:
> 
juanluis@juanluis-laptop:~$ conky
Conky: desktop window (12000b6) is subwindow of root window (59)
Conky: window type - override
Conky: drawing to created window (3c00001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

I checked and the reason it cant read the battery status is because the battery is BAT1 and not BAT0 and the file is called "status", not "state"

how could I change this?

---

### Post by BDNiner on 2008-10-18
I believe you change it in the cocky file. Can you post the file here?

---

### Post by sierd on 2009-09-11
```
Battery: $alignr${battery_percent BAT1}%
${battery_bar BAT1}
```

Maybe this will help :P

---

### Post by chauncy22 on 2010-05-26
Thank you! This did the trick for me!:KS
It is know showing percentage in numbers.
Now if I can only get the graph in the bar to show it would be perfect!

---

