---
title: "Builtin webcam not working Ubuntu 12.10"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by Graig on 2013-05-19
The webcam on my Sony Vaio PCG-5J2L is not working with Ubuntu 12.10. 
Cheese just give a solid black picture, Kamerka gives message "cannot connect to v4l device", Guvcview message "cannot open device".
It must be a driver issue, or Ubuntu cannot find the webcam.

Any advice on how I can get started to resolve this issue?

Thank you.

---

### Post by MoebusNet on 2013-05-20
I'm not an expert on this, but this should get you started:

Crl-Al-T to open Terminal

```
lsusb -v

lsusb -n
```

'lsusb -v' This program prints information about the devices connected to the USB bus. If you scroll through it, you should find some information about your webcam.

'lsusb -n' This version of the command lists the device's USB ID; a number that is unique to every device.

We're just checking to make sure that the USB bus can see the webcam.

EDIT: Some generic advice on webcams & troubleshooting:

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Graig on 2013-05-27
Solved.

I installed the following:
[COLOR=#000000][FONT=verdana]1. sudo add-apt-repository ppa:r5u87x-loader/ppa[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2. sudo apt-get update[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]3. sudo apt-get install r5u87x[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh

Which I obtained from [/FONT][/COLOR]http://ubuntuforums.org/archive/index.php/t-1031544.html

My webcam works great in Skype and Cheese!

---

