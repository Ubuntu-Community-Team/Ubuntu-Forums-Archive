---
title: "Intrepid and ATI Radeon"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Michl on 2008-11-14
I upgraded from Heron to Intrepid via update manager
and Intrepid reported that it did not recognize the
graphics card.  I ran this on on a Dell C610, which
has run ubuntu distros since Feisty including Alpha
and Beta versions of Gibbon and Heron without major
problems.

I'm not sure what a fresh install would do, but I'm
tired of reinstalling Heron.

---

### Post by igknighted on 2008-11-14
Can you post the results of the command 'lspci | grep VGA'?  Running it on a liveCD is fine.  ATI dropped support for some older (yet still common) cards in the driver that is included in II, so it is possible that your card is no longer supported.  The 'radeon' open source driver (not the fglrx one from ATI) has improved with specs released from ATI, so that might work for you.  Most people can run Compiz fine from that one.

---

