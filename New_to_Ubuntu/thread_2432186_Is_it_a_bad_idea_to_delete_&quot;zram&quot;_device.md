---
title: "Is it a bad idea to delete &quot;zram&quot; devices on my HDD?"
date: 2019-11-28
forum: New to Ubuntu
---

### Post by random turnip on 2019-11-28
I've recently been reviving an old laptop and the first thing I want to do was completely format the HDD (there's no data I want on there and I had a malware scare which was probably just me being paranoid).  When doing this, under the devices there was the main internal HDD and 2 others called zram0 and zram1.

A little bit of Googling taught me that these are created by the kernel and not to be worried about, but as I mentioned I want to be 100% sure no malware could survive my re-installation of Lubuntu, and I'm thinking that there's a chance some malicious code could be living in there.  I've seen both sides of the argument; that deleting it could damage the system beyond repair or that it could do nothing at all.  I don't really understand how deleting things off a HDD I intend to re-format could damage my system, but I'm no expert.

So, to be 100% sure, is it worth deleting these "devices" from my harddrive or is that going to kill my machine?  Is it even possible that malicious code could be hiding there when they're only even visible when in the partition editor?

Also, I assume creating a new partition table and a whole new ext4 partition for Lubuntu is going to make 100% sure nothing can still be lurking in there?
I'm doing all this with the KDE partition editor on the Lubuntu Live CD by the way.

---

### Post by Impavidus on 2019-11-28
zram is a block device (that's why you find it in /dev) with compressed data, existing in ram. So it's not on your hard drive. It's used by your live disk. The contents of zram don't survive a reboot.

---

### Post by random turnip on 2019-11-28
Thanks, that clears it up. Won't worry about it then, I dare connect my laptop to my network again.

---

