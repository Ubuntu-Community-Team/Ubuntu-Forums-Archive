---
title: "Ubuntu Crashing when booting"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-05-04
I have a computer which would run Ubuntu 12.04, and the computer ran great until I updated to Ubuntu 14.04. After the update the computer will stall in a black screen wheen booting or it will crash when almost finishing to boot. I have re-installed Ubuntu 12.04 and the computer stilll insists on crashing when trying to boot. The istallation process works great, just the booting after installing is when it doesn't work. The graphics card is a Nvidia which is on the motherboard, this computer worked great for years and now it just will not work.

---

### Post by LastDino on 2014-05-04
Have you tried installing the non-free drivers for the GPU and try?

---

### Post by Ikenna_Onwuzuka on 2014-05-06
It maybe that you need to re-install your desktop. So when you restart your computer and it stalls at the black screen,
Try Ctrl+Alt+F4 then enter your username and password.
After that do this: 
sudo apt-get install ubuntu-desktop &#8211;reinstall
or
sudo dpkg -reconfigure ubuntu -desktop

---

