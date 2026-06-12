---
title: "Xbox360 gamepad emulator (other gamepad being recognized as xbox360 gamepad)"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Silesius on 2012-01-19
So I'm pretty new to Ubuntu and Linux in general but I'm quite enjoying it so far.

I do have one question I would like to make, is it possible to have my Sixaxis gamepad recognized as Xbox 360 gamepad? Reason being newer games auto detect the gamepad that way and some only accept xinput gamepad.

This program [http://www.motioninjoy.com/](http://www.motioninjoy.com/) that I used to use in windows does that, is there anything similar to it for Ubuntu? Or rather something that would do the trick...

Thank you for your time.

---

### Post by Grumbel on 2012-02-07
> **Silesius said:**
> I do have one question I would like to make, is it possible to have my Sixaxis gamepad recognized as Xbox 360 gamepad? Reason being newer games auto detect the gamepad that way and some only accept xinput gamepad.
Yes, that is possible with xboxdrv:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

There are however a few pitfalls:

1) I assume you want to use the gamepad in Wine, this works, but requires some additional [hacks in Wine](http://groups.google.com/group/xboxdrv/browse_thread/thread/c20634b29f9dac3f/5b84037bf20b7f15?#5b84037bf20b7f15), as Wine doesn't nativly support Xinput, which games using Xbox360 need

2) xboxdrv only supports the Sixaxis via USB, not wireless.

3) Linux itself doesn't have any standard conventions for controller layouts, even the Wireless and Wired versions of the Xbox360 controller are handled differently, so you will have to remap your controller in most games to have it work properly.

---

