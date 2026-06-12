---
title: "Can someone verify a bug in FPC/Lazarus"
date: 2010-01-27
forum: Programming Talk
---

### Post by Irvine_himself on 2010-01-27
I have an array of Timage where the mouse event handlers point to the event handlers of a single "mother image". There they are processed and the correct array element is identified.  This all works and I only mention it for completeness.

The bug I think I have found is when the mouse leaves one image and enters another. I wish to know the state of the mouse buttons but this information is not passed to the event handler.  So I have been trying to use the primitive "GetMouseButtons", but no matter what I do, it always returns zero. I even tried using it conjunction with InitMouse!

For the moment, I have a workaround using a global boolean that is continually set false except when exiting an image with the left mouse button down. It works, but is not elegant and dangerously unsatisfactory.

Before posting a bug report I would like to see if anyone else can confirm it, (and also make sure that it is not my lack of knowledge.)

---

