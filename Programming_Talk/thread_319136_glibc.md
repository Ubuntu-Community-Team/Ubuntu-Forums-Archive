---
title: "glibc?"
date: 2006-12-15
forum: Programming Talk
---

### Post by Starcraftmazter on 2006-12-15
Hello.

I just installed ubuntu 6.06 for home use. I now need to install lamp. I will be building everything from source. I have some experience with this, reconfiguring and rebuilding php when adding extensions on a remote centos box.

Now, when getting mysql (I don't want the special ubuntu one), whats the difference between these two:

Linux (x86, glibc-2.2, "standard" is static)
Linux (x86)

Thanks!

---

### Post by ZERO_SHIFT on 2006-12-15
Maybe one is a dependent on the other?

---

### Post by Starcraftmazter on 2006-12-15
Thats what I figured, but then does Ubuntu come with glibc or not? And what is it anyway?

Come on, I need more info :confused:

---

### Post by ZERO_SHIFT on 2006-12-15
Why dont you just install both?

---

### Post by Starcraftmazter on 2006-12-15
Both contain mysql, one has glibc and one doesn't (as far as I understand). No need to install something already there, I just want to know if I need to or not....SURELY at least one person here knows?!

---

### Post by yabbadabbadont on 2006-12-15
glibc is the standard C shared library that exists on all linux machines.  The difference between those two downloads is that one of them has already been statically linked to the exact version of glibc it needs and so won't use the one already on the system.  The other has been dynamically linked and will (try to) use the glibc shared library that is already installed.  Your safest choice would probably be to get the version that has been statically linked.

---

### Post by Starcraftmazter on 2006-12-15
Thanks :D

---

### Post by yabbadabbadont on 2006-12-15
Just for completeness: [http://en.wikipedia.org/wiki/Glibc](http://en.wikipedia.org/wiki/Glibc)

---

### Post by winch on 2006-12-15
If you want to build everything from source you need to download the source not precompiled binaries. It's a long time since I last built mysql from source but back they didn't make the source downloads obvious, you had to look for them.

I'd apt-get mysql myself. it's less hassle unless there is something wrong with the ubuntu packages?

---

### Post by Starcraftmazter on 2006-12-15
Yeh, they're ages out of date.

---

