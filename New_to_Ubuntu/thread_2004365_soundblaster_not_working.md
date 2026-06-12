---
title: "soundblaster not working"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by stiggowitz on 2012-06-15
I recently installed ubuntu 12.4 over winxp (beginner) and everything is ok except that I have no sound.
I have a soundblaster audigy sound card and it was working with the windows os
but not with U.
is there a driver I need?

s:)

---

### Post by Curtis6767 on 2012-06-15
Try this. 

Open up a terminal by hitting Ctrl + Alt + t

In the terminal type alsamixer

When alsa mixer opens use your arrow keys to move sideways and/or to push the volume levels up.

If you see MM at the bottom of one of the columns, then move over to it and press the 'm' key on you keyboard to unmute it.

Once you get the volumes set, then try to see if you get any sound. If not then click on the gear icon in the top right hand corner of the screen and select System Settings and then Additional Drivers. In there see if there's a driver for your sound card.

Hope this helps

---

