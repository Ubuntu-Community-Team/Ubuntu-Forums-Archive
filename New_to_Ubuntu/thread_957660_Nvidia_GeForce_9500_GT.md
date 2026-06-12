---
title: "Nvidia GeForce 9500 GT"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by rob-rjt on 2008-10-24
I have got the video card in the title of the thread and downloaded the Nvidia Linux driver, and when I run the nvidia-xconfig command and restart the X server it works fine - I get shiny 3D acceleration.

Unfortunately when I restart the computer, either the monitors or the graphics card or both are not detected?

What could be causing this. I've had a look on Google and can't find anything regarding the same problem.

Thanks.

---

### Post by LowSky on 2008-10-24
run this command gksu nvidia-settings

dont forget to save a new Xorg.conf file
restart and everything should work

---

### Post by rob-rjt on 2008-10-24
I've run sudo nvidia-xconfig and also run nvidia-xconfig through a root shell but every time I reboot it goes into safe graphics mode and I can only get proper setting back by rebooting into the restore mode and resetting the X server settings :(

nvidia-xconfig auto saves the xorg.conf file.

As I run it from default X Server settings it complains that the Configured Video Driver does not have a "Device" line..?

---

