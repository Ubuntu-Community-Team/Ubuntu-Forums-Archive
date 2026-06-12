---
title: "HELP! Recover Harddrive Data After Zero Out 512k"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by sherl0ck on 2008-05-25
Ok so i made a big mistake trying to fix a boot problem. I used the dd command to zero out the first 512k on /dev/hdc -- now i cant see any of the data. dumb i know.

here is the situation:
it was format as Linux LVM with a ext3 filesystem. It was in a volume group with another drive /dev/hdd. now i cant access the volume group. I had about 200GB of data on there. any ideas on how to access the data again.

---

### Post by ghantoos on 2008-05-25
Take a look at the following link.

It helped me more than once. : )

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

Cheers,

---

### Post by HotShotDJ on 2008-05-25
TestDisk, as recommended by ghantoos, saved me from an even worse mistake than you have made.  Of course, there are never any guarantees with this sort of thing, but I agree that it is your best chance.

---

