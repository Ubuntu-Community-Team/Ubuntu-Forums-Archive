---
title: "Moblock errors after Upgrading Ubuntu"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by videocheez on 2008-05-03
I have used moblock with the GUI for the past year while filesharing and I just noiticed that after recently upgrading Ubuntu that it does not seem to be working properly.  I get the following error when I try to run it.

***error during nfq_unbind_pf()***

What does this mean and how can i fix it?  Any help will be appreciated.

Thanks in advance,

VC

---

### Post by nowshining on 2008-05-03
have you tried seeing if there is an update to the program and if so, installing this update?

---

### Post by videocheez on 2008-05-03
> **nowshining said:**
> have you tried seeing if there is an update to the program and if so, installing this update?
according to synaptic, i currently have the latest version already installed.

---

### Post by nowshining on 2008-05-04
hmmm, trying downloading an update manually here, last I searched a search returned the prob. saying it was a change in the kernel that caused it in the desc.

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

try there the home page. :)

---

### Post by jre on 2008-05-06
I guess this relates to this bug: [http://developer.berlios.de/bugs/?func=detailbug&bug_id=12156&group_id=2509](http://developer.berlios.de/bugs/?func=detailbug&bug_id=12156&group_id=2509)
In this case this is not a "real" error message:
Cite from the bug report by the upstream author:
"[...] you still get the error the first time you run moblock but it works correctly, then if you kill moblock and restart it you will not get that error until reboot."

So, just test moblock:
Have a look at "moblock-control status" and "moblock-control test".

---

