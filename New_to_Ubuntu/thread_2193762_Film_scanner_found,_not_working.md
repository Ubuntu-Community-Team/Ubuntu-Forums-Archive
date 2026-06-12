---
title: "Film scanner found, not working"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by edfast on 2013-12-14
Hello everyone, at my wits' end here. Running Ubuntu Studio 13.04 and a Nikon CoolscanV (LS-50 ED), which is found:```
XYZ@Studio-Z68ITX-B-E:~$ sudo lsusb
[sudo] password for XYZ: 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 2109:0811  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0749:1000 EVer Electronics Corp. 
Bus 002 Device 004: ID 1267:0210 Logic3 / SpectraVideo plc LG Optical Mouse 3D-310
Bus 002 Device 005: ID 0d8c:0126 C-Media Electronics, Inc. 
***Bus 003 Device 007: ID 04b0:4001 Nikon Corp. LS 50 ED/Coolscan V ED***
```(my **bold**, my *italics*) but xsane returns an error message saying it cannot open the unit, and that there's an error with its I/O. I have tried the backends suggested at the lp sane project page, but am not sure I installed them correctly. I googled another usb printer and found someone who had tried ```
sudo chmod 0777 /dev/bus/usb/[COLOR=#ff0000]xxx[/COLOR]/[COLOR=#0000ff]yyy[/COLOR]
```substituting 003/007 as was the case with my installation, but to no avail (and who knows what else I mucked up in the process?). I am getting predictably sick of second-guessing and afraid I might soon do some real harm. 

Presumably *someone* is using the same film scanner having successfully installed it? Is it you? How did you do it?:D

---

