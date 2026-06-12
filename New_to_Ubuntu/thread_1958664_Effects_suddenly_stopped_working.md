---
title: "Effects suddenly stopped working"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by CSmiddy on 2012-04-14
Hi everyone!

I've been using Ubuntu for just over a year now and I've really grown to love it! I've recently hit a snag though....It's stopped working. Everything worked fine until about 2 days ago when I turned the computer on and suddenly  it would just freeze randomly, or everything would stop working except for the mouse pointer (I couldn't click on anything but it would still move). I was using Gnome shell at the time but tried Unity as well and it had exactly the same problem. I then tried it in Gnome(no effects) and Unity 2D, both of which worked perfectly fine as far as I could tell, which led me to believe it was a problem with the graphics card. I tried to reinstall/change graphics card drivers but this had no effect. I also tried a fresh reinstall of Ubuntu and still the problem persists (I even tried Lubuntu with Gnome Shell and that freezes as well). Does anyone have any idea why this would have suddenly become an issue when everything worked pretty well until 2 days ago? I can't seem to fix the problem no matter what I do (with my somewhat limited knowledge). Windows is working perfectly fine so it's not a general problem with my graphics card, as I initially feared.I don't know what info will be helpful but here's some of the details of my computer just in case....

OS: Ubuntu 11.10 64bit
Processor: AMD Athlon 64 X2 Dual Core 5600+ (~2.8GHz)
RAM: 4GB
Graphics card: Nvidia GeForce 8800 GTS

Any help would be much appreciated! I much preferred using Ubuntu +Gnome Shell over windows and would really like to go back to using it, sadly Unity 2D/Gnome (no effects) just don't perform in the same way.

---

### Post by theknightlinux on 2012-04-14
Hello, do you know if Update Manager Upgraded the Kernel?

---

### Post by theknightlinux on 2012-04-14
You said you changed your graphics card drivers. Did you also try the post-release drivers from nvidia? My question might sound too obvious, but I just felt the need to ask it.

---

### Post by CSmiddy on 2012-04-15
Thanks for the reply! :-)

I've tried all the drivers that it offered me (there were quite a few on 11.10 but only two offered on 12.04, which I have now installed and still has the same issues) but none of them seem to work. I'm not sure if the kernel has been updated or not, it's running 3.2.0-23-generic which I gather is the latest, but I'm not sure when this was last updated. Should I try downgrading the kernel? If so, how do I go about it?

---

### Post by theknightlinux on 2012-04-15
Yes, it might be an update to the kernel. You said you did a fresh install. Try doing that again, and on the updates prompt on your first system run, do not select the latest kernel update, and lets see if that works.

---

### Post by CSmiddy on 2012-04-16
That seems to have worked! :-) I did a fresh install of 11.10 without connecting it to the internet so it couldn't update itself, then installed all updates except for anything kernel related and everything is working fine. Unity, gnome shell, everything! :-D Thanks for your help!!

I guess this probably means I won't be able to upgrade to 12.04 when it comes out, since it'll come with the new kernel, no?

Thanks again for your help!

---

### Post by theknightlinux on 2012-04-16
I don't know, may be on the next kernel update you should give it a try, that bug might get fixed. Or may be on the next Graphic Card Driver Update the bug might get fixed. When the next video card update goes out, you might try, both, the kernel and the graphics card update and see if both are working smoothly together. And if that'd be the case, you will be able to have 12.04.

---

### Post by CSmiddy on 2012-04-16
ok, well thanks for your help! It's good to have ubuntu up and running again! :-)

---

### Post by CSmiddy on 2012-04-18
Just thought you might like to know....It seems that is wasn't the kernel after all but the Nvidia drivers. I have now updated the kernel and everything works fine, but as soon as I install any of the proprietary drivers it fails to load unity 3D. I've tried all of the drivers available; version 93 won't even load ubuntu at all, it just hangs on a black screen. I guess I'll just have to stick to the nouveau drivers.

---

