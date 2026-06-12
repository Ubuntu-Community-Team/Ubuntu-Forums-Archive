---
title: "What is this?"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by morgan4 on 2013-09-30
There isn't anything wrong with my system (at least that I can tell) but something happens upon boot that makes me curious. 

Before the purple Ubuntu screen with the loading orange dots, my screen turns black and there is white text. The text is only about 6 lines long, each stating DRM and then what the DRM is for, such as something about Intel and something else. 

Why would DRM be showing up before booting Ubuntu? Doesn't make sense to me.

---

### Post by steeldriver on 2013-09-30
The messages are probably about loading the drm kernel module(s) (i.e. kernel support for accelerated graphics)

[http://en.wikipedia.org/wiki/Direct_Rendering_Manager](http://en.wikipedia.org/wiki/Direct_Rendering_Manager)
[http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)

```

$ lsmod | grep drm
drm_kms_helper         22738  1 i915
drm                   146387  2 drm_kms_helper,i915
i2c_core               19116  5 i2c_algo_bit,drm,drm_kms_helper,i2c_i801,i915

```

Nothing to do with digital rights - if that's what you were thinking.

---

### Post by morgan4 on 2013-09-30
I will compare this to what loads up on my computer. 

I was thinking it had to do with digital rights. Which seemed odd. This makes much more sense.

---

### Post by grahammechanical on 2013-09-30
Direct Rendering Manager (DRM)[URL="http://www.phoronix.com/scan.php?page=news_item&px=MTI5NTk"]

http://www.phoronix.com/scan.php?page=news_item&px=MTI5NTk[/URL]

---

### Post by tgalati4 on 2013-09-30
While booting, hit esc or Alt-F1 to see the messages.  It's similar to the smoke you see out of the tailpipe when you start your car in the morning.  It's annoying, goes away quickly, and doesn't seem to affect operation.

---

### Post by gordintoronto on 2013-10-01
Do you have a phone (or other device) which can record video? If you record the boot sequence, you can play it back using VLC media Player, which lets you slow down playback so you can pause and read what it says.

---

