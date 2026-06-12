---
title: "Why does Ubuntu want to remove linux-image-generic?"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by hoopia on 2014-01-05
Upon installing whois, apt-get is stating to autoremove linux-image-generic. 

```

The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.

```

According to Synaptic, the package version is: 3.11.0.15.16

My concern here is that I thought linux-image-generic was an essential kernel package, and if it is, why does the system want to remove it?

---

### Post by Dave_L on 2014-01-05
linux-image-generic is actually a "metapackage":

> Generic Linux kernel image 
 
This package will always depend on the latest generic kernel image
available.

The only problem with removing it (I think) is that you might not get notified about updates to the "real" packages that contain the kernel.

Have you upgraded to a newer kernel series? Do you have other kernel metapackages installed, such as linux-image-generic-lts-raring, linux-image-generic-lts-saucy, etc.?

But wait for someone else to confirm this before you remove it.

---

### Post by Frogs Hair on 2014-01-05
Do you have the pre-released updates repository enabled ? You can check this from Software & Updates > Updates Tab. Type linux-image-generic in the software center or better yet the synaptic package manager if installed  to find out what kernel/s are installed . Have you installed or removed any software from a non official source such as a PPA ?

---

### Post by hoopia on 2014-01-05
I have not made any changes to the kernel (no attempts at upgrading), and I do have pre-releases enabled. Per *uname -r *my kernel version is 3.11.0-15-generic. I do have some PPAs configured, but haven't tried to remove or install anything from them recently. I do not see any other linux-image-generic-* installed (see attached screenshot).

---

### Post by Frogs Hair on 2014-01-05
It looks like 15.23 and 15.16 are both installed what's odd is the auto remove prompt . I use proposed repositories and have not seen this on my system .

---

### Post by hoopia on 2014-01-05
If there is a later package installed already, safe to assume it's okay to autoremove ?

---

### Post by Frogs Hair on 2014-01-05
Normally yes, proposed updates are primarily for those interested in testing and bug reporting. They can make the system and unstable and cause problems with the package system. In some cases bug fixes come through proposed updates first, but this is not a good reason to enable them. Things become more complicated when PPA software is thrown into the mix.I have both kernel packages installed, but have no autoremove prompt, so there are differences in our systems.   You do have a number of old kernels installed which won't cause problems.

---

### Post by hoopia on 2014-01-05
Alright, thanks for the detailed information. I'll autoremove and see how it turns out.

---

