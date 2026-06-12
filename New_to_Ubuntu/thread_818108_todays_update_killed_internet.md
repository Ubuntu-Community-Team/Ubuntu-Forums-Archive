---
title: "todays update killed internet"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-06-04
I just restarted after installing the latest updates (new kernel?)
and I am unable to connect to the internet.

It says:

no devices found

It is a normal wired connection.

Help wanted.

---

### Post by philinux on 2008-06-04
These new kernels are borking wireless for some, suspend and hibernate and now wired net.

Try the previous kernel from grub.

---

### Post by billgoldberg on 2008-06-04
Thanks, I'm back online using the 2.6.24-17-generic kernel

2.6.24-18 breaks my internet connection

Now, is this fixable or do I have to wait for an update?

I presume this bug will be fixed in a few days?

---

### Post by philinux on 2008-06-04
I'm dreading a new kernel update as I've then got to reinstall my nvidia driver see my thread just now you might be able to help me. :lolflag:

---

### Post by billgoldberg on 2008-06-04
I filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/237335](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/237335)

It's my first bug report, so I don't know if I did it right.

---

### Post by billgoldberg on 2008-06-04
Lot's of people seem to have trouble with the new kernel,

I'm glad I'm not alone.

haha

---

### Post by bumanie on 2008-06-04
You can go into synaptic and remove the latest kernel. Fortunately, my computer works fine with the latest kernel. It's always a good idea to keep some old kernels around for this type of scenario.

---

### Post by billgoldberg on 2008-06-05
> **bumanie said:**
> You can go into synaptic and remove the latest kernel. Fortunately, my computer works fine with the latest kernel. It's always a good idea to keep some old kernels around for this type of scenario.

I'm using the 2.6.24-17 kernel right now.

---

