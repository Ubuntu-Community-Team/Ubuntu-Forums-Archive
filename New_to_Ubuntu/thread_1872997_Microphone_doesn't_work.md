---
title: "Microphone doesn't work"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by reidar4 on 2011-10-31
Hello

 Since I upgraded to Oneiric ocelot,the microphone's stopped working.There seems to be a conflict between the sound settings in the "Sound"-menu (click on the speaker at the upper right of the screen,)and the settings in the Alsamixer-menu.

    Can anyone solve this problem?
                                                          Best regards Reidar

---

### Post by ajgreeny on 2011-10-31
> **reidar4 said:**
> Hello

 Since I upgraded to Oneiric ocelot,the microphone's stopped working.There seems to be a conflict between the sound settings in the "Sound"-menu (click on the speaker at the upper right of the screen,)and the settings in the Alsamixer-menu.

    Can anyone solve this problem?
                                                          Best regards Reidar
I'm not surewhat you mean by the alsamixer-menu, alsamixer is a terminal utility with n-curses interface, but very easy to use.

So run ```
alsamixer
``` in terminal and check that the levels of mic and capture outputs are not set too low or muted.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

You may also need to ensure that the pulse volume controls are set properly, using the menus for "Sound and video" though I'm not sure how you find it in unity.

---

