---
title: "graphics"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by teds1931 on 2012-07-04
Hi ,Hope some one can help, after a lot of trouble I have managed to get Ubuntu 10.4 on my fairly old desktop. My problem now is that the screen size of the Ubuntu window is too big to fit the monitor (17inch) there is a inch line above and below the screen and I cant see the slides at either side to move the window. The resolution is 250 X 350 and I can put it to 1200 X 1050 but I cant see the the Apply button at the bottom ,I think if I could change the resolution all would be OK, I have been trying for a while to get Ubuntu and now it dont work. Can any one help. Ted.

---

### Post by papibe on 2012-07-04
Hi teds1931.

By any chance your monitor is a HDTV? If so, you may be experiencing [overscan]("http://en.wikipedia.org/wiki/Overscan"). The easiest solution would be to disable that feature on the TV itself.

Tell us how it goes.
Regards.

---

### Post by NikTh on 2012-07-04
If you are sure about resolution open a terminal and write 
```
xrandr --output VGA --mode 1200x1050
``` 
if fails then run in terminal
```
xrandr
```
to see the available resolutions and set one .

---

### Post by teds1931 on 2012-07-05
Thanks for the quick replys, Papibe, no its not HDTV just a flat screen monitor. NikTh sorry to be a bit thick but what do you mean by open a terminal. Ted.

---

### Post by NikTh on 2012-07-05
> **teds1931 said:**
>  what do you mean by open a terminal. Ted.

Hit Ctrl+alt+t 
copy-paste above commands in there .

---

### Post by teds1931 on 2012-07-06
thanks NikTh. Ted

---

