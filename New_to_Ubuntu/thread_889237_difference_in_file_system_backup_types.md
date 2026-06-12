---
title: "difference in file system backup types"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by rlaliberty on 2008-08-13
what is are the differences between the various methods for backing up the entire OS? im thinking of mainly just compressing the entire FS vs using a program like remastersys to create a liveCD. 

advantages? disadvantages?

---

### Post by Pro-reason on 2008-08-15
Remastering programs will try to preserve everything, but won't totally succeed.  Simply copying the hard drive means that every byte will be the same.  Remastering is better if you want to create something to install on several different machines.

---

### Post by yaztromo on 2008-08-15
I've only every used dd to create an exact image of the drive:

dd if=/dev/sda of=hdd.img

You can then compress with bzip2. Or if you like pipe the output of dd into bzip2.

Then when you want to restore the drive just

dd if=hdd.img of=/dev/sda

---

### Post by Pro-reason on 2008-08-15
> **yaztromo said:**
> 

You can then compress with bzip2.

For massive files, *lrzip* will get much better results than *bzip2*.

---

### Post by yaztromo on 2008-08-18
> **Pro-reason said:**
> For massive files, *lrzip* will get much better results than *bzip2*.

Just be aware you need good system specs for this program. My 20gb drive image was still crunching after 12 hours. lrzip will also scale to the amount of RAM you have, making your machine unusable while it's running.

---

### Post by Pro-reason on 2008-08-18
> **yaztromo said:**
> Just be aware you need good system specs for this program. My 20gb drive image was still crunching after 12 hours. lrzip will also scale to the amount of RAM you have, making your machine unusable while it's running.

You can tell it how much ram you want it to use.  (Even with restricted RAM, it will do better than bzip2.)  Plus, it runs with a high "nice" setting by default, so that other processes get CPU priority over it.

For huge files, I leave it running overnight.

If anyone is interested, you can get DEBs of lrzip on Launchpad.

---

### Post by yaztromo on 2008-08-27
lrzip keeps bombing out on me at random. Sometimes it will work sometimes it won't.

```

lrzip test.tar
Output filename is: test.tar.lrz
Illegal instruction

```

This is with the deb from launchpad. I'm prefering to use rzip which is more mature and stable, and is a more common format.

---

### Post by Pro-reason on 2008-08-28
> **yaztromo said:**
> lrzip keeps bombing out on me at random. Sometimes it will work sometimes it won't.
...
This is with the deb from launchpad. I'm prefering to use rzip which is more mature and stable, and is a more common format.

Yeah, *rzip* is good too.  You could even just use plain *lzma*, because even without the long-range stuff, it'll compress more than *bzip2*.

Pity that *lrzip* isn't working for you.  Have you tried the latest version from the PPA?  It might be an idea to report the bug to the developer (Con Kolivas).

---

### Post by yaztromo on 2008-08-28
> **Pro-reason said:**
> Yeah, *rzip* is good too.  You could even just use plain *lzma*, because even without the long-range stuff, it'll compress more than *bzip2*.

The Ubuntu server at work always has a dd'ed backup of it's system drive. Rzip compressed 40GB down to 800MB! I'm amazed.

> Pity that *lrzip* isn't working for you. Have you tried the latest version from the PPA?  It might be an idea to report the bug to the developer (Con Kolivas).

Thanks, I'll get in touch with him.

---

