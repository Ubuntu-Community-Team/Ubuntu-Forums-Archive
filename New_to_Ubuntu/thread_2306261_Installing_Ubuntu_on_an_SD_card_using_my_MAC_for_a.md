---
title: "Installing Ubuntu on an SD card using my MAC for a raspberry Pi"
date: 2015-12-13
forum: New to Ubuntu
---

### Post by Stephen_Wilkerson on 2015-12-13
Help please 
Trying to install ubuntu on a SD card from the MAC  must have a mistake
1. Downloaded ubuntu-trusty commands as follows:
diskutil unmountDisk /dev/disk1
sudo dd if=2015-06-04-ubuntu-trusty.img of=/dev/rdisk1 bs=1m

No errors, finishes but sd card won't boot in Raspberry Pi

Help Please....

---

### Post by Frogs Hair on 2015-12-15
What version of Pi ? A Pi 2 is required to run Ubuntu and if the SD card is not properly formatted the OS won't start.  

[https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)

[https://www.sdcard.org/downloads/formatter_4/eula_mac/](https://www.sdcard.org/downloads/formatter_4/eula_mac/)

---

### Post by Stephen_Wilkerson on 2015-12-16
Yes I believe it is a Raspberry Pi 2 model B+ but I could be wrong.  The board says: Raspberry Pi Model B+ V1.2  do I have that wrong?

---

### Post by Frogs Hair on 2015-12-16
The version is indicated on the board . I have a B+ which has a smaller processor. 


[http://www.alphr.com/raspberry-pi-2/1000353/raspberry-pi-2-vs-raspberry-pi-b-a-raspberry-pi-comparison](http://www.alphr.com/raspberry-pi-2/1000353/raspberry-pi-2-vs-raspberry-pi-b-a-raspberry-pi-comparison)

---

### Post by QIII on 2015-12-16
> **Stephen_Wilkerson said:**
> Yes I believe it is a Raspberry Pi 2 model B+ but I could be wrong.  The board says: Raspberry Pi Model B+ V1.2  do I have that wrong?

The Pi 2 should indicate clearly that it is a Raspberry Pi 2 Model B.  If it says B+, then it is the older ARM6 architecture and it will not run Ubuntu.

---

### Post by Stephen_Wilkerson on 2015-12-16
Ok I have a 2 for sure now it says: Raspberry Pi 2 Model B v1.1 On to my next screwup....
Thanks much,
Drew

---

### Post by Stephen_Wilkerson on 2015-12-16
Yep that was it.  Booted to Raspberry Pi 2 really quickly.  No issues.  Are there versions of Ubuntu that run on the older Pi s?

---

### Post by QIII on 2015-12-16
No.  Canonical held out for ARM7 architecture and Ubuntu won't run on the ARM6 in the older Pis

---

