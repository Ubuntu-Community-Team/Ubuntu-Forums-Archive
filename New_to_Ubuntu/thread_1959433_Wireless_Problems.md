---
title: "Wireless Problems"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Socinus on 2012-04-15
I just did an install of Ubuntu on a desktop and it seems to have trouble accessing the computer's onboard wireless capabilities,

When I go to the wireless menu, it doesnt allow the wireless to be turned on and shows a "device not ready (firmware not installed)" message.

---

### Post by Gleichsnerd on 2012-04-15
Can you please enter
```
lshw -C network
sudo lsmod
```
into the terminal and post the output?

---

### Post by callmemahavir on 2012-04-16
Your operating system is not ready for working with wireless capabilities may be.

Please refer the URL to make ready your system...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

THIS WILL GIVE LOT OF INFORMATION!!!.

---

### Post by Socinus on 2012-05-02
It's been fixed. After some messing around I managed to find proprietary drivers that needed to be installed which I did and it now works.

Thanks :)

---

