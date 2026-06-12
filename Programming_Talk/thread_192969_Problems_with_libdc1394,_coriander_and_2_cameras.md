---
title: "Problems with libdc1394, coriander and 2 cameras"
date: 2006-06-09
forum: Programming Talk
---

### Post by jpsisko on 2006-06-09
Hello all.

I am experiencing some issue with libdc1394 2.0 pre7 and coriander 2.0 pre 6.

When I connect just one camera to the ieee1394 card all works well; however when I connect two cameras I have some really strange behaviours: sometimes I cannot see the video feed from one camera at all, some other time, when I activate one camera, the video feed from the other one gets corrupted and get back to normal when I deactivate the acquisition from the 2nd camera.
This is really getting me crazy.

Can anyone help me out in some way?
I think that the problem regards the multiple camera support; I don't know, maybe I haven't initialized some device...

Thank you for your help!
Andrea

---

### Post by makhand on 2007-01-17
Did you have to do anything special to compile these? I get errors like>  libdc1394 is too old if i try coriander2.0-rc2,3, or I get things like > error while loading shared libraries: libdc1394.so.20. I guess I'd like to get to where you are. I've tried several combinations of libdc and coriander, including the one you listed with no luck. 

Also, as a side note, maybe you know something about this, but when i try all these different versions, do I need to worry about somehow 'uninstalling' the other ones (say getting rid of -rc3 before trying pre6)?

---

