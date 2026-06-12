---
title: "[SOLVED] Bluetooth mouse delays on keyboard action"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by katsu_ishii on 2008-05-27
To explain in (slightly) greater detail:
I am using an HP dv9000 laptop. When I press a key on the built-in keyboard, Ubuntu will not read any input given from the bluetooth mouse. Ubuntu has no issue reading input from the built-in touchpad during keypresses. I have no other mice (mouses?) that work with my laptop to test with.

It has been occurring for some time now, but I believe it started when I installed and used wminput. Any ideas?

---

### Post by katsu_ishii on 2008-06-10
Update: After more extensive searching, I've found that the mouse delay is related to a package named mouseemu. Removing the package solved the problem without any noticeable side-effects. I'm not sure why mouseemu didn't prevent input from the touchpad during keyboard activity though...

---

