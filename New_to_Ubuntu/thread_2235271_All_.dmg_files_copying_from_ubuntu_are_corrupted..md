---
title: "All .dmg files copying from ubuntu are corrupted."
date: 2014-07-20
forum: New to Ubuntu
---

### Post by kristan97 on 2014-07-20
I use Ubuntu on my desktop to store my documents and softwares. I transfered them from my Mac (Mac OSX 10.9.4) to my Ubuntu desktop (Ubuntu 13.10) via AFP using 1gigE. When I needed my softwares back, I realised that all my softwares in .dmg form have corrupted in Ubuntu. Problems such as, Invalid Checksum, No mountable Filesystem appear when opening any .dmg file. I transfered them without any errors, but why will they become corrupted?

---

### Post by bapoumba on 2014-07-20
Was the partition you backed them up HFS ? May be a permission problem. If you check them up in DiskUtility, what does it say ? Is it read/write ?
I always backup my dmg from MacOS to a HFS drive.

---

### Post by buzzingrobot on 2014-07-20
Here's a Wikipedia page about dmg's: [http://en.wikipedia.org/wiki/Apple_Disk_Image](http://en.wikipedia.org/wiki/Apple_Disk_Image).  It points out that the dmg format is proprietary to Apple and they haven't released it.  A few open source tools for handling dmg's are mentioned, as is the phrase "provided hfsplus support has been enabled".

I used OS X and Linux together for several years but have to admit I don't recall trying to open a dmg on Linux.

---

