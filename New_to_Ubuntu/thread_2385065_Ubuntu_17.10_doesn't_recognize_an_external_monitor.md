---
title: "Ubuntu 17.10 doesn't recognize an external monitor?"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by luvaix on 2018-02-15
I have an HP Pavilion g4 with an AMD 6 , and I want to connect an external monitor HP w1907 by VGA. Is it possible? In Winodws 10 it works perfect, I don't know why in Ubuntu not. 

Please help, I need it my monitor, I really like Ubuntu. 

Ty

---

### Post by Autodave on 2018-02-16
Have you gone into Settings -> Display and activated it?

---

### Post by frnkln on 2018-02-17
Can you see it when you type xrandr in terminal?

---

### Post by luvaix on 2018-02-20
uhmmm

> **Autodave said:**
> Have you gone into Settings -> Display and activated it?

Do you know how ubuntu 17.10 is? 
If it was so easy I didn't ask here... really!

> **frnkln said:**
> Can you see it when you type xrandr in terminal?

I can see this on the Terminal:

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
XWAYLAND0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 310mm x 170mm
   1366x768      59.80*+

---

### Post by deadflowr on 2018-02-20
To get the displays in 17.10 go to Settings  then go down to Devices, and then open Displays.
The layout can seem a tad convoluted, so take your time figuring it out.
Good luck.

---

### Post by kerry_s on 2018-02-20
you might also want to try logging out & selecting the standard ubuntu with xorg, wayland causes a lot of issues with things not working because of permissions.

i have the hp-pavilion-g6 & could not get hdmi output in 17.10, moved up to 18.04 & hdmi works perfectly, but my only worry is 18.04 is not a release yet. i've had no issues so far.

---

