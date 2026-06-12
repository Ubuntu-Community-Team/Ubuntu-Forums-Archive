---
title: "Hardy Penryn High CPU Load"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Marsonis on 2008-06-10
Hello.  I have been using Ubuntu for about a year now, and I really like it.  It worked just fine on my old laptop, but I am having some issued with Hardy on the new laptop.  The problem is that desktop effects is very slow (to the point that I have turned it off completely) and the CPU load when I am doing nothing is from 40% to 60% continuously.  When I typed top in the terminal, Xorg and npviewer.bin were almost always at the top of the list for CPU usage.  

This laptop has an Intel Penryn T8300 processor and an nVidia GeForce 8600gt video card.   

Does anyone know why Hardy is using so much processing power when it is doing nothing?  My old laptop was far less powerful and it did not use nearly as much when it was running Gutsy.  If you need any more information, please let me know.  Thanks!

---

### Post by sdennie on 2008-06-10
npviewer means Adobe Flash.  It always uses huge amounts of CPU on linux and the only way to really prevent that is to simply not go to websites with flash (or disable flash with the Firefox NoScript plugin).

As for desktop effects going slowly, on a laptop with nvidia, this is almost always caused by something called PowerMizer.  This has been a longstanding problem with nvidia laptops (think, years) but, there are workarounds that usually work.  The one I use can be found here: [http://ubuntuforums.org/showthread.php?t=747294](http://ubuntuforums.org/showthread.php?t=747294)

---

### Post by Marsonis on 2008-06-11
Thanks for the reply.  I'll try that and let you know how it works out.

---

