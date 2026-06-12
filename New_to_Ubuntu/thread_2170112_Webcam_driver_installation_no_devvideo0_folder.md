---
title: "Webcam driver installation no dev/video0 folder"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by QQmHGsr on 2013-08-24
Hello,

I have installated ubuntu 12.10 replaced my windows vista. Webcam not working after that. Also there is no /dev/video0 folder at all. It was working fine with windows and i assume there is no driver installed. Please suggest or help of how to proceed with installing. I also installed Cheese and when i try to open it i get the error "no device found". Please help.

Thanks

---

### Post by QQmHGsr on 2013-08-24
more information around this. When i type lsusb in terminal window. i get the below text

Bus 001 Device 002: ID 05ca:1836 Richo Co., Ltd Visual communication camera vgp-vcc4(r5u870)
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

---

### Post by coldraven on 2013-08-25
Do you have a icon for your web-cam on your keyboard? It might just be switched off by hardware.
Something like Fn+F7 might cure it. Sorry but no web-cam on this laptop so I'm really just guessing.

---

### Post by Merrattic on 2013-08-25
Check your dmesg for some output, easiest to do after unplugging and plugging in webcam for fresh output

---

### Post by QQmHGsr on 2013-08-25
My laptop has inbuilt web cam and so i can't unplug and plug again.

Also there is no web-cam icon on my keyboard.

Really struck here as web-cam is widely used in this laptop on daily basis. Any help is appreciated.

---

### Post by Merrattic on 2013-08-29
OK, can we please have the output from:
```
lsusb
```
```
hwinfo --usb
```
```
dmesg
```

---

### Post by mytaz on 2013-09-16
I have too this problem of no video0, you can create one with a sudo mknod, a chmod 666, a ls -n to create a symbolic link... But gstreamer-properties reply no video0 !!! I suppose there is a problem with permissions or groups because video or video0 belongs to root and I don't know how to change to my admin account (by users & groups, il doesn't work) !!!

---

