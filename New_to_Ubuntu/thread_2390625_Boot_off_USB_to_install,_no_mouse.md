---
title: "Boot off USB to install, no mouse"
date: 2018-04-30
forum: New to Ubuntu
---

### Post by Riggs on 2018-04-30
Hello all,

I've installed Ubuntu before, but it's been an incredibly long time since I tried. I have a self built PC with a Gigabyte Z97X-Gaming 5 motherboard. I've read up on some of the forums that there could be USB problems causing the mouse to not work. The keyboard works fine, and the mouse cursor shows up, but doesn't move. I don't have a IOMMU option that I can find in the BIOS. Any help would be appreciated.

---

### Post by #&amp;thj^% on 2018-04-30
I have seen this from time to time myself, I however was lucky enough to simply pull the USB reciver and replug it, and mouse then worked. Other than that i can't add anything else based on your given information.

Maybe a "lsusb" might help you get help or even better install inxi:
```
sudo apt install inxi
```
Then you will need to upgrade inxi to show USB devices via:
```
sudo inxi -U
```
And now tell inxi to show all related USB devices via:
```
inxi --usb
```

---

### Post by oldfred on 2018-04-30
Have you enabled USB support in UEFI?
I have Asus  Z97. UEFI screen shots attached.

---

### Post by Riggs on 2018-04-30
I don't see anything specific in my BIOS relating to USB. It's just funny that the keyboard plugged in right next to the mouse works just fine, and both devices work just fine in Windows. I looked for something similar to your screenshots, but I don't have anything specific saying to enable or disable USB.

EDIT: Tried a generic Dell mouse I had laying around. For some reason, that mouse works just fine. My expensive Corsair Glaive mouse doesn't though. Why in the world?

---

### Post by #&amp;thj^% on 2018-04-30
That was kind of my worry here "Corsair Glaive mouse".
Know issue for over a year now:  [https://github.com/mattanger/ckb-next/issues/225](https://github.com/mattanger/ckb-next/issues/225)
Some kernels it works just fine others not so good. :(
There was 1 or 2 folks having reported they got it working from that link i listed.
Good Luck :)
**EDIT 5-1-2018**: I just set both my Keyboard and Mouse USB reciver's side by side and had the same problem as you are seeing cursor won't move, so I then moved one of the receiver's from the rear of my tower to the front and now cursor moves and functions as normal again.
I would definitely call this a bug in the 4.15 and 4.16 kernels.
As a side note I notice the same freeze with the mouse if the receiver is next to my WiFi USB dongle also.

---

