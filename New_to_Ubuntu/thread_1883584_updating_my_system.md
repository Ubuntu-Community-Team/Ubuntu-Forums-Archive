---
title: "updating my system"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by Junior Dugan on 2011-11-19
I have been trying to update my system, now when I do a sudo apt-get update, it goes through and when I try to update 10.4 it says I need an additional 2 MiB of space on the /boot. same thing happens with KPackageKit, what can I safely get rid of to continue to update or how can I increase the size of my /boot partition?

---

### Post by TeoBigusGeekus on 2011-11-19
You can delete old kernels.
Open synaptic and do a search for linux-image.
Keep the 2 most recent ones and right click>completely uninstall the other ones.
Then
```
sudo update-grub
```
to update your grub menu and you're done.

---

### Post by Junior Dugan on 2011-11-19
are some of the older kernels being used or at lease the newer kernels using some of the older kernels items?

---

### Post by Junior Dugan on 2011-11-19
would some of the older Kernels be dependent in some way to the latest one?

---

### Post by Junior Dugan on 2011-11-19
That worked TeoBigusGeekus, Thanks!

---

### Post by TeoBigusGeekus on 2011-11-19
Sorry for the late answers.
> **Junior Dugan said:**
> are some of the older kernels being used or at lease the newer kernels using some of the older kernels items?
No.
> **Junior Dugan said:**
> would some of the older Kernels be dependent in some way to the latest one?
No again.
> **Junior Dugan said:**
> That worked TeoBigusGeekus, Thanks!
Glad to hear that. Don't forget to mark the thread as solved.

---

