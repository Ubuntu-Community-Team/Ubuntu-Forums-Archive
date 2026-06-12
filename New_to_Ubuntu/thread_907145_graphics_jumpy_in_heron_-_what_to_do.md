---
title: "graphics jumpy in heron - what to do?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by absalom on 2008-09-01
I upgraded to hardy - and now all video playback is veryvery jumpy in fullscreen. In a small screen it's okay but when i enlarge the screen it goes jumpy and even the sound starts jumping. I've tried every player and type of media i have installed - same thing in a bit different amounts.

other things i've noticed:

- I have an integrated ATI GPU - i've used "envy" to update the restricted drivers - no help.

- changing window manager to metacity makes things even slower! if i set the manager to metacity even dragging a window around the desktop starts lags.

- Xgl seems to take a lot of my processor poer whole the time.

Might a have any help of a clean 32 bit install instead of this upgrade fro mgutsy?

---

### Post by cwsnyder on 2008-09-01
First response, it looks as if you are having a problem with not enough memory to buffer the video.  You could try going to System >> Administration >> Hardware Drivers and seeing if your ATI driver is enabled, and switching off compiz or other eye candy display environments.  You could also try going to Synaptic and loading Xfce or Enlightenment display environments, then restarting and setting the Session for the Xfce or Enlightenment environment.  Either of these may be confusing if you are not familiar with them because the menu bars are eliminated, but they take fewer system resources and may enable you to smooth out the video playback.

---

