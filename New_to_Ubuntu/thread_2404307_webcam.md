---
title: "webcam"
date: 2018-10-22
forum: New to Ubuntu
---

### Post by scamp666 on 2018-10-22
I have downloaded and extracted the files for my logitech webcam, but cannot find the commands for compiling to make it able to install. The webcam works with VLC but not skype. I'm running 18.04. Any help would be much appreciated.

---

### Post by Holger_Gehrke on 2018-10-22
If it works in vlc (and/or in guvcview or in cheese or ... ) then you've got a working driver and the problem in skype is more likely a matter of settings in skype. It's very rare to need any kind of driver on Ubuntu, mostly drivers are included unless it's something very unusual or very new.

Holger

---

### Post by mastablasta on 2018-10-23
the issue is with sykpe not webcam. try the LD PRELOAD trick: 

[https://askubuntu.com/questions/315643/ld-preload-fails-with-skype](https://askubuntu.com/questions/315643/ld-preload-fails-with-skype)

or for 64bit os:
[https://askubuntu.com/questions/973129/skype-for-linux-on-64-bit-asus-with-upside-down-webcam](https://askubuntu.com/questions/973129/skype-for-linux-on-64-bit-asus-with-upside-down-webcam)

---

