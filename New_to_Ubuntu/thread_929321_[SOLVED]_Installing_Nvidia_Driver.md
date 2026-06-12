---
title: "[SOLVED] Installing Nvidia Driver"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by brookswm on 2008-09-24
I downloaded the Nvidia Linux driver for my video card and the instructions say:

sh NVIDIA-Linux-x86-173.14.12-pkg1.run

to install the driver.  I assumed that I needed to type that out in terminal, but when I did I got:

sh Can't open sh NVIDIA-Linux-x86-173.14.12-pkg1.run

Please help!

---

### Post by kjohansen on 2008-09-24
you probably need to give it executable permissions

```

chmod 755 NVIDIA-Linux.....

```

It would be much easier to use the driver from the repositiories though.

System->Hardware drivers, and then click the checkbox next to the nvidia driver...

---

### Post by mike1234 on 2008-09-24
> **brookswm said:**
> I downloaded the Nvidia Linux driver for my video card and the instructions say:

sh NVIDIA-Linux-x86-173.14.12-pkg1.run

to install the driver.  I assumed that I needed to type that out in terminal, but when I did I got:

sh Can't open sh NVIDIA-Linux-x86-173.14.12-pkg1.run

Please help!
  I would just use the one in synaptic. Check system -> Adminisration -> Hardware drivers. see if it lists an nvidia card and if it's enabled.

M.

---

