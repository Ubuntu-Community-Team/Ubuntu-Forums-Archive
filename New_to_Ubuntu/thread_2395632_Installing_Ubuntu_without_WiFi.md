---
title: "Installing Ubuntu without WiFi?"
date: 2018-07-04
forum: New to Ubuntu
---

### Post by shubanshii on 2018-07-04
Hi there,

I'm using Windows 10 and attempting to install Ubuntu 18.04 on a partition.  I'm using a custom desktop.  

The desktop has no built in wifi capability, so I use a Netgear A6210 to access wifi.

All of the installation guides for Ubuntu say you want to be connected to the internet for the installation.  The problem is that my pc doesn't automatically start using the A6210, and there is not much support for using the device with Ubuntu.  

Is it fine to install Ubuntu into the partition without internet access, and figure out internet access later?

If so, can anyone here help me get wifi using Ubuntu with my A6210?  

[https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)

I found this, but it's old and doesn't seem like a user friendly way for a new person to get started using Ubuntu on a desktop.

Thanks in advance

---

### Post by cariboo on 2018-07-04
I haven't tried installing 18.04 without a network connection, but I have installed most previous versions without wifi. Make sure you don't mark updates and drivers for download while doing the install.

---

### Post by The Cog on 2018-07-04
You may find yourself in a catch-22 where you can't download the required wifi drivers because the wifi doesn't work. You would do well to try to find an ethernet connection to use while installing. However, installing without any internet at all does indeed work.

---

### Post by jeremy31 on 2018-07-04
If that is USB wifi device, plug it in and post results from terminal for ```
lsusb
```

---

### Post by shubanshii on 2018-07-04
It is a USB wifi device, but before I proceed ... I just realized that I didn't make an educated choice regarding the boot device. 

Last time I used UEFI: HL-DT-ST DVDRAM GH24NSBO.  Should I use that one or AHCI P4: HL-DT-ST DVDRAM GH24NS?

---

### Post by shubanshii on 2018-07-04
> **jeremy31 said:**
> If that is USB wifi device, plug it in and post results from terminal for ```
lsusb
```
So I went ahead and did try ubuntu, and entered the command.

I received the following:

```
Bus 002 Device 002:  ID 8087:8000 Intel Corp.
Bus 002 Device 001:  ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002:  ID 8087:8008 Intel Corp.
Bus 001 Device 001:  ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001:  ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003:  ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 003 Device 004:  ID 1038:0210 SteelSeries ApS
Bus 003 Device 002:  ID 0846:9053 NetGear, Inc.
Bus 003 Device 001:  ID 1d6b:0002 Linux Foundation 2.0 root hub

```

If you could also answer my question regarding AHCI vs UEFI mode, I'd appreciate it.

---

### Post by ajgreeny on 2018-07-04
I have **never** bothered with wifi when installing on a laptop with wifi hardware and have always updated all packages after the OS was rebooted; it is much the quicker way to get the fully updated OS in my opinion.

Even on my main desktop with ethernet only I also do not update whilst installing but wait until after the installation is complete, then update everything.

It is, however, definitely worth seeking out an ethernet connection if possible when you reboot the new OS if the live system you use to install does not connect to wifi as you could otherwise have problems getting wifi working after rebooting simply because you can not get updated drivers or whatever is needed.

If your Windows 10 was preinstalled on the machine it will be in UEFI so you must also install Ubuntu in UEFI mode, as you did, for a successful dual boot system.

---

### Post by kurt18947 on 2018-07-04
I keep an old ugly wifi adapter that is recognized by every distro I've tried since at least 2009. It's slow and obsolete but it will enable me to download updates and drivers for the latest gee-whiz devices. Another option would be if you have an unused router that one of the 3rd party router firmware support (Open-WRT, DD-WRT etc.) convert it to a wireless ethernet bridge. Here's one set of instructions.

[https://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](https://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

It can be useful to have a portable pseudo ethernet port where there's no wire.

---

### Post by shubanshii on 2018-07-05
OK, so I thought I had it solved by using an Ethernet cable from my laptop, which is connected to the wifi.  It worked on windows.  Then I tried Ubuntu without installing.  I was connected and my internet was working.  Then I installed.  Internet was still working.  Then I removed the installation medium, and restarted.  I opened Windows.  Ethernet connection was still working.  I opened Ubuntu and sadly it was no longer working.  Any idea what's going on?

Edit: solved.  This approach to internet access just has some kinks I have to work out, but I don't think they are Ubuntu related. They're related to my laptop.

---

### Post by dwayne222 on 2018-07-06
Good to know that it got resolved well i have tried also to install ubuntu without wifi before and it's not easy to install it.

---

