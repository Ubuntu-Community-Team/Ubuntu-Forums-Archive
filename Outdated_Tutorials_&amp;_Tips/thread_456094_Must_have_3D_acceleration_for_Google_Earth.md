---
title: "Must have 3D acceleration for Google Earth"
date: 2007-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by lingenfr on 2007-05-27
Having read through 13 pages and not found an answer, I am making this post for those attempting or having difficulty with googleearth. Fist, you need 3D acceleration for googleearth to work. You can check this with the following command:

glxinfo| grep direct

You should receive the following:

direct rendering: Yes

If not, check you video driver, install the correct one or fix your /etc/X11/xorg.conf until you get it working. Then use googleearth from the repositories rather than installing from scratch.

---

