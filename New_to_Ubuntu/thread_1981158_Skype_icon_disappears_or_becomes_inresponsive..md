---
title: "Skype icon disappears or becomes inresponsive."
date: 2012-05-16
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-16
Hey guys, so this has been an issue from the start for me when I did a clean install of 12.04....I have Skype 2.2 installed which I believe is the latest version and is the one advertised on Skype's official website but basically, the blue Skype icon at the top of my menu bar, only works for the first few minutes after Skype is launched. Randomly later, it either disappears or just does nothing when you left or right click on it :confused:

Is this happening to anyone else? Does anyone know how to fix this?

---

### Post by sudodus on 2012-05-16
I have recently used the following link to make Skype work in Lubuntu 12.04. [[COLOR="Red"]_http://askubuntu.com/questions/119306/skype-wrapper-on-ubuntu-12-04_[/COLOR]]("http://askubuntu.com/questions/119306/skype-wrapper-on-ubuntu-12-04")

It seems that skype-wrapper get stuck in an infinite loop, but after reboot Skype is working as it should. (And you don't need skype-wrapper after the installation.)

---

### Post by d4m1r on 2012-05-16
I'm not looking to integrate it with the default messaging icon (aka skype-wrapper), it is the standalone and Skype specific icon in my menu bar at the top that disappears or becomes unresponsive :(

---

### Post by xedi on 2012-05-16
Did you install skype by getting the .deb from the skype homepage or by getting it in the software-center? I had the problem that in the case of the former the skype indicator was not appearing at all in the panel and read from others who had the same problem. This is not a problem with the skype version which you get in the software-center so it might be worth trying that one out (in case you are not using it already).

---

### Post by d4m1r on 2012-05-16
> **xedi said:**
> Did you install skype by getting the .deb from the skype homepage or by getting it in the software-center? I had the problem that in the case of the former the skype indicator was not appearing at all in the panel and read from others who had the same problem. This is not a problem with the skype version which you get in the software-center so it might be worth trying that one out (in case you are not using it already).

I installed the .deb availble from Skype.com but I guess I'll try the one in the software centre instead...

---

### Post by DaveDeviant on 2012-05-16
Before you install skype go to **Software Sources**, on the second tab which is called **Other Software** mark the options to be on from **Canonical Partners** and **Canonical Partners (Source Code)**. Close it and now you can install skype without any problem and will work for sure.

Good luck,
Dave

---

### Post by d4m1r on 2012-05-16
> **xedi said:**
> Did you install skype by getting the .deb from the skype homepage or by getting it in the software-center? I had the problem that in the case of the former the skype indicator was not appearing at all in the panel and read from others who had the same problem. This is not a problem with the skype version which you get in the software-center so it might be worth trying that one out (in case you are not using it already).


Thanks for the recommendation, it fixed the problem :cool:

It's weird because the .deb offered on Skype's official website is the exact same version offered in the Software Centre, but the one in the Software Centre has a much better functioning system tray icon...

---

### Post by DaveDeviant on 2012-05-16
> **d4m1r said:**
> Thanks for the recommendation, it fixed the problem :cool:

It's weird because the .deb offered on Skype's official website is the exact same version offered in the Software Centre, but the one in the Software Centre has a much better functioning system tray icon...

It's all related to that Canonical Partners stuff. When I was new to Ubuntu, I installed skype, had the same problem and I was ready to stop using Ubuntu for that as I needed skype for work too. A friend helped me with this simple and useful advice and everything worked like a charm.

Glad that your problem is resolved.
Welcome

---

