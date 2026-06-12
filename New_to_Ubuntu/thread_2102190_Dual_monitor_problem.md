---
title: "Dual monitor problem"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by magnesium02 on 2013-01-06
I'm using Ubuntu 12.04 LTS (32-bit).

So far I was using an old 20'' monitor connected via VGA cable. Now I additionally bought a 24'' monitor (Dell UltraSharp U2412M) to use both monitors in a dual setup. The Dell monitor is connected via DVI-to-HDMI cable. Both monitors work like a charm separately when the other one is switched off in the display settings, and also as mirrored displays they're ok (although the resolution is suboptimal for the Dell), but that's basically not what I want. When I deselect mirror displays and try to activate both monitors at once, I get the following error message:

"The selected configuration for displays could not be applied. Required virtual size does not fit available size: requested=(3600, 1200), minimum=(320, 200), maximum=(1920, 1920)."

Yep, I had 1920 × 1200 for the Dell and 1680 × 1050 for the old monitor (makes 3600 × 1200 together, so I suppose this is what the requested size is referring to).

Here's what I did so far:

Immediately tried out lower resolutions. This does not help, because I do not really get below this maximum of 1920 × 1920.

I thought at first that it might have to do with my graphics card (AMD Radeon HD 6450), but as far as I understand, it should not be a problem to use 2 monitors in an acceptable resolution with this card. I also tried exactly the same setup, same monitors, same graphics card in Windows 7 and there it worked out of the box. Monitors automatically detected, left and right monitor correctly displayed, high resolution automatically set. So the graphics card should be ok I guess...

I then checked in the System Settings which drivers for the card were activated – no proprietary drivers until then (strangely, because I think I did that not long ago), with two options displayed:

ATI/AMD proprietary FGLRX graphics driver
ATI/AMD proprietary FGLRX graphics driver (post-release updates)

Installed the first one – did not fix the problem.
Installed the post-release updates – installation did not work (maybe because of the driver I had just installed?) and at the same time killed this other proprietary driver. Did not fix the problem, obviously.

Alternatively, I then downloaded and tried to install the appropriate driver from AMD support according to these instructions:
[http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation) (sorry it's just in german) but this also did not help. Although, according to the output I get with the command fglrxinfo, the installation should have worked...

I'm lost...

Any help very much appreciated.
Thx in advance.

---

