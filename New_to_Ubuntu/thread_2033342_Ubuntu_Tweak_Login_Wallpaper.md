---
title: "Ubuntu Tweak Login Wallpaper"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by elang on 2012-07-26
I am using Ubuntu Tweak 0.7.2 on Ubuntu 12.04 32-bit
I tried to change my login screen wallpaper.  In accordance to what I read randomly on the net, I placed my wallpaper in /usr/share/backgrounds/. Let me call that "**L.jpg**")

If I set desktop wallpaper to a static picture (let me call that "**D.jpg**"), the login screen briefly shows L then quickly transitions to D. On the contrary, the login wallpaper L stays till I log on when I put the DESKTOP  wallpaper as the (default) slideshow that is available on 12.04. 

I have not clicked the button in Tweak that links Desktop and Login Screen Background

---

### Post by colin.p on 2012-07-26
Not sure what you are saying, but are you trying to get a certain wallpaper for login, then a different one for the desktop? If that is the case, then all I did was select the login background through ubuntu tweak.
I did it through "tweaks-login settings". I have a login wallpaper, then when I login, a different desktop wallpaper.
I have set up a separate folder called "wallpapers" in home that I linked to.

---

### Post by Frogs Hair on 2012-07-26
The login wallpaper has matched my desktop wallpaper by default in 12.04 without using Ubuntu Tweak . It is possible to make the different but the setting is temporary until the desktop wallpaper is changed. See the las comment at the link. 
[http://helpdeskgeek.com/linux-tips/change-the-ubuntu-12-04-login-screen-using-ubuntu-tweak/](http://helpdeskgeek.com/linux-tips/change-the-ubuntu-12-04-login-screen-using-ubuntu-tweak/)

---

### Post by elang on 2012-07-26
Firstly, thanks for the prompt replies.

Colin, unfortunately your method did not yeild results.

Frogs, I face the same problem as John (2nd comment in [http://helpdeskgeek.com/linux-tips/change-the-ubuntu-12-04-login-screen-using-ubuntu-tweak/#comments](http://helpdeskgeek.com/linux-tips/change-the-ubuntu-12-04-login-screen-using-ubuntu-tweak/#comments)). Still don;t know how to solve it. Even when I change wallpaper, it does not work temporarily.

---

### Post by Frogs Hair on 2012-07-26
This is the final comment in the tutorial section .> One thing to note about this solution is that – unfortunately – it is not persistent. The next time you change your Desktop wallpaper, you’ll find that the login screen background has been changed to match that image, instead of what you just selected. Still, if you don’t change wallpapers too often, this is a solution for the moment, if not a perfect one.



---

### Post by d4m1r on 2012-07-26
You should not need Ubuntu Tweak for this...it is a built in feature of 12.04. I'd recommend removing it, restarting your machine, log back in, change your wallpaper, and then log out and view it at the login page. Worked for me out of the box :)

---

### Post by elang on 2012-07-30
d4m1r,  you mean remove ubuntu tweak?
could you please tell me how to change login wallpaper by default Ubuntu options ??


Frogs,  thanks, did not notice that one. Will let you know how it turns out...

---

### Post by elang on 2012-08-08
Worked like a charm. Also made a pseud-looking logo (transparent background) to replace the default 12.04 logo.
Guess this bug should be cleared in next release of ubuntu tweak

Thanks to d4m1r, Frogs, colin.p and all those who helped

---

