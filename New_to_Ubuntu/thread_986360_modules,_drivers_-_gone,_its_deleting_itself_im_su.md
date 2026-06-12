---
title: "modules, drivers - gone, its deleting itself im sure.."
date: 2008-11-18
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-11-18
hi guys

i have quite a serious problem....

I recently got wireless internet, it wouldnt connect well - (0.5mbs etc), i played around with modprobe b43 and ndiswrapper, nothing worked, but now doesn't connect at all - and when i type
```
 sudo modprobe b43 
``` 
it says 
FATAL ERROR: module b43 not found 

I also cant plug in any HDD's, or memory sticks because my pc says - you do not have the necessary modules to open vfat.... whereas i did before

My speakers wont work because i now dont have the correct gstreamer plugins - whereas again i did before.

This sudden lack of any modules etc seems to have happened almost instantly... 

where are they - whats going on??

any help!?

---

### Post by ggaaron on 2008-11-18
Playing with things (probably especially with things like ndistwrapper) can break other things. You provide not enough information to help you. Why didn't you let Ubuntu install your wifi card? If it needs non-free firmware you can install it using the restricted drivers application.

---

