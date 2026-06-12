---
title: "Linux 3.0.0-6.7 soon in Oneirc repos"
date: 2011-07-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-20
This is a bug fix build, not a new rc.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-6.7](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-6.7)

Actually this is the rc7.

---

### Post by Harry33 on 2011-07-21
The kernel 3.00-6.7 is now ready for manual download from Launchpad.
One thing to note.
For me, the dkms module autoinstallation did not work.
So I had to manually reinstall nvidia-current after kernel installation.
But that one worked and new kernel is now up and running well.

---

### Post by dino99 on 2011-07-21
cant be installed via synaptic/update-manager

---

### Post by Harry33 on 2011-07-21
> **dino99 said:**
> cant be installed via synaptic/update-manager

That is true, because the kernel has not been published and uploaded into Oneiric repos.
ATM it is only possible to install them manually by downloading the files:
- linux-headers-3.0.0-6
- linux-headers-3.0.0-6-generic
- linux-image-3.0.0-6-generic
- linux-libc-dev
and then installing them locally with dpkg.

---

### Post by Harry33 on 2011-07-21
Now this kernel is in Oneiric repos.

---

### Post by cariboo on 2011-07-21
I just installed 3.0.0-6.7, I had to re-install nvidia-current.

---

### Post by Harry33 on 2011-07-22
> **cariboo907 said:**
> I just installed 3.0.0-6.7, I had to re-install nvidia-current.

Yes, same here.
I now use the new beta nvidia-current (280.04) from xorg-edgers.

---

