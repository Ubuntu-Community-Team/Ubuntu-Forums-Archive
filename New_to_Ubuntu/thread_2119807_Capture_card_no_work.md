---
title: "Capture card no work"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by n123q45 on 2013-02-24
I changed to ubuntu and my capture card doesn't show up. Is there any way for it to work?
i have a Sabrent USB-AVCPT

---

### Post by zrdc28 on 2013-02-24
First thing you need to do is go to terminal and do a.

"sudo lspci" and look and see if the system recognizes the card. If it is listed then.
 
Next do a "lsmod" to see if the software module for that card is loaded it might look like usb_11n, rtl 8191 or 8188 if it is not listed in lsmod you will need to come up with the linux driver, install it and modprobe driver software.

---

### Post by gordintoronto on 2013-02-28
lspci won't help with a USB device.

Have a look at:
[http://www.linuxquestions.org/questions/slackware-14/vlc-and-sabrent-usb-video-capture-adapter-usb-avcpt-4175436842/](http://www.linuxquestions.org/questions/slackware-14/vlc-and-sabrent-usb-video-capture-adapter-usb-avcpt-4175436842/) 

In what way does your card not "show up?" What program are you trying to use with it?

---

### Post by n123q45 on 2013-03-05
Cheese Webcam Booth. I dont know anything else that captures videos

---

### Post by n123q45 on 2013-03-05
all it shows is vertical lines of diffrent shades starting from black and going to white

---

