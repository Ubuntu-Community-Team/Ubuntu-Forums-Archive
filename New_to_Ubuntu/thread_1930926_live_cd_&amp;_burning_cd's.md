---
title: "live cd &amp; burning cd's?"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by kurja on 2012-02-24
When I've booted from 10.04 LTS live CD, can I burn CD's (when I have only one optical drive)? It would seem logical that this can't be done as the OS is running from that CD, but I don't get any warning message or such, it just stays at the "preparing" phase indefinitely and nothing happens. Can it be done?

---

### Post by Lisiano on 2012-02-24
The second you eject your CD, you remove the root partition and because of this, Ubuntu can't load anything or do anything which is why you see it stay on "Preparing".
You need to tell Ubuntu to boot from RAM, as in, tell the CD to copy itself into RAM then run from there, this way you can eject the disk without making the system lose access to the root filesystem.
I don't exactly remember how to do it, but try this.

When booting, press F6 and type in ```
toram
``` just before the 2 dashes (--) so the line looks something like this
```
... boot=casper initrd=/casper/initrd.img toram --
``` then just press Enter, Ubuntu should boot into RAM and you should be able to eject the CD without freezing the whole system.

---

### Post by kurja on 2012-02-25
Thanks, I'll give that a try.

For the record, the whole system doesn't freeze when ejecting the cd, it keeps running, just produces errors when for an example trying to launch applications. Re-inserting the cd normalizes things. When trying to burn a cd, the burning process gets stuck to "preparing" but everything else continues to run.

---

### Post by kurja on 2012-02-25
worked like a charm, thanks!!!

---

