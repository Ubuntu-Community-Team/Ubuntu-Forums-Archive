---
title: "wacom stylus cursor offset problem"
date: 2008-04-07
forum: Programming Talk
---

### Post by anuragkhare on 2008-04-07
Hi All,
I have stylus offset problem.
i would like to explain my problem and machine setup.
Setup:
1- I am using RHEL-4.6 with kernel-2.6.9.67-EL(I can not upgrade kernel).
2- Using wacom.ko which came with kernel.
3- Using wacom cintiq 21UX tablet and setup with TwinView tablet and desktop monitor have 
different resolution.
4- Tablet has 1280x1024 and Monitor has 1152x864 resolution.

5- When Tablet and desktop monitor have same resolution than no offset problem.

Problem:
1- cursor offset problem only inside GIMP and Krita canvas area, outside canvas area 
everything fine.

Test:
1- I built linuxwacom-0.7.8-3/src/2.6.9/wacom.c and hid-core.c with kernel.
Same cursor offset problem i am getting.

Drawing location:               X
Stylus cursor location:                 X


If you need more information ,Please let me know. I am trying to solve this last so many days.

Thanks,
Regards,
Anurag Khare

---

### Post by nanotube on 2008-04-08
i recall seeing a thread about this very issue some time ago... 

aha, here it is (actually... two of them):
[http://ubuntuforums.org/showthread.php?t=696160&highlight=wacom+stylus+offset](http://ubuntuforums.org/showthread.php?t=696160&highlight=wacom+stylus+offset)

[http://ubuntuforums.org/showthread.php?t=496923&highlight=wacom+stylus+offset](http://ubuntuforums.org/showthread.php?t=496923&highlight=wacom+stylus+offset)

read through these and see if they help...

---

### Post by anuragkhare on 2008-04-08
Thanks for reply,
 But i am unable to understand why stylus cursor offset problem only inside application(GIMP, Krita) canvas area while tablet and desktop monitor in TwinView mode have different resolution.


For example:
Tablet resolution: 1280x1024
Desktop Monitor resolution: 1152x864

When both device have same resolution in TwinView than no offset problem.
:-k

Regards,
AnuragKhare

---

### Post by parktownprawn on 2008-04-10
it might have to do with your gimp settings.

go to file>preferences>input devices>configure extended input devices

if the mode "Window" is selected try select the mode "Screen"

this fixed an offset problem i had with gimp but i do not have a plain tablet not an lcd tablet

---

### Post by anuragkhare on 2008-04-11
Hi ,
           I have gone through links and done all changes & replace wacom.ko and wacom_drv.so.
           than remove and load wacom.
           Offset problem has been solved.Thanks

           Problem:
                 I am unable to draw using stylus pen through eraser i can do any thing like erase, draw etc.

            Can you tell the reason behind this behavior is?
 

Regards,
Anurag Khare

---

