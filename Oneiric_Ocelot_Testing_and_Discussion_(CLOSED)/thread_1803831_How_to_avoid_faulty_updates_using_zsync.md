---
title: "How to avoid faulty updates using zsync?"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-13
Hello,

Let's say I download and burn July 12 iso onto a CD, then find that an update later during the day borks Oneiric.  

Suppose a fix is announced on July 14.  

1. Can I download the July 14 zsync image, which is way smaller than the regular July 12 iso, in order to update the July 12 iso?
If so, how?

2. If I am too busy on July 14 and have to delay the task until July 16, can I use July 16 zsync file instead?

Thanks for your help.

---

### Post by linuxman94 on 2011-07-14
For zsync, as long as the file you are downloading with zsync is the same name as the older file it will update that iso.  So an example would be...
```
zsync http://cdimage.ubuntu.com/daily/current/oneiric-alternate-i386.iso.zsync
```

As long as you have an iso in the folder you are in with the same name it will update it.

---

### Post by 3vi1 on 2011-07-14
> **iClouseau88 said:**
> Hello,

Let's say I download and burn July 12 iso onto a CD, then find that an update later during the day borks Oneiric.  

Suppose a fix is announced on July 14.  

1. Can I download the July 14 zsync image, which is way smaller than the regular July 12 iso, in order to update the July 12 iso?
If so, how?

2. If I am too busy on July 14 and have to delay the task until July 16, can I use July 16 zsync file instead?

Thanks for your help.

I think you're confused about how zsync works.  You don't download the zsync file - that's done automatically when you run the zsync command.  The zsync file just contains checksums for the current iso.

Zsync compares those checksums to whatever existing file you have (it looks for one of the same name, but you can override that with -o) and then downloads the parts of the .iso that are different.  So, zsync will always be able to update the image you have - no matter how old it is, to the current version - it will just have to download more if it's been a while since you last ran zsync.

---

