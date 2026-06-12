---
title: "Unable to connect to Wi-Fi in Ubuntu 14.04"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by Yasaswy on 2014-05-17
This is my first time ever installing and using Ubuntu so please bear with me. I am a noob when it comes to commands that Ubuntu uses.

I am trying to connect my Edimax AC600 Wireless Dual Band USB mini USB Adapter. When I tried installing this in Win 8.1, it kept BSODing me because I had to install the drivers before I could use it. I don't really know how I install the drivers here in Ubunutu. I tried looking online for hours but no luck. I tried using "lusb" and it shows up there. But when I tried to see if I can update in via Additional Drivers, it searches for a while and says "No Additional drivers are available." I downloaded the drivers from their website but I have zero clue of how to install this driver. Can anyone help me out with this situation?

---

### Post by squakie on 2014-05-18
First, let's get some detail on the adapter:

please do the "lsusb" again with the device plugged in and post the output back here.

---

### Post by claracc on 2014-05-18
> **Yasaswy said:**
> This is my first time ever installing and using Ubuntu so please bear with me. I am a noob when it comes to commands that Ubuntu uses.

I am trying to connect my Edimax AC600 Wireless Dual Band USB mini USB Adapter. When I tried installing this in Win 8.1, it kept BSODing me because I had to install the drivers before I could use it. I don't really know how I install the drivers here in Ubunutu. I tried looking online for hours but no luck. I tried using "lusb" and it shows up there. But when I tried to see if I can update in via Additional Drivers, it searches for a while and says "No Additional drivers are available." I downloaded the drivers from their website but I have zero clue of how to install this driver. Can anyone help me out with this situation?

In order to install the wifi drivers for ubuntu, here you have edimax page where you can download the driver for linux: [http://www.edimax.com/en/support_detail.php?pd_id=498&pl1_id=28&pl2_id=138](http://www.edimax.com/en/support_detail.php?pd_id=498&pl1_id=28&pl2_id=138) , go to the bottom part of the page and select driver to download the one for linux (is a .zip file). Is it the same you have yet downloaded?

Then, you have in the same page a quick installation guide: [http://www.edimax.com/images/Image/QIG/Wireless/EW-7811UTC/EW-7811UTC_QIG_EN%28English%29.pdf](http://www.edimax.com/images/Image/QIG/Wireless/EW-7811UTC/EW-7811UTC_QIG_EN%28English%29.pdf) , go to linux part, and as I understand you will have to compile the wifi driver for your system. All steps are given there.

Note, the guide is made for ubuntu 12.04, What ubuntu do you have?.

---

