---
title: "Upgradint from Release 15.10 (Wily Werewolf) 32-bit to 16.04 (Xenial)"
date: 2016-05-16
forum: New to Ubuntu
---

### Post by blaze24-matrix on 2016-05-16
After doing the upgrade, my PC is starting so slow (take to long to load), and i'm having some problem with my graphic card. The monitor is doing the on/off job few times. The problem could be the NVidia driver preinstalled? Right now i'm using Ubuntu Mate Release 15.10 (Wily Werewolf) 32-bit on USB with persistence, and it's working just fine. But on my sda1, with the upgrade i'm having problems. Anny help?

---

### Post by grahammechanical on 2016-05-16
Your thread title suggests that you upgraded from 15.10 32 bit to 16.04 64 bit. Did you upgrade in the sense of doing a fresh install of 16.04? One of the differences between a live session and an installed session is that the live session uses an open source video driver.

If you think that the problem is being caused by the proprietary video driver then change video drivers. Try using the open source video driver. I do not know how that is done using Ubuntu Mate but it should have a utility called Additional Drivers or something like it.

Regards.

---

### Post by oldrocker99 on 2016-05-16
On Ubuntu MATE, Additional Drivers is located in Preferences/Hardware. It does sound as though you're using the Noveau driver, which is inferior to the proprietary nVidia driver. That's opposite of ATI cards, for which the open source radeon driver is superior to the proprietary ATI driver.

---

### Post by Mark Phelps on 2016-05-18
Personally, I would advise against doing any in-place upgrades between Ubuntu versions. 

As an experiment, since it was offered, I upgraded my 15.10 installation to 16.04, and while it worked fairly well, insomuch as it at least didn't introduce any problems, after careful examination, I found that it had migrated NONE of the apps that I had installed via Synaptic and PPAs.

The PPAs, I could understand, but I though it would retain (or upgraded, where applicable) the synaptic-installed apps as it had a record of them.

I ended up downloading and reinstalling all the apps that didn't come preinstalled by default.

In the end, it was about as much work as a clean-install -- which is what I usually do.  Next time, I will do that.

My recommendation is to save off what you want to keep and do a clean-install of 16.04.

Good Luck

---

