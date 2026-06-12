---
title: "[SOLVED] gimp not recognizing wacom pad"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by wog on 2008-06-05
The wacom pad works fine as a mouse, but neither the pressure to the stylus nor the eraser are recognized.

In Gimp preferences > Input Devices > Configure Extended Input Devices I see that devices "eraser" and "stylus" are disabled under Mode. But when I look for an enabled setting under Mode, all I find are "Screen" and "Window".

Which do I choose? Am I even in the right area for doing this?

---

### Post by ZabiGG on 2008-06-05
You might find the info you need here:

[http://the-labs.com/GIMP/](http://the-labs.com/GIMP/)
(search for wacom)

Hope this helps,

Z.

---

### Post by wog on 2008-06-06
I'm sure that site is very helpful to someone, but I can't even tell what I'm looking at. Does Ubuntu even use xf86Wacom.so as it's Wacom pad driver?

As it turned out, I tried screen mode on both the stylus and eraser, and that seems to be what I needed. My stylus pressure is now recognized in Gimp. I haven't tried the eraser yet, but I'm hopeful.

Thanks!

---

### Post by ZabiGG on 2008-06-06
Thanks for sharing ;) I'm sure it will help other users.

Cheers,

Z.

---

