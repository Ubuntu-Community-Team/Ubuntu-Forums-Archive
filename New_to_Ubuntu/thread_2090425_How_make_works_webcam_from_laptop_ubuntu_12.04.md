---
title: "How make works webcam from laptop ubuntu 12.04"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by gurrunaki on 2012-12-02
Hi, I have a Toshiba Portege Z830 and running ubuntu 12.04 I can not make works the webcam that is coming with the laptop, when I write in the terminal this command

ls /dev/video*

recognice the webcam like /dev/video0 but not clue how make it works!!!

Please, any help?

Thanks in advance

---

### Post by NikTh on 2012-12-02
Hi , 
make it work with what program ? Is this specific to Skype ... etc ? 

Lets see if your cam recognized by Ubuntu. 
Open a terminal and give this command
```
lsusb
```give the results back here.  
Also write ```
gstreamer-properties
``` and at the opened window goto **Video** and then click **Test** at **Default Input** , can you see your self ? 

If not , give here any messages from terminal. 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

---

### Post by gurrunaki on 2012-12-02
Thanks for your fast reply 

This is after write  lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 1bcf:288e Sunplus Innovation Technology Inc. 
Bus 002 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth

---

### Post by gurrunaki on 2012-12-02
And this is what happen after write the second comand
(gstreamer-properties:6540): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:6540): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

And yes, after test the video, I can see myself!!! but why in Skype doesn't recognize the webcam? And how can I make it work even if is not for skype, just for take shots or video, etc?

Thanks a lot

---

### Post by gurrunaki on 2012-12-02
Is done!!! :P I downloaded the cheese software, so now the webcam is working perfectly, thanks a lot all of you for your help.

---

