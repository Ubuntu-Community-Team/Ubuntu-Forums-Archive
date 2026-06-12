---
title: "Major Graphic Issue"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by andrei21 on 2015-09-08
So guys one day i wanted to install ubuntu,so i installed 15.04.I succesfully installed but after log in screen is flickering and keep freezing.I installed the nvidia driver for my gpu 8400M G.That solved nothing..I tried every ubuntu version with unity.It seems that unity is the problem right here because when i installed ubuntu 10.04(gnome based) it worked pretty fine.So what can i do i really like unity and i want to use it..:(

My Laptop is Fujitsu Siemens e8400:

Intel core 2 duo e7250 2GHZ
2GB Ram
Gpu:Nvidia 8400M G which supports shader 4.0

P.S:Only version which worked and has unity was 11.04 but support has ended years ago

---

### Post by v3.xx on 2015-09-08
If your dead set on Unity, try Ubuntu 12.04.  It has Unity 2D and will be supported till 2017.

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by sandyd on 2015-09-08
Sounds like [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/456637](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/456637)

Seems to be caused by powermizer
Try
```

sudo nano /etc/modprobe.d/nvidia.conf

```

Copy/Paste the following in, press control+x to save, and reboot computer
```

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

---

### Post by andrei21 on 2015-09-08
on unity 2d is the same i said that i tryed all ubuntu with unity and get the same thing and i will try what did you said sandyd

P.S:Sometimes i have to use kill -9 -1 to log in.Why
And i should try ubuntu wthout to install and the install it,not restarting installing the nvidia driver and write those in terminal(i am very begginer with linux,sorry for my english)

---

### Post by grahammechanical on 2015-09-08
The Nvidia web site tells me two things about your graphic adapter.

1) the maximum video memory is 256MB. In my opinion even twice that amount that would give a minimal visual user experience. But you never know.

2) the Nvidia driver to install is nvidia 340.93. This means that the very latest Nvidia drivers do not support that video adapter. This is an important point because when we install and tick the box "Install third party software" we get some proprietary audio and video codecs and a proprietary video driver. And what is more the latest versions of Ubuntu install the newer video drivers.

So, the install of 10.04 is giving you a proprietary video driver from the same era as that video card. But 15.04 might be bringing a driver that does not support that card. I am in the same situation. My advice is to not tick the box to install third party software then when the install is finished the restart will load an open source video driver (Nouveau). That might give a satifactory performance. To set a proprietary video driver (legacy) go to System Settings>Software & Updates>Additional Drivers tab. You need to be connected to the internet and to allow time for the utility to find the drivers for you.

To install the third party audio & video codecs look in the Ubuntu Software Centre for Ubuntu Restricted Extras. 

I have a Nvidia GT220 and that is running on driver 304.125 (legacy). I could also use driver 340.76 (legacy) if I choose but I am not offered anything newer. And am using Ubuntu 15.10 development version.

Regards

---

### Post by andrei21 on 2015-09-08
I installed Ubuntu 14.04.3 LTS so i should put 340.76 or 304.125?(and i think the flickering was because my gpu reacher 73 degrees celsius)

P.S:I was looking on nvidia website and it says that the 340.76 driver is compatible with Nvidia 8400M G

---

### Post by deadflowr on 2015-09-08
> **andrei21 said:**
> I installed Ubuntu 14.04.3 LTS so i should put 340.76 or 304.125?(and i think the flickering was because my gpu reacher 73 degrees celsius)


Do you have a fan running on that thing?

---

### Post by v3.xx on 2015-09-09
I use to have a 8400 card in a desktop.  Fanless with a giant heat sink; you could fry an egg on it.  The OP has it in a laptop and is going to turn up the heat with Unity?

Driver support for this card started at something like 178.  I do not think it will matter much if you use the 304 or 340 driver.

---

### Post by andrei21 on 2015-09-09
I think not but last night i left the laptop in idle and something happened i will come back with the photo

I get a **** like this (is not my photo i founded on internet but the screen is the same)[IMG]http://i.stack.imgur.com/BGQiy.jpg[/IMG]

---

### Post by andrei21 on 2015-09-09
> **sandyd said:**
> Sounds like [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/456637](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/456637)

Seems to be caused by powermizer
Try
```

sudo nano /etc/modprobe.d/nvidia.conf

```

Copy/Paste the following in, press control+x to save, and reboot computer
```

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```
 
It seems that this done the job.Everything works fine with the noveau driver every time i was opening dash the screen is messed up but now its fine

---

