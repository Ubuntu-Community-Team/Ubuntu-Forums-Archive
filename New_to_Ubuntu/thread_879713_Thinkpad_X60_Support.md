---
title: "Thinkpad X60 Support"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by kuhbus on 2008-08-04
Hi guys!

Im new to (x)ubuntu and wanted to ask, where the best place to look for drivers for my lenovo thinkpad x60 would be? I wished to use the additional keys (volume,...)

cheers

---

### Post by Funk Phenomena on 2008-08-04
I have a thinkpad with a P3 800mhz cpu and Ubuntu installed.  Have you tried installing either xubuntu or ubuntu to check functionality?

---

### Post by abgemacht on 2008-08-04
If you haven't already, check out [http://thinkwiki.org]("http://thinkwiki.org")

That's where I got most of my info for my T60p.  It's a great site.

---

### Post by LowSky on 2008-08-04
X60 should work, only because my T60 is nearly the same. Worst thing will be ATI drivers. just use a program called EnvyNG. you'll be fine

---

### Post by kuhbus on 2008-08-06
unfortunately, my main problem is the wifi driver.

i have an atheros ar5212 chip. In the GUI everything looks fine. Networks are detected and displayed, even with signal strength and so on, but sadly it is not possible to connect to one of those networks.

I have the newest xubuntu and it ships with the latest madwifi driver (MadWifi v0.9.4). It "SHOULD" work I think, but it doesnt....

---

### Post by halitech on 2008-08-06
are you using WEP/WPA/WPA2 on your router? 

by "not connecting" what do you mean?

---

### Post by kuhbus on 2008-08-06
I tried 2 networks. One protected with WPA, one used WPA2. I know the keys. 

By not connecting I mean, that after I trigger "Connect to ABC" using the GUI, it tries to connect for a minute or so and fails in the end raising an error message like "couldnt connect".

---

### Post by halitech on 2008-08-06
can you try disabling the protection, just to make sure the card is working properly? I know I have trouble with mine connecting and staying connected if I have either enabled.

---

### Post by kuhbus on 2008-08-07
Hi! yes, just tried it without any security protection. unfortunately it is the same: no connection is established

---

### Post by kuhbus on 2008-08-07
I also installed the newest WLAN driver module ath5k from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

basically the same things happen. But with the ath5k driver even the networks are not listed.

but by trying to connect it is the same. 1 minute it "tries" , afterwards nothing happens....

---

### Post by kuhbus on 2008-08-14
okay, finally I got it.

It didnt work with the newer ath5k. It also didnt work with the stable 0.9.4 release which is included in xubuntu.

I had to install the HEAD version of the (legacy) madwifi driver.

---

