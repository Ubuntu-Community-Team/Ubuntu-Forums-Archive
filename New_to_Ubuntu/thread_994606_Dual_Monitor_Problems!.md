---
title: "Dual Monitor Problems!"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by SilverShadow118 on 2008-11-26
Hello again, world! Well, as the title says, I'm having problems. One monitor is hooked up to GFX card via a DVI to VGA adapter. The other is hooked up to the VGA port on my motherboard. I've downloaded the nvidia-settings repository and my second monitor is not detected by it. I looked up guides and other posts and they've just led me to a broken X.org many times. To put it simply, I don't know what to do. All help is greatly appreciated. Thank you.

---

### Post by overdrank on 2008-11-26
> **SilverShadow118 said:**
> Hello again, world! Well, as the title says, I'm having problems. One monitor is hooked up to GFX card via a DVI to VGA adapter. The other is hooked up to the VGA port on my motherboard. I've downloaded the nvidia-settings repository and my second monitor is not detected by it. I looked up guides and other posts and they've just led me to a broken X.org many times. To put it simply, I don't know what to do. All help is greatly appreciated. Thank you.

Hi and I understand your issue as you are trying to use two separate graphic cards. If you are using Hardy you may try and use the command ```
gksu displayconfig-gtk
``` and see if it will detect and use the second card.

---

### Post by SilverShadow118 on 2008-12-13
It's not detected :/

---

### Post by JKBurton on 2008-12-13
Do you have a second output port on your Nvidia card?  Mine has both a VGA and a DVI, and I have a display plugged into each one. nvidia-settings picked it right up.

I've tried the arrangement you have a couple of times on different Ubuntu versions, and never did get it working to suit me. The closest I ever got was to have two completely separate desktops running at the same time. Helpful, but not what I wanted. 

The third time I was going to try (um, maybe Ubuntu 7.10), I thought about how many hours I'd wasted on this problem and found an 8400GS card on-sale for $30. Two ports on the back, and no problems at all.

---

