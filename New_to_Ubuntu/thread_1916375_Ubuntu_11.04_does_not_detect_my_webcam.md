---
title: "Ubuntu 11.04 does not detect my webcam"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by RobikShrestha on 2012-01-27
Ubuntu 11.04 does not detect my webcam. I tried it with cheese and kamoso. Most probably the driver is missing but I do not know which driver I need and from where I can get it.

When I ran gstreamer-properties, no video input device was detected.

---

### Post by nipunshakya on 2012-01-27
Please read the following...might help you out..

[http://ubuntuforums.org/showthread.php?t=842160](http://ubuntuforums.org/showthread.php?t=842160)

---

### Post by ptsubin on 2012-01-28
Try
> sudo modprobe -r uvcvideo
sudo modprobe uvcvideo

Sometimes this fixes the issue for me.

---

### Post by RobikShrestha on 2012-01-28
I made a stupid mistake of not turning on the web cam module. It works now.

---

### Post by nipunshakya on 2012-01-28
Glad that it was just a stupid mistake...:D....

Goodluck and Happy Linuxing
Regards,WinuxUser

---

