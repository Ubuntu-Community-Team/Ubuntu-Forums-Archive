---
title: "Problem when using mount"
date: 2008-07-15
forum: Programming Talk
---

### Post by blooddrunk on 2008-07-15
In the PAM application I am writing in C after the user is authenticated on the server, the program should display his home directory. For that I found the module pam_mount. The problem is that I don't know how to get it working. I've done all the necessary changes in pam.d, but when after authenticating I reach the mounting part, it gives me things like "mount errors: only root can do that" and "waiting for mount: ... mount failed". The mount point is : /home/%(USER) and the lclmount looks like:
<lclmount>mount -p0 -t %(FSTYPE) %(VOLUME) %(MNTPT)
          "%(ifnempty=\"-o\" OPTIONS)" %(OPTIONS)</lclmount>

Any help and suggestions will be appreciated

---

