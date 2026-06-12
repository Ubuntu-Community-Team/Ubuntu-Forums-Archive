---
title: "problem with new monitor"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by m3t3ors on 2012-01-14
just got a new monitor, as mine went faulty.
anyway when i connected it via graphic card, it booted for 3 minutes then a box came on screen saying not optimum resolution, recommends some settings and thats it.?
i cant get any further then that screen, ive tried using on board graphics and get to the same screen.
ive even tried a new cable, tried re-installing ubuntu which went fine untill it says remove cd and reboot, where after reboot i get the screen sainy not optimum resolution

any ideas as im thinking of launching it through the window:confused:

---

### Post by Buntumatic on 2012-01-14
There is the monitor, graphics card, and Xorg. There has to be harmony between these three.
Xorg is supposed to query your monitor what it is capable of, monitor is supposed to reply with EDID data, Xorg is supposed to tell your graphics card to use a supported video mode.
Now, if this automated process is failing for some reason you have to interfere as master of your computer and let it know what you want.
If you need help establishing your position as boss over that PC then you need to post your Xorg log in pastebin so potential helpers can have a clue what's going on.

---

### Post by m3t3ors on 2012-01-14
the computer boots but not on screen, ive googled the "not optimum mode" error and its a common problem with lcd monitors

---

### Post by Buntumatic on 2012-01-14
You didn't understand a word of my post, did you? I should have known better, sorry for replying.
[Why some posts should be ignored.]("http://catb.org/~esr/faqs/smart-questions.html#writewell")

---

### Post by m3t3ors on 2012-01-14
yes i understood your post, ive used linux for 10 years now since red hat 9 was released
the error message " not optimum mode, recomend 1280 x 1024 60hz is the monitor issue
if i cant get linux on screen i cant change anything.

any way back to my post

ive finally got it to boot in recovery mode and changed the resolution BUT still cant change the monitor setting for the mode

---

### Post by m3t3ors on 2012-01-15
just connected my old monitor and set to the highest resolution. rebooted and all is fine, 
when i connect my new monitor alls fine to the monitor goes into stand by then the pc goes to stand by and if i use keyboard i get the error message, not optimum mode, recommend 1280 x 1025 60 hz
ive looked for screen saver but cant find how to activate screen saver as i was hoping it might save the monitor going in stand by mode

---

### Post by m3t3ors on 2012-01-15
installed xscreensaver, just hoping this works

---

