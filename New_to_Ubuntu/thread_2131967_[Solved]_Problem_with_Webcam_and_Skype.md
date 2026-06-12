---
title: "[Solved] Problem with Webcam and Skype"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by ferguson1951 on 2013-04-03
Hello everybody.
I have Ubuntu 12.04 Precise 32 bit
Skype 4.1
Logitech Quickcam Chat

The webcam works with Cheese but not with Skype.
I have tried from terminal without success the following command:LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so /usr/bin/skype
Any ideas?
Thanks and regards

---

### Post by ferguson1951 on 2013-04-06
Hello everybody.
This is how eventually, after trying a great number of options, I solved this problem
I went to the Tucows website and, through the Ubuntu Software Centre, downloaded this Skype version:  Skype Beta 2..1 for Linux.
I then opened the shell and gave this command:                         
 LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
Obviously I had to uninstall the old Skype on my computer.

It worked.
I only had to fiddle a bit in order to activate the webcam, but it worked.
I hopoe this is useful.
Thanks everybody and best wishes

---

