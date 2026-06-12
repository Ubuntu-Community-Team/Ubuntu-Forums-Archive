---
title: "How to update logitech usb mouse driver? (double click problem)"
date: 2020-11-11
forum: New to Ubuntu
---

### Post by wugutech on 2020-11-11
When I first had fresh install of Lubuntu 20.10, I see my mouse working fine,
then sometime (if im correct) after using second monitor for extending display (was using it as duplicate display),
after that i guess it started to have double click problem,

i did try to re adjust "double click interval" milliseconds in keyboard and mouse settings, but that doesnt help,

How to update logitech usb mouse driver?
How to restart this driver?
Can I use different mouse driver? How? I use Logitech M310t

Thank you,

---

### Post by Impavidus on 2020-11-12
Can you use the **xev** tool to test your mouse? Run it from a terminal. It will open a small window. Click in the window and monitor the output in the terminal. On my computer it says```
ButtonPress event, serial 34, synthetic NO, window 0x5400001,
    root 0x13e, subw 0x0, time 14080051, (176,79), root:(770,384),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x5400001,
    root 0x13e, subw 0x0, time 14080114, (176,79), root:(770,384),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 34, synthetic NO, window 0x5400001,
    root 0x13e, subw 0x0, time 14080218, (176,79), root:(770,384),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x5400001,
    root 0x13e, subw 0x0, time 14080282, (176,79), root:(770,384),
    state 0x110, button 1, same_screen YES
```This means I clicked and held button 1 (the left button) for 63 milliseconds, then released it for 114 milliseconds, then clicked again, holding it for 64 milliseconds before releasing again. That's a typical double-click event.

I my experience, simple usb mice of whatever brand just work. They don't need separate drivers as they're highly standardised and well supported by the kernel. Might it be hardware failure, dirt or a bad battery?

---

### Post by Autodave on 2020-11-12
Or try the receiver in a different port.

---

### Post by ActionParsnip on 2020-11-12
A USB mouse is a USB mouse, just like in Windows. There are no specific drivers...just like in Windows.

---

### Post by wugutech on 2020-11-12
by using xev that i can detect unwanted double click events but my eyes have to catch them, is that correct? 
it seems the problem goes away after I change it to different usb port, and go back to usual port also normal now, so I guess its a port thing, may be just simply unplug and replug....

Thank you all,

---

