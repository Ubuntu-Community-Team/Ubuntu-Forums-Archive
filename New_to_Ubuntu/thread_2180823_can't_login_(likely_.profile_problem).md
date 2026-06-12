---
title: "can't login (likely .profile problem)"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by dart2 on 2013-10-14
Hello!
I logged into 12.04lts, and modified my .profile.  Tested it by running it in new xterms; worked fine (it also works fine under Scientific Linux 6.3).  Rebooted (its a VM).  Now I get the login screen (two options, myself and guest).  I enter the p/w, and it accepts it and works a bit, then reverts back to the login screen.  I have set a root password, so if su or sudo worked under guest, I'd "mv /home/me/.profile /home/me/profile" and I expect I'd be able to login.  ("me" isn't really my login directory name).  If I could ssh onto the machine -- but its a VM, and I have no idea how to do it (using ssh me@unicorn didn't work, and unicorn is the hostname).  Any ideas about how to get logged in?

Thanks!
Chip Campbell

---

### Post by whitesmith on 2013-10-14
Hi **dart2**, and welcome to the forum! A common reason for this problem is screwy permissions in $HOME. You should (minor oversimplification) own everything there. Check and see if you do. Ownership problems can arise from such errors as ```
sudo nautilus
``` instead of ```
gksudo nautilus
```Be sure to login in the terminal (ctrl+alt+f2). If Ubuntu buys that, your problem is almost certainly in $HOME.

---

