---
title: "ATI Mobility Radeon's (Before the HD's)"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by martypastor on 2012-08-04
I have an ATI Mobility Radeon X700 (0x5652) installed on my laptop running Ubuntu 11.04 (Natty Narwhal).

If I may ask, is the FGLRX drivers will work for my graphics card? I know the latter versions may not be compatible with my card, however, would the old versions of FGLRX work on 11.04? 

I just wanted to control the graphics card though, rather than modifying the xorg.conf again.

Thanks :)

---

### Post by kaldor on 2012-08-04
Newer versions of FGLRX, as you said, will not support this card. It is not at all recommended to attempt using an outdated version of FGLRX, and it most likely will not work anyway (kernel support, etc).

At this point the Radeon open source driver is quite mature for older chips. You should also look at upgrading from 11.04 to 12.04 because there were a lot of improvements on the graphics front.

Unsure about a simple way to modify settings, though. Hope I at least cleared up the question :)

---

### Post by prshah on 2012-08-04
> **martypastor said:**
> I have an ATI Mobility Radeon X700 (0x5652) installed on my laptop running Ubuntu 11.04 (Natty Narwhal).

If I may ask, is the FGLRX drivers will work for my graphics card? 


ATI's mobility series use the mach64 module/driver; unfortunately, you cannot use it with fglgrx.

The mach64 driver should be automatically detected and loaded; you shouldn't need to touch the xorg.conf / xorg.conf.d

Are you facing any particular issues?

---

### Post by martypastor on 2012-08-05
> **prshah said:**
> Are you facing any particular issues?
 
Well,  in the Wine part, the applications doesn't detect the graphics card (such as BMW M3 Challenge). In the ubuntu part, it works flawlessly though.

> Unsure about a simple way to modify settings, though. Hope I at least cleared up the question :smile:

Oh yes you did. the Wine part will be my problem now, coz the 3D apps doesn't seem to detect the graphics card. :(

---

### Post by Mark Phelps on 2012-08-05
To run Windows stuff under Wine, you would most likely need the features provided by the fglrx drivers -- which you can't get with recent Ubuntu versions and your legacy card.

There's basically nothing you can do as your card is not compatible with the newer AMD drivers, and your Ubuntu version won't run the older ATI drivers.

---

### Post by martypastor on 2012-08-07
Guess I'll just find alternatives on my Windows stuffs. 

Sadly, as of now, the texture compression, of the open source drivers of ATi were not available. Oh well, I'll just have to wait then.

Thank you all for the help and advice :)

---

### Post by mastablasta on 2012-08-07
as mentioned newer version of ubuntu has newer drivers built in. so you may want to try it out.
 
additionally there is xorg edgers PPA.
 
and in wine sometimes things have to be setup a bit different that in windows. for example i couldnt' run diablo 2 well (either poor graphics or not running porpperly), however someone on forums provided me a link to openGL patch and i could run it perfectly with that one.
 
unfortunatelly i do not know anything about your windows programme. but it's good to look first on wine appplicaiton database for any additional tips and tricks.

---

### Post by kaldor on 2012-08-09
> **martypastor said:**
> Guess I'll just find alternatives on my Windows stuffs. 

Sadly, as of now, the texture compression, of the open source drivers of ATi were not available. Oh well, I'll just have to wait then.

Thank you all for the help and advice :)

Just checked this thread, and I might have some advice regarding WINE games with the open source drivers.

Ubuntu 11.04 shipped with a slightly old graphics stack. There were major improvements to some drivers in later versions. Also, many WINE games probably take advantage of patented or restricted features that have to be enabled by the user in order to avoid legal issues. 

So, my recommendation is to do a clean install of Ubuntu 12.04 and then install [this PPA]("https://launchpad.net/~oibaf/+archive/graphics-drivers/"). The PPA contains more recent versions of the open source graphics drivers, and I believe it enables certain features (such as S3TC- without it, many games cannot run) that aren't able to be included in distributions by default.

I've never used the PPA myself, but I've heard of others using with success. If using a more recent Ubuntu distro with that PPA doesn't cut it, then I think you might just be out of luck :(

---

