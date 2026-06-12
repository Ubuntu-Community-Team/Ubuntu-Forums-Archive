---
title: "Failed patch"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by icedogchi on 2008-07-11
I always install the updates when the update manager says there's a new patch.

However, after I applied part of the patch last night, java failed to install (why there is a patch, no idea, I don't have Sun java on this machine).  Now when I attempt to install, the Update manager tells me an error occurred and I must run dpkg --configure -a to correct the problem.

Running that command in a terminal give me an error:

Setting up libc6 (2.7-10ubuntu3) ...

Setting up sun-java6-bin (6-06-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: Writing of cache data failed
dpkg: subprocess post-installation script returned error exit status 1

and I'm right back to not being able to patch my machine.

I've also noticed that scrolling in Firefox is very sluggish.
What's going on?  Any ideas?

---

### Post by TeoBigusGeekus on 2008-07-11
Go to synaptic package manager and completely uninstall the packages (java and libc6).
Then reinstall them and see what happens...

---

### Post by icedogchi on 2008-07-11
I found my own problem.  Had nothing to do with UpdateManager or the packages.

My / partition had no free space.

](*,)

---

