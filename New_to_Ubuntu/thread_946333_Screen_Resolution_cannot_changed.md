---
title: "Screen Resolution cannot changed"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by kunaljain on 2008-10-13
I have installed Ubuntu Ultimate 1.9 and installed the NVIDIA Driver of which i was given an option in Hardware Driver.
All the effects are being provided but i am not able to change the resolution of the screen from 640x480.
I have NVIDIA GeForce 6150

---

### Post by Nxion on 2008-10-17
Can you post the output of:

```
cat /etc/X11/xorg.conf
```

So after you enabled the driver in Hardware Drivers and rebooted the resolution was set to 640x480?

---

### Post by HittingSmoke on 2008-10-17
> **kunaljain said:**
> I have installed Ubuntu Ultimate 1.9 and installed the NVIDIA Driver of which i was given an option in Hardware Driver.
All the effects are being provided but i am not able to change the resolution of the screen from 640x480.
I have NVIDIA GeForce 6150

I have the same problem when installing resctricted drivers via the Driver Manager with my Nvidia card. I have to use EnvyNG to install my Nvidia drivers to get full support.

```
sudo apt-get install envyng-gtk
```

Run that from Applications > System Tools and use it to automatically download and install all the files you need.

---

