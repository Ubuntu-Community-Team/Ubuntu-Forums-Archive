---
title: "[SOLVED] RSI - Joystick as mouse?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by MaxVK on 2008-08-19
Okay, this is a bit of strange one - I suffer from occasional attacks of RSI from using the mouse/trackball too much. Some time ago in Windows I had a small program that allowed me to use the joystick as the mouse.

Is this possible under Linux (Ubuntu 7.10)?

Cheers

Max

---

### Post by MaxVK on 2008-08-19
Well, I didn't solve it myself - In the end some fruitful googling brought me back here to a post that was missed in my own search and the search done with the title of the post.

Nevertheless, its solved and here is the post that helped me:

[http://ubuntuforums.org/showthread.php?t=516709](http://ubuntuforums.org/showthread.php?t=516709)

I used the xorg config from about halfway down, and everything seems to be working just fine. I'm using a (rather battered) Logitech Attack 3, and while all of the buttons don't work, and the top of the joystick has snapped off, the movement and *enough* of the buttons work to replace a standard 3 button mouse.

Off to buy a new joystick and hopefully say goodbye to some RSI!

Max

---

### Post by MaxVK on 2008-08-19
Just as a further informative note:

The line of code that returns the current joystick movement/buttons pressed does not report accurately for my joystick.

 jstest /dev/input/js0

In the terminal the correct number of buttons are reported, as is the correct device, however, the buttons on the actual stick are numbered, and these numbers do not correspond with the numbers being shown as active in the terminal. Subsequent editing of xorg.conf shows that the numbers on the joystick are the correct ones for the assignments.

Its no biggie, but I thought Id mention it just in case anyone suffered any confusion because of it.

All the best

Max

---

