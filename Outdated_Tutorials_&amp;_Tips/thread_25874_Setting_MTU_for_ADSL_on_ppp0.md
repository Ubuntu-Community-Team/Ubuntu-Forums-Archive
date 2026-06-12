---
title: "Setting MTU for ADSL on ppp0"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by mrsuicide on 2005-04-11
I want to set an MTU different than 1492 for my ADSL connection on ppp0.
Howto do that?

It's always reset to 1492 a boot time... :neutral:

EDIT: Move me to another forum section.

---

### Post by philcolbourn on 2005-04-11
[http://www.ubuntuforums.org/showthread.php?t=24706](http://www.ubuntuforums.org/showthread.php?t=24706)

I presume your are using PPPoE. for pppoA(VC mode) use 1478. for PPPoA (LCC mode) use 1474 - these are my figures. I know that 1478 is optimum for PPPoA using VC mode and this gives the best ADSL performance theoretically).

The theory I believe is as follows:

31 ATM cells * 48 bytes is 1488 bytes. This holds the PPPoA (VC) bits (8 bytes) and PPP header (2 bytes) making the MTU 1478. in PPPoA LCC mode there is an extra 4 byte LCC header.

---

