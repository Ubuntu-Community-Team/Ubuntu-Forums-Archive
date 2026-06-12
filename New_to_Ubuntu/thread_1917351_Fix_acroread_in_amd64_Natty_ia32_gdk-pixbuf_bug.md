---
title: "Fix acroread in amd64 Natty ia32 gdk-pixbuf bug"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by dixonstalbert on 2012-01-29
Hello all

Ubuntu 11.04 amd64  has a bug:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646954](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646954)

in how it handles 32-bit applications like AdobeReader (acroread) .

In my case, it manifested as a missing icon in the window list when acroread was running. Acroread firefox plugin is also badly behaved but I am not certain that is the same issue.

In any case, grand ubuntu sensei 'micove'  has kindly posted a ppa with a version of ia32-libs that fixes the bug.

The link to the ppa is in post #12 of the above launchpad thread. I edited the link to read '=natty' at the end as that is the version of ubuntu I am running.

After following instructions to add ppa to repository list, I opened synaptic and installed ia32-libs. Problems fixed!

The Launchpad thread has posts from ubuntu developers explaining the bug and why it will not be fixed until ubuntu 12.04 

A big thank you to micove for volunteering his time to fix this.

I use acroread several times a day as okular and pdfedit fonts are too blurry to use all day long.

---

