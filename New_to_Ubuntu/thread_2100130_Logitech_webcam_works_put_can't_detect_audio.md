---
title: "Logitech webcam works put can't detect audio"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by andres45 on 2012-12-31
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 004: ID 046d:081b Logitech, Inc. Webcam C310
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse


My web cam works but it does not detect the audio I tried finding it in hardware but it does no show up please help new to Ubuntu hope to make it my main OS.

---

### Post by daslinkard on 2013-01-01
Welcome to the forums! One of the things that you could try would be running the following terminal command:
```
alsamixer
```

You should be able to adjust your mic db levels and ensure the mic is not muted at start up.

---

### Post by andres45 on 2013-01-01
Apparently some were muted because they were set to 0 and mm but i turn them all up and changed mm to oo but mic still doesn't work thanks for the input and the welcoming [daslinkard]("http://ubuntuforums.org/member.php?u=1565157")

---

### Post by Bryan55 on 2013-01-01
Look in sound setting and they should be like attached picture.
If so when you make a sound the input level will move.

---

### Post by andres45 on 2013-01-01
Thanks [Bryan55]("http://ubuntuforums.org/member.php?u=991728") it fixed my problem mic works fine now.

---

### Post by daslinkard on 2013-01-02
Awesome this is resolved for you!  Please mark this thread as Solved!

---

