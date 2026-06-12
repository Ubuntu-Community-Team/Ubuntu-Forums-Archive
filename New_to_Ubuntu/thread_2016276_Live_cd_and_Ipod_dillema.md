---
title: "Live cd and Ipod dillema"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-07-04
I have a 16gb Itouch, 2nd gen which I use as a mini external hard drive. My question is - could a Ubuntu 12.04 LTS live cd be put onto it and boot from flash in the case my computer needs a re-install? would there be any issue if there were also other files (non live CD related) on the hard drive? 
I've tried before to re-install Ubuntu from a live cd that was on a  1gb ipod shuffle and it didn't work. 
It's not something that is completely essential to me, but I travel a lot and don't have access to internet for long periods of time and this would guarantee my system is crash-proof wherever I may be.

Thank you. 
K.m

---

### Post by cipherboy_loc on 2012-07-04
No, due to various restrictions Apple has placed on the iPod models, it is impossible for the computer to recognize the iPod as a storage/flash medium on boot. Just placing the .iso on the device from a computer would not work. You could buy a cheap 1GB flash drive, copy the .iso there and boot it via GRUB2 instead though. Would not have persistence. 

Cipherboy

---

### Post by sandyd on 2012-07-04
Doesn't work. You can sync to ipods, but not use it as a MSC (Mass Storage Device).

Get a 1GB usb drive, and use unetbootin to get Ubuntu on the drive.

---

### Post by kabukiM0n0 on 2012-07-08
I thought it couldn't be done. Thank you.

---

