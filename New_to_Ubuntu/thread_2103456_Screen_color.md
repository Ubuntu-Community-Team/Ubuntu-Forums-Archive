---
title: "Screen color?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-10
Hi,

When I turn on my machine shows a voilet background which is normal but than get a black back ground for a second before the Ubuntu logo, is that normal?

Thanks.

---

### Post by cortman on 2013-01-10
Yes. It's not uncommon to get flashes of pixel streaks across the screen during startup, for me anyway.

---

### Post by Yezinki on 2013-01-10
Thanks cortman, they are not flashes or pixel breaks but a black screen before Ubuntu logo with dots..is that normal?

---

### Post by grahammechanical on 2013-01-10
Yes. From boot menu to login screen control over the display is passed from one display server/manager to another. The transition is not smooth. This is one reason why the developers were hoping to use something called Weyland/Weston from 12.10. But they failed to complete the work in time.

I am not sure of the exact sequence but I think it is something like this.

1) The Grub menu appears using a basic VGA display.
2) The Xserver takes over (black screen).
3) The Plymouth splash screen appears (purple screen with dots). This reassures us that the thing is still working.
4) The LightDM login screen appears with default background image or chosen static desktop wallpaper
5) The Gnome desktop loads with chosen wallpaper.
6) Unity or chosen User Interface is loaded.

Oh, if we are using a proprietary video driver, then that has to take over at some point. Hence, the flashes of pixels that some of us see.

That is my guess work.

Regards.

---

### Post by mc4man on 2013-01-10
> **Yezinki said:**
>  but a black screen before Ubuntu logo with dots..is that normal?

Intended behavior, not really, but quite common & nothing to worry about.
The transition from greeter to Desktop worked very well during 12.04 development for about 2 weeks, since then it's been broken, fixed, broken, fixed. 
You may notice some times you won't get the black screen..

---

### Post by Yezinki on 2013-01-10
Thanks grahammechanical & mc4man for your replies & expert views.

---

