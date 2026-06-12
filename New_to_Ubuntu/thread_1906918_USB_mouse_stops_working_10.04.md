---
title: "USB mouse stops working 10.04"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by dave-o-dave on 2012-01-10
i am running a virtual installation of ubuntu 10.04 using version 4.1.8 of oracle's virtualbox on windows xp. 

I am using a wireless, external mouse and keyboard from logitech. They are connect via USB to some wireless sensor/transmitter. Of course I cannot be sure, but i dont think it is a problem with the external devices as the touchpad shows the same sympthoms as described below.

My problem is that the mouse appears to cut out. 
The cursor is still moveable, but i cannot left click. (right-handed mouse, so left click should highlight). 
The problem begins almost immediately after booting. Some forums said it happens after 5-10 minutes, this is NOT the case for me. It happens after a few clicks. Less than five. after booting it always works once or twice, then soon fails. 

I am able undo the problem sometimes by right clicking on the desktop. This seems to free up the left click function for a few more clicks. Then it freezes again. 

The other interesting point is that in theubuntu guest I cannot Alt+Tab to switch between windows. Alt works and underlines the capital letter of each menu item, but combining with tab, does not flick between windows.

There is no evidence of the problem in the host windows xp. However, only in the virtualbox control window, the mouse does not 'unclick' . If i left click, I have to hit escape for it to be undone. 

So far I have tried the purge irqbalance option, reinstalling packages related to mouse , mdetect, inputattach. 

I tried to adjust the clocksource, but I think this failed. It was set to tsc and I tried to change it to the only alternative, acpi_pm. but unsuccessfully.

Perhaps you guys have some more advice on this. Or an idea on how to check if the steps I took have worked.


Please forgive any silly questions in advance, I am pretty ignorant as far as the guts of linux or ubuntu goes.
Sorry for the long post but I am trying to give plenty of info. 

I am extremely grateful for any help. Please let me know if further info is required.

Thanks in advance

---

### Post by nothingspecial on 2012-01-10
Question moved to it's own thread.

---

### Post by nothingspecial on 2012-01-10
Moved to ABT at OP's request.

---

### Post by dave-o-dave on 2012-01-11
All,

I have continued to look into this problem and would like to correct some of the things I posted earlier. 

Actually I now think this is a hardware problem related to the Logitech wireless optical mouse I am/was using. 

It turns out there were symptoms in windows xp, but they were much less obvious. 
I noticed that if I was working in the main window of firefox, I could not click e.g. to minimize or close the window, without clicking on the desktop first. 

The touchpad was only effected if the mouse is included during power up. If I leave the external mouse out completely, and just use the external keyboard and touchpad, everything is fine. Both in windows and linux. 

I guess the only solution left is to replace the mouse, but I wanted to include this update in case anyone has the same problem or perhaps even an explanation. 

Thanks

---

