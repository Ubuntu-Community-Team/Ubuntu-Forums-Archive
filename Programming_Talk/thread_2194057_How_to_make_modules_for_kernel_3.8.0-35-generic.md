---
title: "How to make modules for kernel 3.8.0-35-generic?"
date: 2013-12-16
forum: Programming Talk
---

### Post by Sidoney on 2013-12-16
I used the Ubuntu kernel sources to make modified modules for Ubuntu kernel version 3.8.0-31-generic and could simply copy them for 3.8.0-33-generic and 3.8.0-34-generic but unter 3.8.0-35-generic i first had the problem that the version (module_layout) is incompatible. 
I could fix that by rebuilding the module, but loading the module now fails with new errors like

Unknown symbol skb_pull (err -22)
Unknown symbol dev_kfree_skb_any (err -22)
Unknown symbol skb_pull (err -22)
Unknown symbol skb_push (err -22)
Unknown symbol skb_pad (err -22)

So it seems the 3.8.0-35-generic has other sources and the differences do cause these errors.
But where can i get these sources?

I found the sources and Ubuntu patches for 3.8.0, e. g. under 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/)

but not for 3.8.0-35.

---

### Post by Sidoney on 2013-12-23
I found the answer:

1. Get the sources to the local directory:

apt-get source linux-image-$(uname -r)

This gives:

linux-3.8.0  linux_3.8.0-35.50.diff.gz  linux_3.8.0-35.50.dsc  linux_3.8.0.orig.tar.gz

with the 700 MB kernel sources in linux-3.8.0.

2. Patch:

zcat linux_*.diff.gz | patch -p0 2>&1 | tee patch_log.txt

3. Cleanup and prepare:

cd linux-3.8.0/; make distclean; yes "" | make oldconfig

---

