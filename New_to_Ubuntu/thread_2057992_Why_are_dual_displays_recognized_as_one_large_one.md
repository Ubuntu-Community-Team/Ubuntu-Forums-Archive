---
title: "Why are dual displays recognized as one large one?"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Kurasu1415 on 2012-09-14
So, I have two monitors. I set up dual monitors using the Nvidia configuration tool. They work fine, except that they are considered one monitor that is just my two resolutions added together.

I can't have it work this way, because I need to map my Wacom tablet to one of the screens. Does anyone know how to solve this issue?

Thanks.

---

### Post by Jeremy Davison on 2012-09-14
Forgive me if I sound silly, I just want to clarify, the system sees the two monitors as a single one, and its not just mirroring displays? I know I have had that as an issue before. 

I think I remember reading an article on this issue before though. I'll see if I can find it for you.

---

### Post by Kurasu1415 on 2012-09-14
Yeah, The displays aren't mirrored, they are extended. I have never had an issue like this, and it just showed up when I moved to 12.04 (fresh install, not update). I appreciate the help.

---

### Post by Favux on 2012-09-14
Hi Kurasu1415,

That's just how Nvidia TwinView works.  Luckily the Linux Wacom developers figured out how to support the Nvidia proprietary driver with MapToOutput.  So you should be good.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)

---

### Post by Kurasu1415 on 2012-09-14
The problem here is that they are mapping the tablet to a monitor via device ID. If I do Xrandr I only get one monitor back, which is both combined. 

```
Screen 0: minimum 3840 x 1080, current 3840 x 1080, maximum 3840 x 1080
default connected 3840x1080+0+0 0mm x 0mm
   3840x1080      50.0*
```

---

