---
title: "How to get Fn+ F7 and F8 (brighten and dim) keys working on HP dv2000 with Hardy?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-08-26
I can't seem to find a fix for this. the keys don't work. Any way to enable these Fn keys? Thank you.

---

### Post by marufaberlin on 2008-08-26
do these keys send keycodes?

please post result of:
```
dmsg|tail
```
after pressing them.

If they don't, it doesn't look good.

If they do, you can use setkeycode <keycode> to make it known.

---

### Post by uncibex on 2008-11-04
I couldn't get any fix I tried in Hardy to work.  However, when I upgraded to Intrepid Ibex, the controls worked fine!!  If you're willing to do that, it might be the easiest way to get it fixed.

---

