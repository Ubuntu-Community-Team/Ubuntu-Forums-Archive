---
title: "Built in display not working"
date: 2019-04-15
forum: New to Ubuntu
---

### Post by ory-garmy1 on 2019-04-15
So I have a Dell Inspiron 3475 AIO I put an SSD in there and loaded ubuntu 18.10. but when I loaded it I had no picture even tho my computer was on. So I tryed to plugging in an external display. And I had video through both. I managed to get through the installation on the external display. I unplugged the external display and I still had video on my internal display. When I restarted the computer I had the same issue so I plugged the external display back in and unplugged it and it worked. I did more testing and found out the external display doesn't need to be powered for it to fix my internal display.

---

### Post by oldrocker99 on 2019-04-15
This sounds more like a hardware problem, unless it works on Windows and doesn't work with Linux.

---

### Post by NM5TF on 2019-04-15
oldrocker99 beat me to it....

did the display work with Windows 10 before you installed Ubuntu ???

---

### Post by ory-garmy1 on 2019-04-17
it works on windows

---

### Post by NM5TF on 2019-04-17
can you post the output of

```
xrandr
```

use code tags to make the output more readable....use the [COLOR="#FF0000"]adv reply button[/COLOR] & post the result between the [COLOR="#FF0000"]#[/COLOR] characters....

it should look similar to mine...

```
 tommy@tommy ~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+
   1366x768      59.79  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```

tommy

---

