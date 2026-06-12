---
title: "Secure boot.  Intstaller codecs not installed I did not enter password."
date: 2019-02-07
forum: New to Ubuntu
---

### Post by richard378 on 2019-02-07
Hi,
I had uninstalled Ubuntu for a while due to journalctl -b showing bugs at the time.  However, I am now duel booting with a new Ubuntu 18.10 install and I use secure boot.  When installing I clicked install the additional propitiatory codecs.  However, when I restarted the computer and the MUK screen came up I did not respond and the computer restarted normally.  When I installed NVIDIA drivers I did figure out how to respond.  I realized I did not respond for the secure boot the first time and wondering how to get that screen to install the key for the codecs now that I missed it the first time.  How do I fix the codecs so that I can use them properly with secure boot?

---

### Post by oldrocker99 on 2019-02-07
My own experience with UEFI has convinced me to use nothing but Legacy. Every installation with which I used UEFI failed to install grub, which results in an unbootable computer. Using Legacy has not failed me.

---

### Post by Impavidus on 2019-02-07
Not sure what secure boot has to do with codecs... Those codecs you can ask to be installed are audio and video codecs with restrictive licenses. Choosing to install them will install the package **ubuntu-restricted-extras**, which will on 18.04 in turn (mostly as recommended packages) install:
* ubuntu-restricted-addons
** chromium-codecs-ffmpeg-extra
** gstreamer1.0-fluendo-mp3
** gstreamer1.0-libav
** gstreamer1.0-plugins-ugly
** gstreamer1.0-vaapi
* libavcodec-extra
* ttf-mscorefonts-installer
* unrar

You can check to see if they are installed.

---

### Post by richard378 on 2019-02-07
The inital installer requires a password for installing those packages on install for the secure boot.  How do I test that the packages are working correctly?

---

