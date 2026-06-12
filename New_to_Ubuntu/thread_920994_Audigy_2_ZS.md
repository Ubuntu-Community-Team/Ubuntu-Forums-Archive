---
title: "Audigy 2 ZS"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by mickeykool on 2008-09-15
I'm having problems w/ the sound not working.  I have done a number of things and from what I see I have 2 sound cards.  One is an onboard card and other one is Audigy card.   As of running  alsamixer- cmd I see the via onboard card listed.  So my question is how to make the Audigy card the default card?   I have the onboard card disabled in my bios but still shows VIA listed.  

Thanks

---

### Post by MegaJim on 2008-09-15
You can try alt+f2 then type gstreamer-properties and hit enter; it should allow you to select which card is used for sound output.  I would also double check your bios settings are correct as regards the onboard card as any program that doesn't use gstreamer will also have to be configured.

---

