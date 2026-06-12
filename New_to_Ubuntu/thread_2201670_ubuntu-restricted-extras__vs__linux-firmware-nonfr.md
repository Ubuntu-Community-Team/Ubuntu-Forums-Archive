---
title: "ubuntu-restricted-extras  vs  linux-firmware-nonfree"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-01-25
Hello All...
What is the difference between the codes:

 sudo apt-get install ubuntu-restricted-extras 
sudo apt-get install linux-firmware-nonfree

Do both codes put the same stuff on?
Can I run both codes, are will they interfere with each other?

Thanks

---

### Post by Impavidus on 2014-01-25
They are completely different and won't interfere.

linux-firmware-nonfree:
```
This package provides non-free firmware used by Linux kernel drivers.

Most of the firmware in this package is for television tuner cards. However,
non-free firmware for other classes of devices are provided as well.
```
If your hardware doesn't need it, there's no reason to install this.

ubuntu-restricted-extras:
```
This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Flash plugin, LAME (to create compressed audio files), and DVD playback.

Please note that this does not install libdvdcss2, and will not let you play
encrypted DVDs. For more information, see
https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs

Please also note that packages from multiverse are restricted by copyright
or legal issues in some countries. See
http://www.ubuntu.com/ubuntu/licensing
for more information.
```
A collection of popular user software with non-free licenses. If you want it and it doesn't clash with your ideals, just install. You can also install only parts of it, for example, installing the Flash plugin but skipping the Microsoft fonts.

---

### Post by Frogs Hair on 2014-01-25
No, the linux-firmware-nonfree packages is mainly for TV tuner cards and ubuntu-restricted-extras is an entire collection audio video codec/s including flash , MS fonts and gstreamer plug-ins.

---

### Post by grahammechanical on 2014-01-25
Linux firmware refers to Linux kernel modules. Ubuntu restricted extras refers mainly to video and audio codecs. Compare,

[http://packages.debian.org/jessie/firmware-linux-nonfree](http://packages.debian.org/jessie/firmware-linux-nonfree)

[https://apps.ubuntu.com/cat/applications/ubuntu-restricted-extras/](https://apps.ubuntu.com/cat/applications/ubuntu-restricted-extras/)

[http://packages.ubuntu.com/precise/linux-firmware-nonfree](http://packages.ubuntu.com/precise/linux-firmware-nonfree)

So, those two commands install different stuff. I can understand why someone would want to install Ubuntu Restricted extras. I do that on my installs of Ubuntu. But I have no idea as to why there would be a need to install linux-firmware-non-free. I assume that the Additional Drivers utility would make use of this package if we needed a wireless adapter driver. Click on the list files in the package and you will see of the files that you will get and they are completely different form the packages that we get with Ubuntu restricted extras.

Regards.

---

### Post by GUZZLR on 2014-01-25
>  I have no idea as to why there would be a need to install  linux-firmware-non-free. I assume that the Additional Drivers utility  would make use of this package if we needed a wireless adapter driver

you are correct, I have an old Dell XP Latitude, and I install the linux-firmware-nonfree to get my old Broadcom 43 wireless card to work...just installed Saucy from Raring Ringtail, and of course, my wireless did not work, so I've always used the following codes to get it to work (thanks Hadaka):

sudo apt-get update 
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43

Along with the above codes, I also install the restricted extras, I just never new if installing both was messing things up.  At any rate, for the old Latitude, firmware non-free codes work well.
 
Thanks for the help

---

### Post by oldos2er on 2014-01-25
You can use "-s" to simulate an apt-get command if you're unsure of what it's going to do: ```
sudo apt-get install -s ubuntu-restricted-extras linux-firmware-nonfree
```

---

