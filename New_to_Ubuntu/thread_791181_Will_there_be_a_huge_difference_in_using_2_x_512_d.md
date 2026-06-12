---
title: "Will there be a huge difference in using 2 x 512 ddr2 ram and 1x 1gb ddr2 ram?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by sharks on 2008-05-11
I have decided to buy 1gb ddr2 ram .Will there be a huge difference in using 2 x 512 ddr2 ram and 1x 1gb ddr2 ram?

---

### Post by Ocxic on 2008-05-11
Short answer: no
Long answer: not really going to be a huge difference, but I would go with 2 sticks of 512 dual channel ram, this will allow your computer to access either ram stick individually for a better performing memory system.

---

### Post by Scheater5 on 2008-05-11
It is my understanding that, due to the sharing of memory across two modules, 2x512 would actually be FASTER than 1x1GB.  But I doubt it would be monumental.

---

### Post by tamoneya on 2008-05-11
agreed.  Also the second case would only apply if your motherboard supports dual channels.  Not all motherboards will do this especially older ones.

---

### Post by sharks on 2008-05-11
My mobo supports dual channel.

---

### Post by tgalati4 on 2008-05-12
Dual channel can be 10% faster than single channel.  I ran some tests using memtest several months ago on a Gutsy build.  The other advantage of dual channel is that some motherboards allow higher overclocking speeds in dual-channel mode and less CAS wait-states (4 vs 5 for example) which can boost performance.

Whatever configuration you choose, run memtest for at least 30 complete test cycles to test both memory and data bus integrity.

---

