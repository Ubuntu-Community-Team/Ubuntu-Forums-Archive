---
title: "kernel 3.0"
date: 2011-06-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrrys on 2011-06-15
i know that this is old news to most, but I loaded it this morning and seems to be working pretty good.  did loose my desktop icons and backgrounds, but thats a small price to pay.

---

### Post by beew on 2011-06-15
> **jerrrys said:**
> i know that this is old news to most, but I loaded it this morning and seems to be working pretty good.  did loose my desktop icons and backgrounds, but thats a small price to pay.

To pay for what? :confused:

I slapped 3.0 rc2 on Natty and everything works (as far as I have tested) but can't say what is the advantage either. rc3 however wouldn't install.

---

### Post by VanR on 2011-06-15
> **beew said:**
> To pay for what? :confused:

I slapped 3.0 rc2 on Natty and everything works (as far as I have tested) but can't say what is the advantage either. rc3 however wouldn't install.

Yep I noticed rc3 wouldn't install also, but rc2 installs fine now.

---

### Post by Starks on 2011-06-15
> **jerrrys said:**
> i know that this is old news to most, but I loaded it this morning and seems to be working pretty good.  did loose my desktop icons and backgrounds, but thats a small price to pay.

a kernel wouldn't do that.

btw, rc3 is on the way
[https://launchpad.net/ubuntu/+source/linux/3.0-1.2](https://launchpad.net/ubuntu/+source/linux/3.0-1.2)

---

### Post by jerrrys on 2011-06-15
no, there were other updates.

---

### Post by jfernyhough on 2011-06-16
To get 3.0-rc3 to install in Natty you need a newer version of module-init-tools (3.13 compared to 3.12). I grabbed the Oneiric binary and everything seems fine.

[https://launchpad.net/ubuntu/oneiric/+source/module-init-tools](https://launchpad.net/ubuntu/oneiric/+source/module-init-tools)

---

### Post by bmbaker on 2011-06-16
> **jfernyhough said:**
> To get 3.0-rc3 to install in Natty you need a newer version of module-init-tools (3.13 compared to 3.12). I grabbed the Oneiric binary and everything seems fine.

[https://launchpad.net/ubuntu/oneiric/+source/module-init-tools](https://launchpad.net/ubuntu/oneiric/+source/module-init-tools)

you can get the deb files here :-)
[https://launchpad.net/ubuntu/+source/module-init-tools](https://launchpad.net/ubuntu/+source/module-init-tools)

---

### Post by jfernyhough on 2011-06-16
You can get the deb from both! :D

---

### Post by jyango on 2011-06-17
sir problem here..im trying to install 3.0rc3 on natty but im having problem upgrading my module-init-tools to 3.13, can u give me a detailed instructions how to do this? thanks

---

### Post by dino99 on 2011-06-17
> **jyango said:**
> sir problem here..im trying to install 3.0rc3 on natty but im having problem upgrading my module-init-tools to 3.13, can u give me a detailed instructions how to do this? thanks

download the needed deb packages into an empty folder, then cd to that path, and finally:

sudo dpkg -i *

---

### Post by jyango on 2011-06-19
thanks sir now running natty on 3.0rc3....everything seems running okay...thanks again sir

---

### Post by linuxman94 on 2011-06-19
Installing 3.0rc3 on natty with fglrx doesn't work because it fails to install the fglrx kernal module.

---

### Post by Harry33 on 2011-06-19
> **linuxman94 said:**
> Installing 3.0rc3 on natty with fglrx doesn't work because it fails to install the fglrx kernal module.

It won't because proprietary drivers need to be patched to work with Linux 3.0 kernels.
The latest drivers in Oneiric repos are patched.

---

### Post by sparker256 on 2011-06-19
> **Harry33 said:**
> It won't because proprietary drivers need to be patched to work with Linux 3.0 kernels.
The latest drivers in Oneiric repos are patched.
At this point in time does not seem to like Nvidia-Current is very happy. I did a fresh install with 061911 daily live usb 64 bit and when I tried to update to Nvidia-Current I saw this. Not sure what this is all about but will wait for a updated driver unless there is a reason why.

Bill

---

### Post by Harry33 on 2011-06-20
> **sparker256 said:**
> At this point in time does not seem to like Nvidia-Current is very happy. I did a fresh install with 061911 daily live usb 64 bit and when I tried to update to Nvidia-Current I saw this. Not sure what this is all about but will wait for a updated driver unless there is a reason why.
Bill

Do you have the mesa packages of the version 7.10.3 installed?
If so, pay attention to the fact that from that version they need drivers that support multiarch.
ATM proprietary drivers do not support multiarch and cannot be installed together with new mesa.

However, proprietary drivers may be installed into the systems that have the mesa version 7.10.2.

This the bug #798049
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/798049](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/798049)

---

### Post by sparker256 on 2011-06-20
> **Harry33 said:**
> Do you have the mesa packages of the version 7.10.3 installed?
If so, pay attention to the fact that from that version they need drivers that support multiarch.
ATM proprietary drivers do not support multiarch and cannot be installed together with new mesa.

However, proprietary drivers may be installed into the systems that have the mesa version 7.10.2.

This the bug #798049
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/798049](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/798049)
Thanks now running Nvidia Current 275.09.07 with the 7.10.2 version of mesa after about 3 reboots and updates. I did notice that there are over 18 mesa packages that are at version 7.10.3 that are installed and not causing problems that I can tell.  Now on to trying to help resolve more bugs with kernel 3.0.

Is there a apt-get version of this aptitude "sudo aptitude update && sudo aptitude safe-upgrade" command?
Bill

---

### Post by Harry33 on 2011-06-20
> **sparker256 said:**
> Thanks now running Nvidia Current 275.09.07 with the 7.10.2 version of mesa after about 3 reboots and updates. I did notice that there are over 18 mesa packages that are at version 7.10.3 that are installed and not causing problems that I can tell.  Now on to trying to help resolve more bugs with kernel 3.0.

Is there a apt-get version of this aptitude "sudo aptitude update && sudo aptitude safe-upgrade" command?
Bill

If you want to use apt, then run:
sudo apt-get update
sudo apt-get dist-upgrade

I personally only use Synaptic to really see what is going to happen and all the dependencies for that.

---

### Post by jyango on 2011-06-21
Kernel 3.0rc4 Released!c:

---

### Post by jyango on 2011-06-21
Kernel 3.0rc4 Released!c: i'll report later if everything is A Okay...

---

### Post by jyango on 2011-06-21
successful upgrade!, now running natty on kernel 3.0rc4, everything seems to be okay....

---

