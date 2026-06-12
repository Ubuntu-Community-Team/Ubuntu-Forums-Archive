---
title: "Hardy 8.04 Crashes Switching from AC to Battery"
date: 2014-11-11
forum: New to Ubuntu
---

### Post by jakfish on 2014-11-11
Given the hardware/wifi issues of an HTC Shift x9500 umpc, I have to run Hardy 8.04.  Everything is fine except when I switch from AC to battery.

Upon pulling the plug, the cursor spins for ten seconds and the screen/keys freeze.  This forces a hard shut-down.

This is a dilemma since I work off an external battery (which the machine sees as ac power) and when the external battery depletes, the machine goes to battery and crashes.  I have tried 10.10 and 14.04 and I do not have this problem (but I have unsolved hardware issues with these later OSs).

However, if I start the Hardy OS on battery, fully load Hardy, then switch to AC (or external battery), then back to battery, the machine does not crash.

Is there a handle I can jiggle?  And my apologies for making veteran users cast their minds back to ancient Ubuntu versions :)

Jake

---

### Post by bapoumba on 2014-11-11
Well, memory might not be enough :)
What kind of harware problems are you having ? It is really not recommended to run an ancient outdated release, you must be aware of that. It would be better you outline your issues and see if you can be helped out with a supported release.

---

### Post by jakfish on 2014-11-11
Thank you for your very quick reply.

As for updating an Ubuntu OS for the Shift x9500, there is a world of difficulty, mostly concerning the dreaded Marvell SD8686 embedded internal wifi.  (though touch screen/calibration and the low-powered CPU also present difficulties when running current Linux)

This magician successfully set up Hardy:

[http://pof.eslack.org/2008/04/14/linux-on-htc-shift/](http://pof.eslack.org/2008/04/14/linux-on-htc-shift/)

Here are some key links about the SD8686:

[http://www.armadeus.com/wiki/index.php?title=Libertas_driver](http://www.armadeus.com/wiki/index.php?title=Libertas_driver)

[http://wireless.kernel.org/en/users/Drivers/libertas](http://wireless.kernel.org/en/users/Drivers/libertas)

[http://forum.tinycorelinux.net/index.php?topic=16963.0](http://forum.tinycorelinux.net/index.php?topic=16963.0)

Somebody on the Shift forum got Ubuntu 10.10 to work with the wifi using the libertas 9.7 firmware installed though package manager.  I like the other users there could not get the wifi recognized:

[http://forum.xda-developers.com/showthread.php?t=476858&page=6](http://forum.xda-developers.com/showthread.php?t=476858&page=6)

More info than you wanted, I'm sure, but just trying to show that this is a thorny problem :)

Jake

---

### Post by bapoumba on 2014-11-11
I see.. I looked around and hmmm.

---

### Post by jakfish on 2014-11-11
Anything come to your mind about the Hardy AC-to-battery issue?

---

### Post by bapoumba on 2014-11-11
Nope, I used Hardy such a long time ago :)

---

### Post by JeQhdMD on 2014-11-11
Well, **if wireless is main issue** account non-marvellous wifi hardware, use of the atheros open source wifi chipset will fix issue, either running Hardy, or running Trusty:

note that plug & play for Hardy limited to atheros (TP-Link TL-WN722N w/ar9271 & ath9k_htc.  ).   The RTL chipsets listed are also P & P on Ubuntu 12.03 & newer, but not on prior versions - - however, the drivers can be built to run.

Below are usb wireless adapters I own & have tested on multiple devices and versions of Ubuntu & Mint.   Google amazon for availability/prices.

[TABLE]
[TR]
[TH]Brand[/TH]
[TH]Model[/TH]
[TH]Chipset[/TH]
[TH]Driver[/TH]
[TH]Plug and Play[/TH]
[TH]Phone[/TH]
[/TR]
[TR]
[TD]TP-Link[/TD]
[TD]TL-WN722N[/TD]
[TD]AR9271[/TD]
[TD]ath9k_htc[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]TP-Link[/TD]
[TD]TL-WN822N[/TD]
[TD]AR7010[/TD]
[TD]ath9k_htc[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]"""""[/TD]
[TD]"""""[/TD]
[TD]AR9287[/TD]
[TD]"""""[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD] Airlink[/TD]
[TD]AWL5088[/TD]
[TD]RTL8188CUS[/TD]
[TD]???[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]""""[/TD]
[TD]""""[/TD]
[TD]RTL8192CUS[/TD]
[TD]???[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Panda[/TD]
[TD]Ultra Wifi[/TD]
[TD]RTL8188CUS[/TD]
[TD]???[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]""""[/TD]
[TD]""""[/TD]
[TD]RTL8192CUS[/TD]
[TD]???[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Edimax[/TD]
[TD]EW-7811UN[/TD]
[TD]RTL8188CUS[/TD]
[TD]???[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]ASUS[/TD]
[TD]USBN13[/TD]
[TD]RTL8188CUS[/TD]
[TD]???[/TD]
[TD]Yes[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by jakfish on 2014-11-15
JeQhdMD,

Sorry for my late reply.  I had instant email notification, but something went awry.

Thank you for the wifi info.  For posterity, this works too, OOTB, with Xubuntu 14.04/HTC Shift x9500:

[http://www.ebay.com/itm/151020085653?_trksid=p2059210.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.com/itm/151020085653?_trksid=p2059210.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT)

Since the Shift comes with just one usb, I'm trying to keep the slot open, which is why I struggle with Hardy rather than using 14.04 (which I have on another partition).  The Marvell stuff is so hostile to linux, though it vexed me on Vista Ultimate as well.  Why companies contract this hardware is beyond me.

Thanks again,
Jake

---

