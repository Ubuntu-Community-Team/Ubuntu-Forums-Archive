---
title: "Can't resize desktop icons."
date: 2013-12-06
forum: New to Ubuntu
---

### Post by bengy103 on 2013-12-06
Now before anyone suggests that there are plenty of solutions online or that if I search the forums I would find answers I've already done that. There are loads of replies that are not what I want and too many for me to check through in my lifetime. The information is buried under information.

My problem.
I have a Unity task bar down the left hand side and the launch icons are enormous. This is a new install of 12.04, with updates, on a Gigabyte GA-970d mobo and a Gigabyte video card. Now the resize function used to be available by right clicking on the Desktop and a slider bar would come up and I could alter it. But that's not available on this set up. I read online that the likely cause is that the 2D desktop version has installed instead of a 3D version. As if I would know what version I've got.

Can anyone tell me a way to alter these icons, bearing in mind that I don't have the little slider?

Can a person double bank the icons so I can get twice as many on the desktop?

regards,

---

### Post by deadflowr on 2013-12-06
Open a terminal and paste this command
```
/usr/lib/nux/unity_support_test -p
```
If any of the out is no, then you are running ubuntu-2d(unity2d), which would explain the lack of resize.

Another, quite simple to see, way to find out is if you have many launcher in the launcher dock already, in unity-3d the launcher will fold like an accordion at the bottom, where as unity-2d will just look as if the icon disappear into a well or bottomless pit, without any design change.
Hard to explain, but when you see it, you know what I mean.

Added: adding this
In the terminal you can see which session is running with
```
echo $DESKTOP_SESSION
```
if ubuntu-2d is running it will be the listed name, if 3d, then it will say ubuntu only, without the -2d.

---

