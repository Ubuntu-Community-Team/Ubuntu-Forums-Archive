---
title: "How do I get my graphics card working?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by nachomania on 2008-05-16
I've been trying to get my Geforce2 to work with ubuntu, and can't get it right. Either I make my system unable to get me to the login screen, or, like right now, I think I have it kind of running, but can't enable desktop effects. Any ideas?

---

### Post by sailor2001 on 2008-05-16
you have to have restricted drivers activated. If you are on 8.04 it is taken care of for you, however, that card can get touchy at times. I suggest you go to /usr/share/applications/screen & graphics and pull up your monitor # and change resolution to a higher setting and see if that helps. Have you gone into synaptics and downloaded a compiz manager?

---

### Post by nachomania on 2008-05-17
I've got 1024x768 resolution, and the Simple CompizConfig Settings manager. It's telling me that accessibility is disabled.

---

### Post by alienexplorers on 2008-05-17
You need to load the nvidia-glx-legacy driver for that board.  The easiest way to load it is to use Envy-ng.  First unload any driver you have loaded and then select manual load and select the last driver in the list.  This would be the legacy driver.  Once loaded you should be able to run compiz.

---

