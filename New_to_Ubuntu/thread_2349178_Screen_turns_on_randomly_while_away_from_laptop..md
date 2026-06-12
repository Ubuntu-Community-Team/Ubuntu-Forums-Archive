---
title: "Screen turns on randomly while away from laptop."
date: 2017-01-11
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-01-11
Normally google seems to have a lot of hits about the screen going blank randomly. But in my case it's backwards. When I go afk and leave it alone the screen goes black after a certain amount of time. But occasionally it turns itself back on without ever touching the mouse or screen or keyboard. Then it turns itself off again, sometimes in a few seconds, other times a few hours. It never stays black or off like it is supposed to. How to fix. This problem is happening on Kubuntu, Ubuntu, and Ubuntu Server with the i3 window manager. The screen keeps waking up.

---

### Post by DuckHook on 2017-01-11
You give us no info on your HW setup. In particular, your mouse/keyboard/video specs. Do you use a KVM switch? If so, take it out of the loop and plug your components into your computer directly. Some KVMs send intermittent keyboard signals to your computer as a sort of "hey, I'm still here" notice.

The next time your monitor self-wakes, immediately look at your logs, especially *kern.log* and *syslog*. You can try using *tail* to cut down on the sheer volume of entries. Pay particular attention to the entries around the time your screen wakes up, which would be the latest ones. Log entries are time-stamped to facilitate this kind of detective work.

---

### Post by Geoffrey_Arndt on 2017-01-11
Sometimes even a small vibration can move an optical over-sensitive [FONT=tahoma]**mouse**[/FONT] . . . . . do you have any heavy steppers in the house (or a FAT cat)???

---

