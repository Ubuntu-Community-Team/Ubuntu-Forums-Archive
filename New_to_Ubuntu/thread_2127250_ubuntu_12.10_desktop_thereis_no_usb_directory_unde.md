---
title: "ubuntu 12.10 desktop thereis no usb directory under /proc/bus"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by awaybrave on 2013-03-19
My desktop enviroment is ubuntu 12.10, and I want to set up usb device for my virtualbox. But I found there was no /usb under /proc/bus but /usb exists under /dev/bus/, I really need to alter the settings of etc/fstab and add this to /etc/fstab file : "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0". How can I fix it ? Or how can I set up usb device for virtualbox?? Please Help Me.... I am a beginner...

---

### Post by ibjsb4 on 2013-03-19
Have you seen this?

[https://www.virtualbox.org/manual/ch03.html#idp18996720](https://www.virtualbox.org/manual/ch03.html#idp18996720)

---

### Post by awaybrave on 2013-03-19
The turtorial says:
"For example, most Linux distributions have a user group called       usb or similar, of which the current       user must be a member. To give all users of that group access to usbfs,       make sure the following line is present:


# 85 is the USB group none     /proc/bus/usb     usbfs      devgid=85,devmode=664    0    0 "
but there is no usb under /proc/bus, instead /dev/bus/usb does! Therefore, when I add  "none     /proc/bus/usb     usbfs      devgid=85,devmode=664    0    0 " to /etc/fstab file ,  the system could not mount the file and crashed the system down. How can I fix this? Does it relate to the version of newer Ubuntu? Thanks for listening.

> **ibjsb4 said:**
> Have you seen this?

[https://www.virtualbox.org/manual/ch03.html#idp18996720](https://www.virtualbox.org/manual/ch03.html#idp18996720)

---

