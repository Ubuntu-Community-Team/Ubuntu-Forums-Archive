---
title: "Problems with 3d apps."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by shakari on 2008-05-05
When trying to set chess to 3d mode I keep getting this error
"You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support"

So wondering how I enable this. I have a nvidia 7600gs, and have enabled the restricted drivers for it.

I have no been able to install the drivers from the nvidia website though, can download it easy enough, but it just wont run or something.

Im also guessing that this is the reason why im only getting 5 or so fps trying to play eve-online in ubuntu. I get 40+ fps running it in windows.

---

### Post by SunnyRabbiera on 2008-05-05
no, but the chess application does need some extra stuff to make 3d work.
To fix your chess application at least to display in 3d go up to system then to administration and go to synaptic package manager.
search for python open gl and install it by right or left clicking it and selecting "mark for install"
and if it asks to mark additional packages do so.
and also in that same list mark the python Python GTKGLExt package for install too and again mark extra changes when prompted.
and then go to apply, and again apply...
its very straightforward.

---

### Post by cojafoji on 2008-05-29
just an fyi, it may not have worked for you if you just installed the GtkGLext library. you also need to install the GtkGLext python bindings as well. Just go into synaptic, search python-GtkGLext1 and install the library that comes up. that should get it working if the above didn't already.

---

