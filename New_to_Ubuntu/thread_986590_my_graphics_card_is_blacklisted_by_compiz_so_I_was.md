---
title: "my graphics card is blacklisted by compiz so I was wondering if I could change it"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-11-18
Compiz has blacklisted my "Intel Corporation 82845G/GL"

I want to add the "Intel experimental modesetting" as default to Xorg.conf but I'm not sure how.

I'm using intrepid so I can't use "gksudo displayconfig-gtk" so please don't suggest that.

Anyone have an ideas??

Thanks!!

This is my xorg:
```


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

