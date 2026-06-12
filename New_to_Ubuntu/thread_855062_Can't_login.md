---
title: "Can't login"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by CrunchbiteJr on 2008-07-10
Completely new to this Ubuntu thing but am needing help. Burned the iso onto a disc and installed it on my PC over Windows (which I'd finally lost patience with) and all was fine. When I try and log in though I get the noise that I've logged in correctly then the screen goes black and I get booted back to the login page. I can log in using Failsafe Gnome so I went in and installed libpam_smbpass.so but it hasn't helped. Anyone have any suggestions?

I'm running an AMD sempron with 512mb ram and ample hard drive space for Ubuntu.

---

### Post by TenPlus1 on 2008-07-10
It could be a problem with one of the startup programs in Gnome causing it to return to the login screen...  Pop into gnome-failsafe and disable the srevices/sessions you dont need (things like bluetooth, tracker etc.) and see if that works...  Otherwise you could ask synaptiv to re-install ubuntu-desktop and see if it fixes the error...

---

### Post by CrunchbiteJr on 2008-07-10
Oh, nevermind. Got it. When I activated some ATI drivers it started working.

---

### Post by fatality_uk on 2008-07-10
Nice one. Could you mark the thread as sovled please?
Cheers

---

