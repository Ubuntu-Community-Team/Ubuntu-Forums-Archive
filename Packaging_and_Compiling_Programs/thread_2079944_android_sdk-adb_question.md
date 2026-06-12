---
title: "android sdk-adb question"
date: 2012-11-02
forum: Packaging and Compiling Programs
---

### Post by unibroker on 2012-11-02
When I do ```
lsusb
``` from my terminal with the device that has the sdk installed it returns ```
Bus 001 Device 011: ID 18d1:2d03 Google Inc.
```

When I do ```
./adb devices
``` it returns ```
List of devices attached 
2010720135452002	device

```

I'm confused because the format that I need for my udev rules is not what is given with the adb command but rather with the lsusb command.  When I type ```
adb devices
``` it returns ```
command not found
``` which indicates to me that adb is not set up properly.

FYI, here is the terminal input/output ```
jim@computer:~/jim/android-sdk-linux/platform-tools$ ./adb devicesList of devices attached 
2010720135452002	device

jim@computer:~/jim/android-sdk-linux/platform-tools$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 03f0:110c Hewlett-Packard 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 011: ID 18d1:2d03 Google Inc. 
```

---

