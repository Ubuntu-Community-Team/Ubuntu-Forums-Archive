---
title: "upgraded and black screen"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2016-04-23
I upgraded to 16.04 last night. Now rebooting only to black screen. 
If I choose recovery I get the root. 
I also have an "Upstart" option in the boot options as well. 
If I use the Upstart. It will load to my desktop just fine. 

What would be the difference between the Upstart and the "normal" boot. 
Any Ideas on where to go from here would be great.

---

### Post by RobGoss on 2016-04-23
I have 16.04 and I've never seen a Upstart option have you try it?

---

### Post by BuzzStPoint on 2016-04-23
I have tried the upstart. It's the only way I can get to the desktop. 
Booting normally will only result in a black screen. It will just sit there and do nothing. If I press Ctrl, alt F1 It will bring me to console login. 

I've attached an image of the advanced boot options for my system.
[ATTACH=CONFIG]268568[/ATTACH]

---

### Post by RobGoss on 2016-04-23
Seeing this is the latest distro of Ubuntu 16.04 I have to ask you is this the first time installing Ubuntu for you?

Sometimes the ISO file we download may not be a good one and there for we might have to try yet another installation and see what the out come is..

At the bottom of the page has some helpful tip on how to check the [COLOR=#333333][FONT=Ubuntu]integrity of an ISO file[/FONT][/COLOR]
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by BuzzStPoint on 2016-04-23
I've installed other distros before. 
This one was Ubuntu/Kubuntu 15.10.

I was prompted to upgrade to the latest 16.04 so I decided to go for it. So something didn't take.

---

### Post by QIII on 2016-04-23
Hello!

Could you give us the hardware specs of your machine?

Were you using a proprietary video driver prior to upgrading?

Which one?

Did you remove it before upgrading?

---

### Post by BuzzStPoint on 2016-04-24
Yes I was using Intels driver 
Hardware specs:
```

2.40 gigahertz Intel Core i5-4210U
Slot 'ChannelA-DIMM0' has 4096 MB
WDC WD5000LPVX-80V0TT0 [Hard drive] (500.11 GB)
Intel(R) 8 Series Chipset Family SATA AHCI Controller
Intel(R) HD Graphics Family [Display adapter]

```

Also I did not remove Proprietary driver prior to upgrading.

Edit....
After trying several ideas from other sources. I just saved data and reinstalled from disk. After installing the OS from scratch everything came up like it should.
Reinstalling all my apps now..

---

