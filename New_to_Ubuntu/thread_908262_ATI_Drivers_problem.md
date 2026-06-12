---
title: "ATI Drivers problem"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by bob74 on 2008-09-02
I installed an ATI X1300 card and everything ran OK until I tried to apply the accelerated graphics which promptly screwed up my graphics. I did a system repair and Xfix and now have graphics but when I try the resolution change I get the message "the xserver does not support the xrandr extension. Runtime resolution changes to the display size are not available"
Originally the radeon x1300 and display were recognised and there was a choice of many resolutions. Now I appear to be stuck with what looks like 800x600, useable but useless for some applications. The irony is that I have put in the ATI to replace the nvidia 6100 which I couldn't get to work correctly, after many hours of effort and thread perusing.
Can some kind person please, in the simplest terms possible, give me some guidance.
Thanks, bob74

---

### Post by aimpau on 2008-09-02
Open Terminal and

```

gksu displayconfig-gtk

```

Also you may want to visit this:
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by bob74 on 2008-09-03
aimpau
Thanks for suggestions
Now sorted but I have another problem. When I log out to access another desktop the options screen is partly out of window and therefore cannot choose new session and therefore I have to go back to ubuntu. I cannot find any way of re-positioning this particular screen. Any ideas please?
Thanks again
bob74

---

### Post by aimpau on 2008-09-04
ah...i had the same problem as before. The screen of the login differs from the screen of the desktop. bear with me whilst i research on this again. also, i hope some would also be able to help.

---

