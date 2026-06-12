---
title: "Keyboard layout suddenly changed!"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by pointyblue on 2008-11-04
Hi,

On my Ubuntu 8.04 the keyboard has somehow changed from Danish to English...  :-k

Could someone please help me change it back to Danish again?

Thanks!

---

### Post by Ahunt on 2008-11-04
I think what you are looking for can be selected at System>Administration>Language Support and then select Danish.

---

### Post by InSearchOf on 2008-11-05
This happens to me as well (Ubuntu 8.04, kernel 2.6.24-16), although I have Norwegian as default layout. Almost every day I have to change keyboard layout back to Norwegian from English. (do this in System - Preferences - Keyboard - Layouts). The weird thing though, is that when i go to Layouts, It still says Norwegian as default, (and that is the only language added to the list of layouts). I then have to add another Norwegian layout, and then remove the former layout. Then it works. 

This problem arrived only a couple of weeks ago, and I've been on the same install since 7.10. Never been an issue until now. A problem popping up from what seems like nowhere... 

Any experts out there?

---

### Post by InSearchOf on 2008-11-06
If the problem persists after changing the layout in System - Preferences - Keyboard - Layout, it may be that xorg.conf haven't been configured properly. This was what had happened in my case.

I found that in /etc/x11/xorg.conf there is a section like this: 
-------------------
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection
_________________

The "XkbLayout" "us" defines your keyboard layout - in this case it is set to "us" (=english). I changed this to "no", in my case norwegian, and everything works fine after reboot. Not sure what the equivalent is for Danish keyboards, perhaps "dk"? 
You can edit the file by typing in terminal:
----
sudo gedit /etc/X11/xorg.conf
----
Be sure to make av backup of xorg.conf before editing.

-ISOf

---

### Post by pointyblue on 2008-11-06
I checked and the keyboard layout had somehow changed to US - weird. Anyway, changed it back to Danish and everything seems to work again.

Thanks for helping out!

---

