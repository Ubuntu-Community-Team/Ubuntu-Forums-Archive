---
title: "/boot is nearly full"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by msd2008 on 2011-11-25
Hi all,

I am running Ubuntu Server (10.04) and noticed that the /boot partition is nearly full. How can I go about clearing it up?

Thanks

---

### Post by Gone fishing on 2011-11-25
What's it full of?

Old image files? If so if you uninstall the old Linux kernel images you should be OK.

sudo apt-get uninstall linux-image-?????

depending on the old kernels you have.

---

### Post by sophia911 on 2011-11-25
Uninstall it . Try it .

---

### Post by msd2008 on 2011-11-27
Thanks Gone Fishing.

I'll give that a go.

---

