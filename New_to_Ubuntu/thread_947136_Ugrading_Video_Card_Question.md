---
title: "Ugrading Video Card Question"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by false_apology on 2008-10-14
Hey Experts,

I have a mythTV box, build from some old hardware, that is a constant "work in progress". I originally used a PCI NVidia card I had from on old build, but I've read I'd get much better HDTV performance using AGP. I'm considering doing "the ebay shuffle" to get an AGP card, but I'm not entirely sure how easy the upgrade process will be. My old card is an Nvidia GeForce 5200. If I get another nvidia card, can I just pull out the old PCI card and put in the AGP card and it will just work? Do I have to do any sort of special driver manipulation since I'm going from AGP to PCI (and a different chipset, maybe geforce 6200)? I believe I am using the "NVidiaProprietaryDriver" at the moment (to be able to use XvMC, etc).

I really want to avoid having to do a fresh install as I am happy with how thing are setup and I don't want to go through all the configuration steps again.

Thanks a lot everyone.

---

### Post by bumanie on 2008-10-14
Theoretically ubuntu is programmed to recognize new hardware, therefore, it should not be a problem. I would remove the nvidia driver back to the standard linux vesa driver, then switch the graphic cards and assuming the new hardware is recognized, download the the appropriate driver again (usually the one in the repoistories is fine). Hope it works without hassles.

---

### Post by false_apology on 2008-10-14
> **bumanie said:**
> Theoretically ubuntu is programmed to recognize new hardware, therefore, it should not be a problem. I would remove the nvidia driver back to the standard linux vesa driver, then switch the graphic cards and assuming the new hardware is recognized, download the the appropriate driver again (usually the one in the repoistories is fine). Hope it works without hassles.

Thanks for the advice bumanie. I was wondering if you could point me to some tutorials on how to remove the proprietary drivers? And I'm guessing I can use an "apt-get" command to re-download them after I have the new card? I tried reading the manual steps on the nvidia website, and its pretty tricky, I have to configure it to boot w/o X, etc etc, and I'm guessing there is an easier way to do it.

---

