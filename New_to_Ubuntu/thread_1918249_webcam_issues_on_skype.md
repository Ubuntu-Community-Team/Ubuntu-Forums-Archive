---
title: "webcam issues on skype"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by nicckc on 2012-01-31
hi i have recently recieved a webcam that works with photo taking apps such as camorama webcam viewer. but it will not stream video during a web chat on skype. It also works on web chat applications such as chatroulette or omegle. im not sure what i should do to make it work with skype. i have already ruled out skype settings as the issues. i have gone throuhg everything to make sure my webcam is recognized and given permission to send video. 

heres a little info about my webcam.

```
lsmod | grep videodev
videodev               92992  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev

``````
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08a0 Logitech, Inc. QuickCam IM

```

---

### Post by sailor2001 on 2012-01-31
skype is mainly for windows. I have to reboot into  XP to have the  webcam work as it should.

---

### Post by rgreener25 on 2012-01-31
Did you download skype from skype.com or the repo's

---

### Post by nicckc on 2012-01-31
i downloaded it straight from skype. i downloaded the newest beta build for linux and everything else works as it should but it will not stream video

---

### Post by partloer on 2012-02-01
Does skype detect the webcam?  Under options -> video devices

My available webcam shows: UVC Camera (046d:0990) (/dev/video0)  Both of which were listed from ```
lsmod | grep videodev
``` and ```
lsusb
```

---

