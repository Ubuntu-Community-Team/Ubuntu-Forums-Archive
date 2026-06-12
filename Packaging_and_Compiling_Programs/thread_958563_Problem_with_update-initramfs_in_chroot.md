---
title: "Problem with update-initramfs in chroot"
date: 2008-10-25
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2008-10-25
I'm not sure this is the right place to ask. I'm trying to build a customized version of Ubuntu following [these instructions]("http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd"). As you can see everything is done in chroot, starting with the mounted filesystem of a live cd.

I'm trying to replace usplash with a custom one, so I do the usual
```

update-alternatives --config usplash-artwork.so

```
and choose my usplash file. So it appears at the closure. If I want it to appear at the beginning I have to do
```

update-initramfs -u

```
but the output is
```

update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

This way at the beginning I still have the usual ubuntu usplash. Actually the livecd fstab is empty, so there is reason to complain. But how do I solve this issue?

It looks like a minor problem, but I cannot distribute my version until I remove all Ubuntu logos for trademark reasons. :(

---

### Post by YannBuntu on 2013-05-05
hi
I have exactly the same issue. Did you find a way ?

---

### Post by oldos2er on 2013-05-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

