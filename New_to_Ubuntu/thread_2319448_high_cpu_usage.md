---
title: "high cpu usage"
date: 2016-04-04
forum: New to Ubuntu
---

### Post by sunil16 on 2016-04-04
hey im currently using ubuntu and my cpu usage goes to 30% while watching youtube videos or doing some bigger tasks,, my on board ati graphics drivers are not supported for ubuntu. when i used to watch youtube videos on windows7 the computer uses less cpu,,, is this problem because i dont have a proper gpu? what if install new gpu with proprietary drivers will that help? also opensource drivers arent good for playing games online using flash player currently,,, will all these problems be solved if i buy install a new gpu? if yes should i buy amd or nvidia, which is best supported?

---

### Post by v3.xx on 2016-04-04
Please post the output of..

```
inxi -b
```

Thankyou

---

### Post by him610 on 2016-04-04
> cpu usage goes to 30% Not a problem.

You did not report your system specs so it is difficult to provide the advice you seek; however, I can give the following answers to your questions -
no, no, no, not applicable.

---

### Post by sunil16 on 2016-04-04
> **v3.xx said:**
> Please post the output of..

```
inxi -b
```

Thankyou

System:    Host: sun Kernel: 3.19.0-56-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4130 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS780L [Radeon 3000] 
           X.Org: 1.17.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1600x900@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD RS780 GLX Version: 3.0 Mesa 10.5.9
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1000.2GB (0.5% used)
Info:      Processes: 200 Uptime: 2:58 Memory: 1043.9/2926.3MB Client: Shell (bash) inxi: 1.9.17

---

### Post by v3.xx on 2016-04-04
I do not run ATI, so my findings are limited.  But to me, this suggest that your card is supported.

[https://help.ubuntu.com/community/RadeonDriver#Fully_supported](https://help.ubuntu.com/community/RadeonDriver#Fully_supported)

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Better for someone else (with ati experience) to help you out.  Good luck :)

---

### Post by sunil16 on 2016-04-04
> **v3.xx said:**
> I do not run ATI, so my findings are limited.  But to me, this suggest that your card is supported.

[https://help.ubuntu.com/community/RadeonDriver#Fully_supported](https://help.ubuntu.com/community/RadeonDriver#Fully_supported)

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Better for someone else (with ati experience) to help you out.  Good luck :)

amd proprietary driver support for my card is ended as far as i know  ,

---

### Post by ajgreeny on 2016-04-04
> **sunil16 said:**
> amd proprietary driver support for my card is ended as far as i know  ,
I am afraid that you are correct about that.
The driver you must use at present with 14.04 is the radeon driver currently used, and you can not install anything else for your card.

In future the open source driver will be named **amdgpu** I believe, but I can not help with specific information on its ability to do better than the radeon

Here's some links from a thread at [http://ubuntuforums.org/showthread.php?t=2317751](http://ubuntuforums.org/showthread.php?t=2317751) which you may find helpful.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

[http://www.omgubuntu.co.uk/2016/03/u...x-driver-16-04](http://www.omgubuntu.co.uk/2016/03/u...x-driver-16-04)

[https://lists.ubuntu.com/archives/ub...ch/016315.html](https://lists.ubuntu.com/archives/ub...ch/016315.html)

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

---

