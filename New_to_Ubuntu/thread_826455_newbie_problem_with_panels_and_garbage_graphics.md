---
title: "newbie problem with panels and garbage graphics"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by rptan2000 on 2008-06-11
Hi,

I just finished installing Ubuntu 8.04 on my laptop.

At first glance it looks okay, but the panels and the taskbar seem to be problematic. The system correctly set my screen resolution to 1280x800 but the panels don't seem to follow and are stuck at 800x600? I've already set them to auto-expand but they don't want to expand to the length of the screen. Other programs work well and when maximized take over the entire 1280x800 screen, but the panel and toolbars stay stuck.

Also, when I open windows there seem to be garbage fragments leftover on the screen which you need to wipe out by dragging a window over them!

Please see attached screenshots for more details...
Hope you guys can help me with my problem!

Thanks!
Ryan

---

### Post by Yuki_Nagato on 2008-06-11
Because you said you just finished installing, have you run updates and all that junk yet?  I would have Synaptic check for any bug fixes, and then completely restart Ubuntu.

```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by stalkier on 2008-06-11
> **Yuki_Nagato said:**
> Because you said you just finished installing, have you run updates and all that junk yet?  I would have Synaptic check for any bug fixes, and then completely restart Ubuntu.

```
sudo apt-get update

sudo apt-get upgrade
```

I agree, should do updates then see if it is a problem. It is probably just a bug in app.

---

### Post by sistoviejo on 2008-06-12
Congratulations on being the 600,000th user registered on the forum. :lolflag:

[http://www.mikesplanet.net/2008/06/600000_users/](http://www.mikesplanet.net/2008/06/600000_users/)

---

### Post by rptan2000 on 2008-06-12
Wow. I never knew I was member number 600,000... thanks for the heads up, Sistoviejo! Well, there goes my 15 seconds of fame! :P 

As for my problem, thanks for the suggestions guys but I tried updating and the problem still persists. I made a mistake assuming that it is stuck at 800x600, it's actually 1024x768... but I need it to expand and take up the entire 1280x800. Also, the login screen exhibits the same problem of being limited to 1024x768... although I can't take a screenshot of it.

Can this be caused by my graphics card being an integrated Intel GM965 Graphics Media Accelerator? I've heard that Ubuntu and Linux have problems with this graphics card, although 8.04 should have fixed most of them? As for the garbage, can it also be caused by the video card being weak?

Well I kinda got stuck with a black screen after login when I tweaked some settings (I think I tried to restart it under 1024x768 resolution) so I'm doing a fresh install right now and updating everything again.

Again, hoping for any suggestions on how to tackle this problem...

Thanks!

---

### Post by rptan2000 on 2008-06-15
Found the problem, quite stupid though. Sorry for the trouble.

It seems Ubuntu detects two monitors even if it is just a laptop. Maybe for the VGA port? Anyway, I just disabled the smaller one via the screen resolution tool and it works fine now. Although I haven't tried how it would behave via VGA port.

Anyway, thanks for those who took the time to read and help.

---

