---
title: "Problem with Screen Resolution  asus vivobook F512DA ryzen 3 Radeon"
date: 2020-05-13
forum: New to Ubuntu
---

### Post by apribuntu on 2020-05-13
I just installed ubuntu on my asus vivobook F512DA, Ryzen 3 2200U. But, i have a problem with the resolution, in ubuntu setting just one option screen resolution is 800x600. But, My asus is FHD. Any idea?

---

### Post by CelticWarrior on 2020-05-13
Welcome.

For that hardware you need the latest Ubuntu. Have you installed Ubuntu 20.04?

---

### Post by apribuntu on 2020-05-13
For newest ubuntu 20 i installed it on virtual box, but same problem, screen resolution just 800x600 only.

---

### Post by CelticWarrior on 2020-05-13
Are you complaining about Ubuntu in a VM, the host OS (which one?) or both?
If the host OS, whatever that is, hasn't the proper graphics drivers then, obviously, a VM won't be better or enable an higher resolution than the host.

Please clarify your setup and avoid vague statements.

---

### Post by TheFu on 2020-05-13
In short, the actual GPU installed in the physical machine has ZERO to do with the virtual GPU presented to a guest.

VM GPUs are virtual unless you go way, way, way, out of the normal to setup GPU passthru.  Most laptops only have 1 GPU, and 1 must be assigned to the hostOS, meaning there's no possible way to create a passthru to a guest.  Guest device passthru requires exclusive access of the resource/device. It cannot be used by the host AND guest.

---

