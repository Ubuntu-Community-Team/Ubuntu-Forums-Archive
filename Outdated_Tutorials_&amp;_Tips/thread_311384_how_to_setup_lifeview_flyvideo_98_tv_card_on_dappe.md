---
title: "how to setup lifeview flyvideo 98 tv card on dapper"
date: 2006-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by ryu kun on 2006-12-02
Here I'll explain how I set up my Lifeview Flyvideo 98 TV Card on Dapper. It was little hard to find it on the net, I'll try to make it simple. It may also helpful to setup other tv cards.

In terminal, run:

```
sudo gedit /etc/modprobe.d/bttv
```

Put these lines into the file and save.

```
alias char-major-81-0 bttv
options bttv card=21 tuner=5 radio=0
```

21 means Flyvideo 98 in Linux Kernel 2.6.11.
5 is for tuner which is probably Philips PAL BG in this card.

If you have a different tv card you can find these numbers here:
[http://linuxtv.org/v4lwiki/index.php/Cardlist.BTTV]("http://linuxtv.org/v4lwiki/index.php/Cardlist.BTTV")

Now reboot.

You can use "tvtime" for scanning your channels.

```
sudo aptitude install tvtime
```

You'll find Tvtime in Applications - Sound & Video menu. Click to screen, select Channel Management and Scan your channels. Enjoy.

Some useful links:
[how to install bt878 tv cards]("http://ubuntuforums.org/showthread.php?t=153935")
[bttv driver setup]("http://ubuntuforums.org/showthread.php?t=190219")
[PixelView PlayTV Pro PV-BT878P+9X installation under Linux]("http://www.burghardt.pl/wiki/articles/pixelview_playtv_pro_pv-bt878p_9x")
[Bt878 Video Capture card recognised, not working]("http://ubuntuforums.org/showthread.php?t=260516&highlight=bt878")
[Useful page for TvTunerCards]("http://www.wlug.org.nz/TvTunerCards")

---

