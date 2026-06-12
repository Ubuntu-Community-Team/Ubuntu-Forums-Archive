---
title: "Windows Media (wmv) files?"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-14
I'm running the ubuntu 11.04 DVD and I've managed to get adobe flash video to run with sound which is great.

As I'm sure you know, another very  popular video format on the web is Windows Media (wmv).  How do I go about enabling windows media videos linked from webpages while using ubuntu?  I've researched a little and the discussion gets into codecs and stuff.  Hoping there is a standard approach for ubuntu for this very common format?

I'm running the 11.04 DVD with the unity menu - where do I start?

Thanks.

---

### Post by LowSky on 2011-09-14
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Denver Dave on 2011-09-16
Thanks - with the ubuntu DVD, FireFox plays the wmv files just fine after the additional install mentioned.

I knew it must be possible, because after installing openshot, openshot played wmv files, but openshot did not seem to share this ability with other applications.

Thanks !

= = = = =
There was a confusing message screen at the end of the restricted installation for  "TrueType core fonts for the Web EULA".  Message said "IMPORTANT-READ CAREFULLY:".  Not that few ever do, but the <Ok> text is not clickable and no way to directly read the EULA.   Don't understand EULA's anyway, just thought interesting.

---

### Post by bkratz on 2011-09-16
> **Denver Dave said:**
> Thanks - with the ubuntu DVD, FireFox plays the wmv files just fine after the additional install mentioned.

I knew it must be possible, because after installing openshot, openshot played wmv files, but openshot did not seem to share this ability with other applications.

Thanks !

= = = = =
There was a confusing message screen at the end of the restricted installation for  "TrueType core fonts for the Web EULA".  Message said "IMPORTANT-READ CAREFULLY:".  Not that few ever do, but the <Ok> text is not clickable and no way to directly read the EULA.   Don't understand EULA's anyway, just thought interesting.


Usually (not always) if you press the tab key it will highlight the EULA accept tab so you can.

---

### Post by Denver Dave on 2011-09-20
I'll try the tab key for the EULA next time - thanks.

Reporting back.  The issue with the .wmv files seems to only be with the initial DVD.  When I install to USB and select install third party packages (or something to that effect), .wmv seems to work fine with FireFox.

---

