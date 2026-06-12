---
title: "ati s-video problems"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by mbzn01 on 2013-11-28
Hi there

Struggling to set up a pc to my tv, i have an ati card (radeon 3600) with the right addaptors(got it to work in winxp). I dont have any additional driver installed.
so the only suggestion i could find was 
[https://wiki.ubuntu.com/X/Config/SVideo](https://wiki.ubuntu.com/X/Config/SVideo)
and the answer i get from the machine was 
output S-video not found and then something like ignoring output parrameter.

now the interface on the ati card is converted to s-video with the standard ati cable(s-video in/out and composit in/out) this setup worked in windows so it should here

when i go to system settings / displays / it gives me 3 interfaces ie. dvi0, dvi1 and din.

How could i force enable the din interface to my tv?

Thanks in advance

---

### Post by Mark Phelps on 2013-11-28
> this setup worked in windows so it should here

Actually -- NO.  The two are totally unrelated in terms of video drivers -- which is what governs how well the S-Video jack works.

Sorry, but ATI dropped Linux drivers for your card several years ago.  Today, you have the default open-source Radeon driver installed, and if that doesn't support S-video output, then you're simply out of luck.

---

### Post by squakie on 2013-11-28
You say the svideo output is done with the cables - does the PC actually have an svideo jack?

---

