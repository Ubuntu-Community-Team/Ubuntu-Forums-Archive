---
title: "mouse accelleration"
date: 2016-08-19
forum: New to Ubuntu
---

### Post by cytg on 2016-08-19
Is it true that I have to terminal and edit X config to get rid of mouse accelleration perm? There is an applet for mouse settings right there.. Why is there not a slider for accelleration? Seems like a no-brainer?

---

### Post by cytg on 2016-08-19
[https://ubuntuforums.org/showthread.php?t=1734400](https://ubuntuforums.org/showthread.php?t=1734400)

<- this is retartracted.. I coulda but dont want to. 16.04 and I still have to google a solution for every little thing.

---

### Post by grahammechanical on 2016-08-19
I do not know what operating system you are using. It cannot be Ubuntu 16.04 because in System Settings>Mouse & Touchpad there is a slider to set the mouse pointer speed.

The default setting is half way between slow & fast.

---

### Post by cytg on 2016-08-20
And thats different from mouse acceleration. speed<>accel.
It doesnt feel mature. I just woke the system up, I have two screens setup and one (1080p) wakes up faster than the other (4K). Result is that my main screen (4K) scrolls all of a sudden (with the extend to the 1080p I would imagine). I have to log out and log in again... Doing that resets my positioning of the screens again, so I have to go back in and flip em manually again. Wh00t? :).
Also, installing the nvidia driver gets me accelleration however the 1080p is now detected as a CRT with max res of 1360x768. no way around it.
Again I am sure I can get around it going into x11 myself.. but I have to ask myself at what point do I just fall back to like gentoo again! (as win10 is NOT an option besides as a steam machine.)
Having to log out and in again so far is a deal breaker.

So, if i power off the 1080p before waking the system, it works.. I can then repower it back on afterwards and it will be as it was..
However, coming back from sleep "Files" i had open would be non responsive, another app as well.. Have to go into system-monitor and kill the task. Nice.

edit : can it be that much of this is based in Unity?

Coming out of sleep kills anything Flash you might have had going on in firefox. Sorry, kills the browser. Back to system tools to kill stuff off :) Nice.

---

### Post by Geoffrey_Arndt on 2016-08-21
Maybe this article will help do a workaround:   [http://www.webupd8.org/2016/08/how-to-completely-disable-mouse.html](http://www.webupd8.org/2016/08/how-to-completely-disable-mouse.html)

---

### Post by cytg on 2016-08-21
Thanks. Yea I found that, will def have to be done. Think I am gonna try out Mate too though I have a sneeking suspicion that much of what I am not happy with is tied to Unity. On the other hand I read that Mate is not really 4K ready.. arrgh

---

### Post by Geoffrey_Arndt on 2016-08-21
Cytg . . . because of the power of the command line interface & bash shell, it's not likely the fine grained gui tools you prefer will be available in mos linux distros.   

The closest to it is not Mate or another Ubuntu derivative, but OpenSuse with Yast (imho).

---

