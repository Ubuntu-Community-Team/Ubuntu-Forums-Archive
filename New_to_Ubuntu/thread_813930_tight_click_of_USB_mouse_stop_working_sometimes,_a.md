---
title: "tight click of USB mouse stop working sometimes, any solution?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by legolas_w on 2008-05-31
Hi 
Thank you for reading my post
I have usb mouse and Ubuntu 8.04, my mouse right click stop responding sometimes and it really annoy me specially that it does not fix when I restart the computer.


After sometimes and without any reason it start working and maybe it stop again.

Is there any way to work this out?

for example reloading the driver, the module, ...?


I never had this problem in 7.10.

Thanks.

---

### Post by quelx on 2008-05-31
next time it stop working run **xev** in a terminal, move the white box that appears someplace you can see it and the terminal where all the buttons/location codes are flying accross the screen.  Put the mouse in the **xev** box and don't move it, right click.  You should see something like

```
ButtonPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x1a6, subw 0x0, time 98760123, (81,138), root:(1325,533),
    state 0x0, button 3, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x1a6, subw 0x0, time 98761234, (81,138), root:(1325,533),
    state 0x400, button 3, same_screen YES
```

If you don't then there may be something wrong with the mouse itself...  Do you have a different mouse you can try?

---

### Post by legolas_w on 2008-05-31
Thank you for reply.
I dont have any other mouse to test as it never happens in windows and never happend in Gutsy , I thought there should be some problem with hardy and my mouse.

Any solution which help me reload the mouse module? maybe reloading the module could help.

thanks

---

