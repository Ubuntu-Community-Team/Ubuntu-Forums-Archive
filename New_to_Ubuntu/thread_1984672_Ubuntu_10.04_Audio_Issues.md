---
title: "Ubuntu 10.04 Audio Issues"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by Nick_Kats on 2012-05-22
Hey guys,
I have just purchased a new system (lga 2011, x79 chipset, motherboard: MSI X79A-gd45). I have installed Ubuntu 10.04 and when I plug in headphones on the back panel and/or the front jack, I have no sound.
When I go to System>Preferences>Sound to the Hardware Tab, I only see a
Manhattan HDMI Audio Output choice.
I should tell you that the HDMI output is from the video card.
Why is this happening?
How can I set the audio output to analog and use the back panel ports?

Thank you for your time

---

### Post by Tamlynmac on 2012-05-22
> Nick_Kats

Your mother board uses a Realtek ALC892 audio chipset. I recently built a machine that had the same chip and tried all the fixes on both the forums and the net. None of which worked. I finally just went to Walmart and picked up the least expensive PCIe audio card. Plugged it in and after boot my audio worked fine.

You can try all the fixes and hopefully you find one that works or you can just buy an inexpensive (or high end - pricey) pcie audio card and no longer worry about it. One should make sure that the new card doesn't use realtek. ;)

Good Luck & hope this helps.

---

