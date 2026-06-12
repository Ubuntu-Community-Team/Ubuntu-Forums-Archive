---
title: "Retaining Keyboard Backlight on reboot"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Jacen on 2012-05-25
Similar to this post:
[http://ubuntuforums.org/showthread.php?t=1982078](http://ubuntuforums.org/showthread.php?t=1982078)

I was wondering if the keyboard backlight on a macbook air could also be set in rc.local

Also, would it be possible to, instead of setting a numerical value in rc.local take the current screen and/or keyboard backlight brightness and set that as the brightness upon reboot?

---

### Post by Jacen on 2012-05-25
Ok, so looking around on some macbook pro posts, I found:

```
echo X > /sys/class/leds/smc\:\:kbd_backlight/brightness
```

where X is the number you want, and throw that in your rc.local

SO, now my question skips directly to the second half: Is there a way to read the current brightness from the system and echo that instead of a digit?

---

