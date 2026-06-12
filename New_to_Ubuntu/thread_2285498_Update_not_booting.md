---
title: "Update not booting"
date: 2015-07-06
forum: New to Ubuntu
---

### Post by wyvern3 on 2015-07-06
I've been wanting to try out Linux for quite a while now. I was recently given a couple of old computers since Windows is no longer supporting xp. On the 4th I was able to install Xubuntu 14.04 and other than a screen flicker everything worked fine. I had previously tried to install 15.04 and it wouldn't boot. After I installed it I changed the screen refresh rate from 87.0Hz to 85.0Hz and it worked fine. I noticed that it also works on any settings other than 70.0Hz and 87.0Hz. At 87 it flickers and cuts off a portion of the right side of the screen, and at 70 it cuts off the top bar. While doing this fixed the screen flicker during use the screen still flickered at the log in page. I then installed all of the updates, rebooted and everything worked fine. I continued using it set up some of my accounts and just basic set up. The next day it said there were more updates so I went ahead and installed those, but when i rebooted it wouldn't fully boot. It goes to the Xubuntu screen while everything is loading then the screen goes black. Then the Xubuntu screen is back but it's been vertically compressed into a horizontal bar acrross the top of the screen and it repeats horizontally like film. Since I had just started using it I decided to uninstall and reinstall and see if it worked, and it did until I reinstalled the updates. The computer I'm using is a dell dimension 4500. What should I do?

---

### Post by Vladlenin5000 on 2015-07-06
Hi and welcome.

First of all you thread's title isn't helpful but reading your post at least gives some clues about what's probably happening: Issues with video drivers.
Dell Dimension 4500 came with a variety of nvidia graphics systems; some may require proprietary drivers for proper performance. Go to System Settings > Software & Updates, find the rightmost tab Additional Drivers and select the recommended proprietary nvidia driver from the list. Apply and reboot. Adjust the resolution accordingly.

---

### Post by wyvern3 on 2015-07-06
Okay sorry the title isn't helpful I wasn't really sure what to put. I'm not able to boot into the OS so I'm not really sure how you meant for me to update the drivers, but I can still boot from the usb if I choose boot without installing. So i've done that and searched for drivers, but none appeared. So I ran ```
lspci | grep VGA
```

to get the information on the graphics card, and here is what it returned. ```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rage 128 PRO Ultra AGP 4x

```

---

### Post by Vladlenin5000 on 2015-07-06
> **wyvern3 said:**
>  ```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rage 128 PRO Ultra AGP 4x

```

Oh man... That's ancient. And there are no proprietary drivers that work in later Ubuntu releases. AMD relegated those to legacy a long time ago.

---

### Post by wyvern3 on 2015-07-06
> **Vladlenin5000 said:**
> Oh man... That's ancient. And there are no proprietary drivers that work in later Ubuntu releases. AMD relegated those to legacy a long time ago.

Okay so is there anything I can do to run linux on it as is, or am I either going to have to find a new comuter or replace the graphics card?

---

