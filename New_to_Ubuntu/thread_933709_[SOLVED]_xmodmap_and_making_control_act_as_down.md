---
title: "[SOLVED] xmodmap and making control act as down"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by jordanmthomas on 2008-09-29
The down key on my laptop has recently stopped working very well. 
I'd like to make my right control key act as down, so I can continue to use my keyboard.

I am able to make it work with 
```
xmodmap -e "keycode 109 = Down"
```

The only problem is that if I hold it down, it's not repeated.  For example, typically the down key if held down on a web page will continually move the page down.  After using xmodmap, my control key only registers one press.

I'm sure there's a way to make it work as expected, but I can't really figure it out.

---

### Post by Whiffle on 2008-09-29
Try doing:

xset r 109

(109 is the keycode for control on my laptop, found using xev)

---

### Post by jordanmthomas on 2008-09-29
> **Whiffle said:**
> Try doing:

xset r 109

(109 is the keycode for control on my laptop, found using xev)

Ah, perfect.  109 is the keycode for mine too.  Thanks.

---

