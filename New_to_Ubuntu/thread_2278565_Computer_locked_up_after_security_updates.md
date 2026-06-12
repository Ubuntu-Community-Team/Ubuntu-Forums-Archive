---
title: "Computer locked up after security updates"
date: 2015-05-17
forum: New to Ubuntu
---

### Post by Doug_Jones on 2015-05-17
I did a security update the other day and my computer is locked up. It reaches the desktop but the keyboard and mouse do not work. Right before the splash screen, I get the following errors:

version message write failed ret = -5
hbm_start failed ret = -5
reset failed
link layer initialization failed
init hw failure

Thanks for any help you can provide.

---

### Post by sandyd on 2015-05-17
Try this:

Hit shift when the system boots if your GRUB menu does not show up.

Then, go to 'Advanced Options' and choose an earlier kernel.

---

### Post by Doug_Jones on 2015-05-17
I can log in successfully with all the earlier kernels.

---

### Post by sandyd on 2015-05-17
Assuming that all the updates are applied (apt-get dist-upgrade should have 0 packages), you may want to file a bug as this is now a issue with the new kernel.

---

