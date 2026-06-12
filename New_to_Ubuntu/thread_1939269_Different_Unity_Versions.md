---
title: "Different Unity Versions"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by nickelbox on 2012-03-11
Can someone please explain the difference between Unity 2D and Unity 3D? I assume the 3D version is more resource hungry but what else?

---

### Post by howefield on 2012-03-11
Try these links...

[http://en.wikipedia.org/wiki/Unity_(user_interface)#Unity_vs._Unity_2D](http://en.wikipedia.org/wiki/Unity_(user_interface)#Unity_vs._Unity_2D)
[http://askubuntu.com/questions/34913/what-is-the-difference-between-unity-2d-and-unity-3d](http://askubuntu.com/questions/34913/what-is-the-difference-between-unity-2d-and-unity-3d)

---

### Post by critin on 2012-03-11
> **nickelbox said:**
> Can someone please explain the difference between Unity 2D and Unity 3D? I assume the 3D version is more resource hungry but what else?

I run 2D because my nViidia card won't handle 3D. The screen looks the same but 3D effects don't work.  I don't like cubes and stuff moving around the screen anyway, so 2D is good for me.  You can try it by choosing 2D at the log-in page.  Press the gear icon there and choose from the bottom of the screen.  To change back just log-out, change it and log back in.

---

### Post by mcduck on 2012-03-11
> **nickelbox said:**
> Can someone please explain the difference between Unity 2D and Unity 3D? I assume the 3D version is more resource hungry but what else?

It's not necessarily more resource hungry, it simply requires your graphics card & drivers to be able to handle certain things.

...actually if everything works as it's supposed, it's *less* resource hungry, as most of the desktop and user interface drawing tasks are moved from the processor to the GPU, which handles them far more easily and effectively, freeing the CPU to do other tasks. ;)

(of course if the GPU or drivers aren't up to the task, some of the extra effects end being done using your CPU instead, in which case things will get really slow. CPU's are really bad at that kind of work...)

Apart from the obviously missing visual effects stuff, Unity2D is intended to be as close to Unity3D in appearance and functionality as possible. Some things are still missing, but the experience should be more or less the same.

---

### Post by grahammechanical on 2012-03-11
Think of Unity 2D or Ubuntu 2D (its official name) as a fall-back display mode when the video hardware is not capable of running Ubuntu (as Unity 3D is called at the log in screen}.

It makes it possible for Ubuntu to be used on machines that do not have the most recent hardware.

Regards.

---

### Post by nickelbox on 2012-03-11
So does Ubuntu fall back automatically to 2D if your computer cannot handle 3D?

---

### Post by mcduck on 2012-03-12
> **nickelbox said:**
> So does Ubuntu fall back automatically to 2D if your computer cannot handle 3D?

Yes, it does.

---

