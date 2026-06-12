---
title: "radeon hd4250 drivers"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by opfeld on 2014-02-09
I recently installed the new xubuntu 13.10, without realizing that amd discontinued support for my amd hd4250 graphics card and it sounds like xorg was also updated and so legacy drivers are also out of the question.  I don't mind using the open source drivers but right now the resolution is correctly set on the tv it is plugged into but the picture goes off the screen, I am not seeing anything in the settings to fix this, anyone have any help?

---

### Post by QIII on 2014-02-09
Hello!

Sometimes the man pages are more inscrutable than the problem you are trying to solve -- they baffle me sometimes!  It's sometimes as if you can only understand them if you know the answer to the question you are asking already...

Anyway, try looking through

```
man radeon
```

to see if you can find something.  If you do, don't run off and try a bunch of things half-understood.  Find what you think might be the general direction and come on back and ask questions if you can't sort it out BEFORE you cobble up your machine.  Look for things like overscan, underscan and resolution.

I don't know if any of the references at the bottom of [this]("https://help.ubuntu.com/community/RadeonDriver") will help or not.

We'll be here.

Best wishes!

---

### Post by opfeld on 2014-02-10
[http://www.makeuseof.com/tag/should-you-use-amd-proprietary-graphics-drivers-how-do-you-install-them-ubuntu/](http://www.makeuseof.com/tag/should-you-use-amd-proprietary-graphics-drivers-how-do-you-install-them-ubuntu/)

I was able to get the proprietory drivers to work using the advanced section of this site, not sure what the problem was with the open drivers that could get my screen size right.

---

