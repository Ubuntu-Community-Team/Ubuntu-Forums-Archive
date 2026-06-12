---
title: "Gambas2  v4l  webcam"
date: 2007-06-09
forum: Programming Talk
---

### Post by webcambuntu on 2007-06-09
Running Ubuntu 7.04 Final, I just compiled the latest gambas2 with the exception of one thing that concerns me.   gb.qte  Not sure if I really need it or not. Finding info on gambas is a real pain.
Anyway, it does run. So now I am trying to access a webcam that works great with camstream, (Its a philips SPC 900NC) but not with the example webcam program.

For some reason the help browser is not complete in relation to the gb.v4l component.

With the example code, I tried to modify it on the line 
```
hWebCam.Source = hWebCam.TV + hWebCam.pal
```
play around with different options that come up when you pause after you key the dot.
Example, I tried hWebCam.NTSC

Any ideas would be greatly welcomed.

Also, if you know how to access a webcam with realbasic, I can use it instead of gambas2.

Thanks webcambuntu

---

### Post by msumurph on 2007-06-18
While I don't have experience with the gb.v4l component, I can offer ideas on how to get help.  Gambas2 along with its documentation are still under development, so the v4l component may not be well documented as you mentioned.  I recommend sending a request to the gambas-users email list.  The community is usually very helpful and supportive.

---

