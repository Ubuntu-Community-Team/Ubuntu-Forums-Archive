---
title: "USB camera disconnection/reconnection"
date: 2015-11-09
forum: New to Ubuntu
---

### Post by Mike_Partington on 2015-11-09
I have a project running Python with OpenCV and Pygame under Ubuntu 14.04 that uses two USB cameras, images from which are processed and displayed on the local monitor.

If the system is started with both cameras connected everything runs fine, if I disconnect one camera the associated part of the display freezes as expected. The disconnection is detected and the associated video capture object released. When the camera is reconnected the reconnection is detected and a new video capture object created and the display eventually resumes updating but ONLY if the camera has been allocated the same index, e.g. /dev/video0, as it had before it was disconnected.

If the camera is allocated a different index on reconnection it appears in lsusb as normal, inspection of the uvcdynctrl-udev.log shows no anomalous entries but the images from the camera are never captured. Similarly, if the system is started with one of the cameras disconnected and the camera is subsequently connected while the program is running it is recognised but never activated.

Does anybody out there have an idea of where I could look to try and find out why this happens? I am new to Ubuntu, Python etc but have many years experience in microcontrollers and Visual Basic.

---

