---
title: "Skype Web Cam works but I need help with configuring..."
date: 2011-12-14
forum: New to Ubuntu
---

### Post by suomalainen on 2011-12-14
Ubunteros,

When I open Skype and then OPTIONS--> VIDEO DEVICES and click the "Test" button to see a video nothing happens. Just a black screen.

However, when I open terminal and enter:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Skype launches and I can then see a video stream.

But when I do this command in terminal I get:

> people@people-laptop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
libv4l2: error allocating conversion buffer


Questions:

1. What is the error about and does it need to be corrected?
2. How can I use this terminal command to start Skype since it also enables the video to work?

Thanks for your time and Support!

Suomalainen

---

### Post by suomalainen on 2011-12-16
Bump

---

### Post by Zvanochek on 2011-12-16
I'm not sure it is still appropriate in your position, but have you checked that skype is configured correctly? 
 
If you launch skype normally, then head to the sound preferences panel, and make sure under hardware and input tabs are set to the webcam (or analog mono).

---

### Post by suomalainen on 2011-12-16
such options do not exist.

---

