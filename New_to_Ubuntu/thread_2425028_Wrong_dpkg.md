---
title: "Wrong dpkg"
date: 2019-08-19
forum: New to Ubuntu
---

### Post by picubed on 2019-08-19
I have a Raspberry Pi 3B+ and I installed Ubuntu 18.04 Bionic Beaver on it. I used etcher to flash the OS to the Pi. I set up my account and everything is working fine. But I have one problem. I tried installing a couple .deb files such as Google Chrome with Gdebi Package installer and it brought up the massage "Error: Wrong architecture 'amd64.'" 

Dpkg is using the wrong architecture. I need Armv7l version because I am running this on a Raspberry Pi. I am having trouble getting an arm architecture. Please help me...

Thanks,

Pi Cubed

---

### Post by TheFu on 2019-08-19
Not all packages are made for ARM.  [https://askubuntu.com/questions/590482/downloading-google-chrome-armhf](https://askubuntu.com/questions/590482/downloading-google-chrome-armhf)
Try using chromium-browser.

---

### Post by picubed on 2019-08-19
Oh, so some apps need to be made for arm. How would I get virtualBox? [https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by uRock on 2019-08-19
> **picubed said:**
> Oh, so some apps need to be made for arm. How would I get virtualBox? [https://www.virtualbox.org/](https://www.virtualbox.org/)

You want to run a VM on a RaspberryPi?

---

### Post by TheFu on 2019-08-19
> **picubed said:**
> Oh, so some apps need to be made for arm. How would I get virtualBox? [https://www.virtualbox.org/](https://www.virtualbox.org/)

Different CPUs have different capabilities.   I don't know much about ARM CPU support for fast context changes, but both Intel and AMD in their 64-bit CPUs adds that specific set of instructions to support virtual machines. VT-x and AMD-v are their marketing terms.

There are software VMs, which are significantly slower.  QEMU is probably the best. [https://community.arm.com/developer/tools-software/oss-platforms/w/docs/415/spawn-a-linux-virtual-machine-on-arm-using-qemu-kvm](https://community.arm.com/developer/tools-software/oss-platforms/w/docs/415/spawn-a-linux-virtual-machine-on-arm-using-qemu-kvm)  I've read they are 10,000x slower on ARM.

I haven't used virtualbox anywhere in a long time. I've heard there is a F/LOSS version, so the code should be available. Get the code and compile it.  I suspect there will be some assembly language, which is specific to the CPU and if it hasn't been ported to ARM, then you'll need to do that port yourself.  How's your x68-64 and ARM assembly language?  If it hasn't been ported already, I suspect it is because ARM CPUs don't have the support necessary for virtualization.  Found this which explains some: [https://forums.virtualbox.org/viewtopic.php?f=9&t=65426](https://forums.virtualbox.org/viewtopic.php?f=9&t=65426)

I use virtual machines all the time. I'm using one to type this now, since my main desktop is actually a virtual machine running in a private cloud.

[Apropos cartoon.]("https://i.imgur.com/z96dZ0x.jpg")

---

### Post by TheFu on 2019-08-19
BTW, any Linux containers that you build are sorta like virtual machines, but not really.  Linux containers are part of linux since the 2.6.x kernel time and don't require any hardware support to work.  There are limitations - you can only run programs written for Linux with the same CPU architecture inside a Linux container.  

But I'm confused how needing a browser like chrome is connected to using a hypervisor?  Chromium is the browser that Chrome is based from. The are almost identical, just with less "google" and no DRM video support.  People use chromium for all the google-docs stuff just fine and it should have a pre-built package for any ARM linux distro.

---

