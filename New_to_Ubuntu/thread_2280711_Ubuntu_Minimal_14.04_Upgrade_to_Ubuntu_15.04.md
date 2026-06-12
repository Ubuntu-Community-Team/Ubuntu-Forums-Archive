---
title: "Ubuntu Minimal 14.04: Upgrade to Ubuntu 15.04"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by dillon4 on 2015-06-01
Hello. I was wondering If I could upgrade either to Ubuntu Desktop 14.04 or Ubuntu 15.04  

I'm currently on a VPS I bought using OpenVZ, I noticed the Kernel drivers aren't working on Minimal is there a way to upgrade?

Thank you ~ Dillon

---

### Post by cariboo on 2015-06-01
It may be that your vps may not support virtualization, I'd check with your providers.

---

### Post by dillon4 on 2015-06-01
Thank you ill check with them.

---

### Post by sandyd on 2015-06-02
> **dillon4 said:**
> Hello. I was wondering If I could upgrade either to Ubuntu Desktop 14.04 or Ubuntu 15.04  

I'm currently on a VPS I bought using OpenVZ, I noticed the Kernel drivers aren't working on Minimal is there a way to upgrade?

Thank you ~ Dillon

The kernel drivers won't work on openvz.

OpenVZ uses a shared kernel on the host, so any drivers that you need to load will have to be installed on the host, then your container may need to have the driver enabled. Most providers won't do that as adding kernel modules to the host can affect other users on the host as well.

What driver are you looking to run?

---

### Post by dillon4 on 2015-06-02
Not sure witch ones I need. Just ones that allow me to run a virtualbox.

---

### Post by sandyd on 2015-06-02
Nope, that won't work in openvz.

You can use qemu, but many hosts do not allow nested virtualization anyways.

---

