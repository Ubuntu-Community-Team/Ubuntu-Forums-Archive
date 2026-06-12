---
title: "OpenGL please help"
date: 2009-05-15
forum: Programming Talk
---

### Post by bubuzzz on 2009-05-15
Hi all, 

I tried to install openGL in my laptop (ubuntu 8.04, inspiron 1420n with nvidia geforce 8400M GS) to complete my assignment. During the installtion it required to install these libraries:

[LIST]
[*]libgl1-mesa-dev
[*]libosmesa6
[*]mesa-common-dev
[/LIST]

and also required to remove these libraries:
[LIST]
[*]libgl1-mesa-dri
[*]ubuntu-desktop
[*]nvidia-glx-new  :cry::cry::cry::cry:
[/LIST]

I didn't realize that it will removed the nvidia-glx-new (how stupid iam )coz at that time, i was doing another assignment. So, after i restart laptop, ubuntu doesn't detect my graphics card and of course it display at the low graphics mode. :mad::mad:

I tried to uninstall all the openGL lib and re- install nvidia-glx-new, libgl1.... again but it doesn't work. Everytime the laptop restart, it give the error message "ubuntu can not detect your graphics card and driver...". I know that this is a known issue of glx-new but cannot find the solution coz i am in week 13 of the semester, lot of stuff to do now. So, anyone, please help coz i really really need my laptop at this time. Thank you very much

---

### Post by alwayshere on 2009-05-15
maybe try 

sudo aptitude install nvidia-glx-new

---

### Post by bubuzzz on 2009-05-15
it doesn't work:icon_frown:

---

### Post by jespdj on 2009-05-16
What do you mean with "it doesn't work"? The screenshot shows that the nVidia driver is activated as it should be?

---

### Post by bubuzzz on 2009-05-16
even the graphics card is enable, everytime i login to the system, i got the message "ubuntu is running the low-graphics mode...". And as you can see from the screenshot, it is in 800x600 screen resolution

---

### Post by jespdj on 2009-05-16
Try deleting your /etc/X11/xorg.conf (or rename it to something else) and run nvidia-xconfig, then log out and back in again.

---

### Post by bubuzzz on 2009-05-17
well, since i just discovered that dell just released the 9.04 dell-ubuntu iso, i already format my laptop and everything is fine now. Driver 180.44 for nvidia graphics card make it run smoother and cooler than ever. However, i still want to install openGL on ubuntu instead of window xp (virtualbox). Can anyone show me another solution for openGL installation? The only way i knew is installing libgl1-mesa-dev which can ruin my graphics card again. Thanks

---

### Post by bubuzzz on 2009-05-17
ok. I can use freeglut with code block now. So cool :D

---

