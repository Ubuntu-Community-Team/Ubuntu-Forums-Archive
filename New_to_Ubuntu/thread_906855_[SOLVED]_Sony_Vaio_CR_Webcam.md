---
title: "[SOLVED] Sony Vaio CR Webcam"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-08-31
How do I go about getting my webcam on my Sony Vaio CR520E to work and under what programs can it work?  Any ways to use the webcam in a program that runs AIM?

Here is what lsusb gives:
```
Bus 007 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 044e:3012 Alps Electric Co., Ltd 
Bus 001 Device 005: ID 044e:3013 Alps Electric Co., Ltd 
Bus 001 Device 004: ID 044e:3010 Alps Electric Co., Ltd 
Bus 001 Device 003: ID 044e:3011 Alps Electric Co., Ltd 
Bus 001 Device 001: ID 0000:0000
```

Thanks!
Ryan

---

### Post by subaruwrc01 on 2008-08-31
Ok I followed this guide.  [http://ubuntuforums.org/showthread.php?t=821343](http://ubuntuforums.org/showthread.php?t=821343)

However I can only take pictures when I set Capture to off.  The screen is black for anything else.

Here is my output:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
xinerama 0: 1280x800+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_REQBUFS(count=2;type=VIDEO_CAPTURE;memory=MMAP): Success
station "/dev/video0" not found
ioctl: VIDIOC_REQBUFS(count=2;type=VIDEO_CAPTURE;memory=MMAP): No such file or directory
ioctl: VIDIOC_REQBUFS(count=2;type=VIDEO_CAPTURE;memory=MMAP): Resource temporarily unavailable
ioctl: VIDIOC_REQBUFS(count=2;type=VIDEO_CAPTURE;memory=MMAP): Resource temporarily unavailable
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Input/output error


```

---

### Post by subaruwrc01 on 2008-08-31
Hmm, started working after 2nd reboot.

---

