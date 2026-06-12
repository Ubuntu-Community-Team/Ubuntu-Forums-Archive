---
title: "Suspend issue"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by Norm24 on 2014-05-10
I just did a fresh install of 14.04 on my laptop and I've selected Suspend "When the lid is closed" under the options for Power and I also selected no password to wake.When I open the lid the screen powers up but it stays blank.For some reason when I do Ctrl-Alt-Delete and then move the mouse pointer around it changes to a cursor in the middle and I can blindly type in my password and then get my wallpaper.I then have to enter my password again to unlock the desktop.

Here's the basic specs:
Gateway ML-6230
2GB Ram
Intel Celeron M 520 (1.60GHz)
512MB Memory 80GB HDD
Intel GMA950

---

### Post by mörgæs on 2014-05-11
14.04 has a number of bugs regarding suspend by opening and closing the lid:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736)

The workaround is to use suspend by pushing the button.

---

### Post by Norm24 on 2014-05-11
> **mörgæs said:**
> The workaround is to use suspend by pushing the button.

That's what I've been doing in the meantime.

Thanks for the reply.I would imagine by the next point release this will be ironed out.

---

### Post by mörgæs on 2014-05-11
Bug fixes are not related to point releases. They appear online whenever they are ready.

The dates for point releases are decided long time in advance. Contents in a point release is whatever has been made available until then.

---

