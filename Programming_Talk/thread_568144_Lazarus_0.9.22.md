---
title: "Lazarus 0.9.22"
date: 2007-10-05
forum: Programming Talk
---

### Post by billstei on 2007-10-05
Tried Lazarus 0.9.22 from/under Gutsy and it complains that it can't find the FPC source directory, and recommends pointing to it with Environment -> Environment Options -> Files -> FPC source directory, and setting this to /usr/lib/fpc/2.0.4/units/i386-linux (which contains directories like "rtl" et al) but it still complains saying that it should contain directories like rtl, packages, compiler... :lolflag: .  The config file /etc/fpc.cfg is the one that ppc386 (ppc386 points to /usr/bin/fpc ) finds/uses (checked with fpc -vt bogus ) so the only thing that might be iffy is there are two environment vars in fpc.cfg: $fpcversion and $fpctarget, and I'm unclear where these are set, although fpc reports that it's target is "Linux for i386" and uses the /usr/lib/fpc/2.0.4 path so it knows it's version number.

Not entirely sure yet whether these are fatal complaints or just silly complaints.  I'm still very new to Lazarus, but overall I'm very impressed with what I see.

Bill

---

### Post by billstei on 2007-10-05
Okay here's what I did:

Downloaded fpcbuild-2.0.4.tar.gz from Sourceforge project freepascal.  Unpack the archive into /usr/src.  Point Lazarus Environment Options setting (see above) to /usr/src/fpcbuild_2.0.4_exp/fpcsrc

Lazarus seems happy now.

Bill

---

### Post by billstei on 2007-10-05
Even easier: Download from [http://sourceforge.net/projects/lazarus](http://sourceforge.net/projects/lazarus) the deb package fpc-src_2.0.4-1_i386.deb  This will put the sources in /usr/share/fpcsrc and Lazarus will (probably) find it, or fix up the Environment FPC Source path accordingly.

Since Lazarus is somewhat "broken" right out of the box without this maybe it needs to be a dependency and in the Gutsy repos.

Bill

---

### Post by de_valentin on 2007-12-05
Yes, that last post did it for me!

---

