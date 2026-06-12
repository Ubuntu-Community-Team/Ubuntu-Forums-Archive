---
title: "Headphones Sound - 12.04"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by ajdrew06 on 2013-01-18
Hi All,

When I plug in headphones, my headphones are muted by default, and I have to go into alsamixer to unmute the headphones. If I unplug the headphones even for a second and reconnect the headphones, the headphones get muted & I have to unmute in alsamixer. It's frustrating. Anyone know how to fix this? 

FYI, when my headphones are not plugged in, sound goes to the speakers as expected; when the headphones are plugged in, sound from the speakers is muted as expected.

-Drew

---

### Post by ajdrew06 on 2013-01-28
anyone?

---

### Post by frank604 on 2013-01-28
Just an idea.  Not sure if this will work but logically it made sense to me.

Let's change your configuration/profile.  I'm thinking the headphone is muted by default and after you insert/unplug your headphone, it loads the alsamixer profile which is default to mute.

[]("http://ubuntuforums.org/showthread.php?t=1652691")

This link shows how to either

a) save current settings to conf/profile
b) remove current settings, set the settings in alsamixer, save to conf/profile

Hope it works, keep us posted.

---

