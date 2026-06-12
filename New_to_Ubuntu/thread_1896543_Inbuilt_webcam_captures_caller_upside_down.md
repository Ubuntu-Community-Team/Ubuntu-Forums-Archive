---
title: "Inbuilt webcam captures caller upside down"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by resander on 2011-12-17
This is for a Fujitsu Biblo LOOX FMV LT70x netbook obtained in Japan. It came with Windows Vista and I made it dual-boot with Ubuntu 10.04.03 LTS. Dual booting is working fine. 

Result of lsusb:
lsusb
Bus 005 Device 002: ID 0c24:000f Taiyo Yuden Bluetooth Driver (V2.0+EDR)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:09b2 Logitech, Inc. Fujitsu Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The inbuilt Logitech webcam captures and sends the picture upside down for Skype, as if the caller is suspended upside down from the ceiling! Both for the local image shown on the netbook and the image sent to the Skype destination.
 
Q1 Any other programs using webcam that I can try for Ubuntu?

Q2 Are there settings somewhere to flip the image 180 degrees?

Ken

---

### Post by lechien73 on 2011-12-17
Hmmmm...a China Syndrome webcam :)

I had a bookmark saved to this link, because I've used this solution to fix the same problem before: [http://radu.cotescu.com/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/flipped-images-ubuntu-webcam/)

I hope it helps you too!

---

### Post by resander on 2011-12-19
Thanks Lechien73,

The caller is still upside down!

I am not sure if have interpreted Radu Cotesco's blog correctly.

I noticed the library file v4l1compat.so was present in 
/usr/lib/libv4l/v4l1compat.so of Ubuntu 10.04.03 LTS, so I did not fetch it. I used it instead from the command line like this:   

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

which started Skype on the netbook.
Q1. Is this correct?

I also tried a clip-on separate web camera (I know it is working) plugging it into a usb port of the netbook, but it did not override the inbuilt web camera.

Q2. How to override the inbuilt web cam?

Q3. Would the average computer repair shop be able to refit the inbuilt webcam? Or is that a non-starter?

Ken

---

### Post by lechien73 on 2011-12-20
Hi...sorry for my delayed response, I just notice you'd replied now :)

The v4l1compat.so file has been patched in the link I gave you, so that it flips the image of the webcam. If you fetch it and try with that, then hopefully it will work for you.

A USB webcam should be accessible from Skype, just go into the Skype options and pull down the **Select Webcam** box, you should then be able to select your external webcam (probably /dev/video1). I've attached a screenshot of my settings so you know which tab to choose.

I don't think retrofitting your webcam is the way to go - I'm sure we can solve this with software :) (said the programmer!! A hardware engineer would probably give you the opposite answer ;))

---

### Post by resander on 2011-12-28
Thanks Lechien73,

Yes, indeed I could change/select video camera from Skype.

The recommendation by Radu Cotesco did not work for me, but executing this from the command line did:

export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4lcompat.so skype

I googled to find the above, but have lost the page. From memory I think I was searching on 'Skype upside down' or something similar.

Ken

---

