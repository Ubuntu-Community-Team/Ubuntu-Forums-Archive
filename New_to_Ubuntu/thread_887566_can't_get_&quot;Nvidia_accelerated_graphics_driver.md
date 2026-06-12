---
title: "can't get &quot;Nvidia accelerated graphics driver&quot;"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by slaabrockband on 2008-08-12
Clean installation ubuntu 8.04  : when I try to enable that driver
for geforce 3 I get following error message:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb)
  404 Not Found


NB   My internet connection is ok

---

### Post by tuxxy on 2008-08-12
Did you try enable the driver at system > admin > hardware drivers

---

### Post by slaabrockband on 2008-08-12
> **tuxxy said:**
> Did you try enable the driver at system > admin > hardware drivers

yes I get the same message

---

### Post by Riffer on 2008-08-12
Try another server.

Drop down menu "System > Administration > Software Sources" in there is a section where you can choose different servers, try that.

---

### Post by LowSky on 2008-08-12
Go to Add/Remove look for EnvyNG
it will install drivers from Nvidia's website

---

### Post by Elfy on 2008-08-12
I'm connected to main - the file it appears to be trying to get is not actually there to retrieve - perhaps it's been updated


[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/)

there are 

12-16.34
13-19.45
14-20.46 versions available

but no 13-18.41 which is apparently what the hardware drivers tools is trying to get. You could try later and see if it has caught up or maybe try to install it with envyng.

---

### Post by slaabrockband on 2008-08-12
> **Riffer said:**
> Try another server.

Drop down menu "System > Administration > Software Sources" in there is a section where you can choose different servers, try that.


That helped. Thanks a lot

---

### Post by glennric on 2008-08-12
Have you tried doing "sudo apt-get update" to make sure your package lists are up to date?

---

### Post by LowSky on 2008-08-12
If you have the newest kernel try this command, copy and paste into terminal

```
wget -c http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/avm-fritz-firmware-2.6.24-20_3.11+2.6.24.14-20.46_i386.deb
sudo dpkg -i avm-fritz-firmware-2.6.24-20_3.11+2.6.24.14-20.46_i386.deb
```

---

