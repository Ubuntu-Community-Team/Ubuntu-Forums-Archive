---
title: "can't find integrated graphics drivers"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by hopefulkayaker on 2012-05-22
Because of an obnioxus hardware problem I won't get into in this thread, I removed and threw away my Dell Inspiron 530 desktop's dedicated video card in favor of its integrated garphics. I also switched my display from HDMI to VGA, since my tower doesn't have an HDMI port.

However, my screen looks blurry. I knew the graphics quality would not be as crisp as with HDMI, but I've only been sitting at the computer for 15 minutes or so and it's already giving me a headache.

I hope this is a driver issue. I used the Additional Drivers application, which just told me I have no proprietary drivers active.

I visited the manufacturer's page for drivers for my system, but I'm not really sure what I'm looking for. I tried both available chipset drivers, only to see the ominous and bizarre error message: 

"This computer does not meet the minimum requirements for installing the software."

Help! I hope I'm not doomed to blurriness.

---

### Post by Mark Phelps on 2012-05-23
It would help to know more about your integrated graphics chip.

To get that info, open a terminal and enter "lspci" -- and look for the line containing "VGA".  Post that line back here.

---

### Post by hopefulkayaker on 2012-05-23
I get the following with lspci:

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

---

