---
title: "Creating a Boot Image through chomebook"
date: 2020-12-20
forum: New to Ubuntu
---

### Post by ender-shark on 2020-12-20
So, what I am trying to do is create a boot image of Ubuntu 20.04 (64 bit version) and install the image to my WesternDigital easystore 1tb external harddrive. The issue is the only machine I have access to is my smasung chromebook 3, and when looking for toutorials they seem to be from the point of veiw that I have a mac and or windows device I can use or that I already have a machine running Ubuntu.

---

### Post by CelticWarrior on 2020-12-20
Welcome.

What's the purpose of what you want to do? What's the target hardware you want to boot that installation?
Or perhaps this is a X-Y problem?

---

### Post by ender-shark on 2020-12-20
I just want to run ubuntu off the drive on the chromebook as well as still being able to install a handful of applications on it while I am trying to get into linux. Chromium is not cutting it anymore and with covid my options are pretty limited.

---

### Post by grahammechanical on 2020-12-20
According to this source, which is fairly recent, you use the Chromebook Recovery Utility

[https://technastic.com/create-a-bootable-usb-on-chrome-os/](https://technastic.com/create-a-bootable-usb-on-chrome-os/)

This link is older but notice the answer with 6 votes and the instruction to rename the ISO file to have a .bin extension.

[https://askubuntu.com/questions/278403/how-do-you-make-usb-bootable-on-chromebook](https://askubuntu.com/questions/278403/how-do-you-make-usb-bootable-on-chromebook)

Regards

---

### Post by ender-shark on 2020-12-20
Thanks I'll check that out

---

### Post by CelticWarrior on 2020-12-20
There are options to install Ubuntu in a Chromebook indeed and the location - internal SSD/eMMC, external SD/microSD or, eventually, external HDD - is not that relevant as you might think. So, I suggest you google how to install Ubuntu in your specific model and go from there.

You will likely find out that some methods imply changes to the hardware and/or firmware that violate the TOS/license for the product you own and because of that providing help here is frowned upon (if I'm wrong I hereby authorize the Mods - not that they need it anyway - to edit or delete this post).

---

### Post by ender-shark on 2020-12-20
Yeah that is part of why I wanted to install it on the drive it would void my warenty if I changed the operating system.

---

### Post by CelticWarrior on 2020-12-20
It may void the warranty either way. Some Chromebooks need physical changes in the hardware and/or loading an "unauthorized" firmware ("BIOS") in order to boot a different OS. **It doesn't matter *where* the other OS is installed.**

Also of note: The links above are NOT for what you want. The links above are for making bootable installation media from an Ubuntu ISO in ChromeOS. This is for installing Ubuntu (in compatible hardware), it is NOT an Ubuntu installation.
Chromebooks typically come in two different hardware architectures - x86_64 or ARM -. The former is the same of any regular PC so the regular Ubuntu for which you can download the usual ISO, make a bootable USB with it, then boot and install Ubuntu, can be used, **as long as it boots in the target hardware**. The latter is similar to your phone or tablet. It needs a special port of Ubuntu similar to the one you use in boards like Raspberry Pi. In those Ubuntu is typically installed with the help of a script that downloads and installs Ubuntu in the user defined target device.

If the above seems alien to you - I bet it does - then the sad truth is you definitely shouldn't even try to do what you intend, very likely you'll end up with no OS at all.

My best advice is to try selling it in eBay and buy any new Intel Celeron N4000 laptop (or AMD APU entry level equivalent) or any used but relatively recent more powerful computer.

---

### Post by C.S.Cameron on 2020-12-20
I understand that the Android app EtchDroid will work on ChromeBooks:
[https://askubuntu.com/questions/1274361/can-we-use-etchdroid-to-create-ubuntu-installation-media](https://askubuntu.com/questions/1274361/can-we-use-etchdroid-to-create-ubuntu-installation-media)
It is sorta like balenaEtcher for Android.

---

