---
title: "how to get rid of xdm?"
date: 2005-02-20
forum: Repositories &amp; Backports
---

### Post by dskloet on 2005-02-20
Hi,

I installed xdm but now I want to return to gdm. I tried apt-get remove xdm. It asks me whether I want to stop the display manager. If choose yes the X-server shuts down and I can start gdm manualy. But the next time I boot my computer it starts xdm again. Can anyone tell me how I tell my system it should use gdm again?

thanks,
David

---

### Post by dskloet on 2005-02-20
I fixed it using:
dpkg-reconfigure gdm

thanks anyway,
David

---

