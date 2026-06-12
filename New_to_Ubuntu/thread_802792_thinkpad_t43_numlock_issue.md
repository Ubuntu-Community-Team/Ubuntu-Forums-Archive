---
title: "thinkpad t43 numlock issue"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by wardjame on 2008-05-21
Hi all,
I recently switched over to ubuntu Hardy on my lenovo thinkpad t43.  Everything was working fine for a week or so but now my numlock key is stuck on.

The key combo to turn it off is supposed to be shift+scrLK but that is having no effect.  If I boot it into windows and hit shift+scrLK it toggles numlock on and off no problem so there is definitely nothing wrong with the keyboard.

Having numlock stuck on makes my machine useless so any help would be much appreciated.

---

### Post by spiderbatdad on 2008-05-21
Possibly your keyboard selection... I had to reconfigure using:
```
sudo dpkg-reconfigure xserver-xorg
```and select 101 key generic pc to get mine working correctly. But you may be able to select it under System>>Preferences>>Keyboard>>Layout

Check also that you have the file /etc/X11/xorg.conf
as I didnt initially. xorg.conf was in another file called xresprobe...some weird issue regarding hardware detection that was resloved with boot parameters and reconfiguring xorg

---

### Post by wardjame on 2008-05-21
Thanks for the quick reply.  After playing with the keyboard layout settings a little I realized that I was completely wrong about the problem.

It turns out the LIGHT for numlock is the problem.  It never shuts off even when numlock is off.  Not sure if there is a way to fix that or not but at least I can use my machine again.h

---

