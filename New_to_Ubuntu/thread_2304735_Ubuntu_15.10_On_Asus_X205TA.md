---
title: "Ubuntu 15.10 On Asus X205TA"
date: 2015-11-29
forum: New to Ubuntu
---

### Post by stephen91 on 2015-11-29
I am an experienced Windows user branching into Ubuntu now. I have an Asus X205TA running Windows 10 and I was thinking of scrapping Windows 10 and replacing it by Ubuntu 15.10. My searches indicate that there seem to be many problems installing and running Ubuntu on this box. I am trying to get a clear answer on whether or not Ubuntu 15.10 can successfully run on the Asus and if it does what would be the best way to install it cleanly.

There are so many threads about this topic it is difficult for a newbie to get a concise status update.

Thank you in advance for your feedback.

---

### Post by songangda on 2015-12-10
It depends on how you define the phrase "successfully run."

Ubuntu 15.10 64 bit does boot on this device. You will need a 32 bit grub to boot on a pure 32 bit UEFI.
Graphics, keyboard, touchpad, sdcard reader are all working fine.
Starting from kernel 4.1, Wi-Fi works but requires some configuration (which is not very friendly to a new linux user) and it is not stable. At least not on my x205ta.
At this moment, audio is not working on most (if not all) x205ta models.

If you consider boot and a basic working environment without much multimedia (i.e. audio) as "successfully run", then it can successfully run.
If you want to play music or watch YouTube which requires the audio support and a solid wireless connection, then it cannot successfully run for now.

---

