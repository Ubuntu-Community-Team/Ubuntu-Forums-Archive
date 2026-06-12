---
title: "Stuff not working with new kernel"
date: 2008-04-26
forum: Packaging and Compiling Programs
---

### Post by chadjohnson on 2008-04-26
I compiled a kernel as well as the linux-restricted-modules (and installed them), and now (booted into the new kernel) eth0 does not work. ifconfig shows eth0 as existing, but it simply will not get an IP address with dhclient. Any ideas?

---

### Post by grannyw on 2008-04-26
it sounds rather silly but try to change it to eth1

---

### Post by chadjohnson on 2008-04-27
How would I do this?

---

### Post by grannyw on 2008-04-27
i would do this through the network monitor that u can just add to your control panel.when o open it just change eth0 to eth1 by typing

---

### Post by chadjohnson on 2008-04-27
Doesn't seem I can do this. I go to System->Administration->Network Tools, select eth0, and the Configure button is disabled. It also says "not available" next to everything under Interface Information.

*EDIT* OK, I managed to change the name by changing eth0 to eth1 in /etc/udev/rules.d/70-persistent-net.rules, but I still get the same results.

---

### Post by grannyw on 2008-04-27
i mean on the panel where you have applications/places and etc.add there "network monitor" and try there

---

### Post by chadjohnson on 2008-04-29
Ok, back after finals...

It's simply not there...it's not hidden either. I could not find with apt, either.

Can anyone offer any solutions to my problem?

---

