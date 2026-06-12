---
title: "2 Missing features in 11.10?"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by d4m1r on 2012-02-03
Hey guys, I just updated from 11.04 last night I am missing 2 minor features that I'd like help with getting back:

1) Animation when switching workspaces. 11.04 had a blurr effect, 11.10 just shows me my workspaces and an arrow as to which one is currently being displayed.

2) Sound when login screen is displayed (NOT after logged in, which works fine). Before LightDM, 11.04 would play a quick drum-roll sound to let me know my PC is at the login screen...LightDM is completely silent and I don't see anything related to "Login" that I can configure it....

Anyone know what those 2 packages are called or how I can restore that functionality? :confused:

---

### Post by 3rdalbum on 2012-02-04
> **d4m1r said:**
> 

2) Sound when login screen is displayed (NOT after logged in, which works fine). Before LightDM, 11.04 would play a quick drum-roll sound to let me know my PC is at the login screen...LightDM is completely silent and I don't see anything related to "Login" that I can configure it....

Anyone know what those 2 packages are called or how I can restore that functionality? :confused:

For number 2, you can install GDM.

---

### Post by d4m1r on 2012-02-04
> **3rdalbum said:**
> For number 2, you can install GDM.

Won't that cause any conflicts or issue since 11.10 uses Gnome 3.2 already with a unity shell?

---

### Post by grahammechanical on 2012-02-04
That log in sound is now disabled by default. Ubuntu policy. Open the Dash and look for Startup Applications. You may see a line that says Gnome Login Sound. Tick the check box.

This is how it is done on 12.04 which I am testing. My 11.10 install still plays the log in sound. So, I am a bit surprised that it is not playing by default in  your case.

You should also install CompizConfig Settings Manager to have special or enhanced effects. This has not changed since 11.04. Have you activated a proprietary video driver? You may need a proprietary driver to get the effect that you are looking for.

Regards.

---

### Post by d4m1r on 2012-02-04
> **grahammechanical said:**
> That log in sound is now disabled by default. Ubuntu policy. Open the Dash and look for Startup Applications. You may see a line that says Gnome Login Sound. Tick the check box.

This is how it is done on 12.04 which I am testing. My 11.10 install still plays the log in sound. So, I am a bit surprised that it is not playing by default in  your case.

You should also install CompizConfig Settings Manager to have special or enhanced effects. This has not changed since 11.04. Have you activated a proprietary video driver? You may need a proprietary driver to get the effect that you are looking for.

Regards.

Thanks for the tip. The workspace animation came part of the stock 11.04 install though, I didn't have to enable anything...I'll try enabling it using CCSM in 11.10 though.

---

### Post by d4m1r on 2012-02-10
> **grahammechanical said:**
> That log in sound is now disabled by default. Ubuntu policy. Open the Dash and look for Startup Applications. You may see a line that says Gnome Login Sound. Tick the check box.

Thanks but I already enabled it in 11.04 so it was enabled in 11.10. I tried unchecking and rechecking it, but I still don't get a sound when the login screen (lightDM) is displayed :-?

I am pretty sure that is for the gnome sound once logged in anyway, but I am interested in the quick drumroll that used to be played before the user logged in.

Also, no luck on the workspace switching animation for 11.10...Nothing in compiz config or ubuntu tweak had any related options and I've searched both of these issues ***exhaustively***.  It is funny how Google returns me this thread now as a result :rolleyes:

---

### Post by d4m1r on 2012-02-19
Bump...any other ideas? :(

---

