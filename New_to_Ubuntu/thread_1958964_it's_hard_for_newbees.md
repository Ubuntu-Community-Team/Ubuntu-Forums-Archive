---
title: "it's hard for newbees"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by caboextrem on 2012-04-15
[FONT=Arial][SIZE=3]hi all,
me is an absolute newbee with ubuntu 10.xx
an now i want ti use my webstick with this 
but i have a problem with this - let me tell it - dificult installing - 
i try to get the right stuff (software) to plug in my stick
it is an vodafone model e160e hsdpa usb stick-
can tell me someone - what in hell i have to do ???
where can i find this needed thinks and - if i get this - i can hanel it to install this on my laptop?
thanks to all):P
[/SIZE][/FONT]

---

### Post by Rex Bouwense on 2012-04-15
Try this.  
[http://ubuntuforums.org/showthread.php?p=9572175#post9572175](http://ubuntuforums.org/showthread.php?p=9572175#post9572175)
It seemed to work for the OP.
By the way welcome to the forums.

---

### Post by audiomick on 2012-04-15
Hallo.
You may possibly need a package called "usb-modeswitch".

Look at this thread.
[http://openubuntu.com/index.php/topic,972.0.html]("http://openubuntu.com/index.php/topic,972.0.html")

You can no doubt install it throught the software centre. On this 11.10 install, it is installed by default, but I had to install it on my laptop in 10.04 and 10.10, I think. Open the software centre and search for "modeswitch".

Your webstick, which I assume is a USB stick for using the internet via the moblie telephone network, also known as a 3G dongle in some countries and a UMTS stick here in Germany, is very likely also a Hauwaei model. The seem to make an awful lot of those things.

To check this, plug it in, then type "lsusb" in a terminal.
This is what I get
```
mick@mick-MS-7345:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 005 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 006 Device 002: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270 HSDPA/HSUPA Modem

``` 
The last entry is my 3G Dongle.

What the Modeswitch package does is this: The stick has a mechanism aimed at windows machines that makes it start the installer when it is plugged in for the first time. Once this has been run, an identifier is switched to make it appear as a USB modem when it is plugged in. If the stick has never been installed on a windows computer, this needs to be switched so that the Linux Network manager can "see" the USB modem. Modeswitch does this. Install it, reboot and then plug in the webstick again and see if it works. If it doesn't work, the modeswitch package will not hurt your system (or you can remove it). I can't help you any further in that case, I'm sorry, so I hope this works. ;)

---

### Post by 3rdalbum on 2012-04-15
I don't think you necessarily need to install anything to get it to work; you plug it in, go to the Network Manager applet on the top panel, click it and choose Edit Connections. Go to the Mobile Broadband tab and click Add, and follow the prompts.

If this doesn't work, then you should seriously look at using a later version of Ubuntu. 10.04 is old; ancient in Linux terms. Ubuntu 12.04 is just about to come out in ten days or so and includes more recent hardware support. Things that are difficult to do in 10.04 may be "plug and play" in 12.04.

---

### Post by SeijiSensei on 2012-04-15
Mentioning your problem to Vodafone support might be a good thing to do as well.  They'll probably have no idea about what to do with Ubuntu, but you might be another voice asking them for better Linux support in the future.

---

### Post by Paqman on 2012-04-15
> **3rdalbum said:**
> I don't think you necessarily need to install anything to get it to work; you plug it in, go to the Network Manager applet on the top panel, click it and choose Edit Connections. Go to the Mobile Broadband tab and click Add, and follow the prompts.

If this doesn't work, then you should seriously look at using a later version of Ubuntu. 10.04 is old; ancient in Linux terms. Ubuntu 12.04 is just about to come out in ten days or so and includes more recent hardware support. Things that are difficult to do in 10.04 may be "plug and play" in 12.04.

^This is all good advice. Support for 3G dongles has significantly improved in the last couple of years. If it doesn't "just work" with 10.04 you'll probably find that it does with a newer version. You can try it out with a LiveCD or USB first.

---

### Post by audiomick on 2012-04-16
> **3rdalbum said:**
> I don't think you necessarily need to install anything to get it to work; you plug it in,...If this doesn't work, then you should seriously look at using a later version of Ubuntu. 10.04 is old; ...

> **Paqman said:**
> ^This is all good advice. Support for 3G dongles has significantly improved in the last couple of years. If it doesn't "just work" with 10.04 you'll probably find that it does with a newer version

This is true: the Dongle will probaly "just work" with a newer version of Ubuntu. Point is, the OP is using a version where it doesn't, and may not want to upgrade just yet in order to get the dongle working. Installing usb-modeswitch will take all of 2 minutes, and will very likely solve the problem, and then it will "just work" by plugging it in and letting the network manager set it up as 3rdalbum described.


> **SeijiSensei said:**
> Mentioning your problem to Vodafone support might be a good thing to do as well.  They'll probably have no idea about what to do with Ubuntu, but you might be another voice asking them for better Linux support in the future.

+1 for this. Ringing them up wont change anything quickly, but may turn up in a statistic somewhere that may, in the long run, improve the support for Linux systems.

---

