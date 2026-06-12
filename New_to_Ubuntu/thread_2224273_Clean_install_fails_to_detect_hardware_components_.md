---
title: "Clean install fails to detect hardware components (USB boot detects them just fine)"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by alex203 on 2014-05-15
I just upgraded (well clean install actually) an old (nolonger supported) Ubuntu install on an my old Sony Vaio FE41E to Lubuntu 14.04. I tested Lubuntu 14.04 out on my laptop beforehand by booting off the USB key. Everything (touchpad, wifi, etc.) seemed to work just fine. So I went ahead with the install. First thing I notice is the trackpad is not working. Logged in and the next thing I noticed is the WiFi is not working either. I also noticed that the laptop screen resolution was not available for selection. As I mentioned all of these things were fine been booting from USB.

Running the commands:
[LIST]
[*]'ifconfig': Shows only the lo (loopback) interface. No wlan0 or eth0 that I see when booting from USB
[*]'xinput': Booting from install, it is missing quite a few entries that I see when booting from USB.
[*]'lsmod': Shows nothing (no output straight back to prompt) from install boot; loads of stuff from USB boot.
[/LIST]

I figured that if no kernel modules are being loaded, then things are bound not to be working all that well. But I'm not too sure how to debug and resolve. Any help would be much appreciated.

---

### Post by Vladlenin5000 on 2014-05-15
The Nvidia GeForce Go 7400 really requires proprietary drivers in your notebook. 
Regarding WiFi I have no idea. I supposed it's some a/b/g Intel, one of those that used to just work. That and also not having Ethernet (or touchpad) seems to be symptoms of a deeper&darker problem

---

### Post by alex203 on 2014-06-09
Hi Vladlenin5000,

Thanks for responding. Sorry for late reply. I'm still trying to resolve the issue. I'll try posting separately for each issue. There was one thing I was wondering if you might know... Do you know why I don't have any of these issues when booting from USB? Everything works fine booting from USB. It's the install to disk that's having threes problems.

Thanks again.

Alex

---

### Post by alex203 on 2014-06-14
So I manged to fix this problem myself by recreating the  bootable USB stick with a different tool and reinstalling from scratch. I  did try two installations from the previous bootable USB stick with  same results.


  As I used the same verified ISO I can only assume that it was the  tool I used to create the bootable USB stick (although I don't  understand how/why). I won't name/blame the tool I used though. I think  it was probably down to using an old version and/or choosing the wrong  options when creating it.


  Moral of the story: Use a simple and up to date tool for creating  bootable USB stick. Probably best to go the one most recommended in your  distributions doc! What worked for me was Ubuntu 'Startup Disk  Creator'.

---

