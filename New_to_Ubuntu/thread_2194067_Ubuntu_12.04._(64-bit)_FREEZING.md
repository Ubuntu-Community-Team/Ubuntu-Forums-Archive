---
title: "Ubuntu 12.04. (64-bit) FREEZING"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by markokos01 on 2013-12-16
Hello, I'm new Ubuntu user. Recently I have Windows 7 and I made clean installation of Ubuntu 12.04 64-bit version. After few seconds of using, I'm unable to do anything, screen is totaly freezing (can move mouse or anything), and restart of computer didn't help. Only thing I can do is to turn off computer. I read something about that on internet, and I see a lot of people had this problem. I installed this version beacuse people were saying it's stable version. What do you suggest me to do? Will reinstall fix this bug? Thank you.

---

### Post by ajgreeny on 2013-12-16
This is most likely a hardware problem of some kind, and probably a poorly configured or installed driver.

What hardware have you got?  For a start let's see the output of the commands **lspci** and **lsusb,** one by one in terminal.

---

### Post by markokos01 on 2013-12-16
On Windows7 everything worked perfectly, and laptop is bougth 6 months ago. I don't have any problems until I installed Ubuntu 12.04. I'll post later which hardware I've got.

---

### Post by jones quest on 2013-12-16
There is a known bug in 12.04 64bit which sounds similar to what you have:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)
Probably a hardware/driver problem as suggested by ajgreeny.

Did you try the live DVD before you installed ubuntu? Usually these problems show up already in that environment. You could try the latest version of ubuntu (13.10) to see if the problem still persists.

---

### Post by markokos01 on 2013-12-16
I've installed with DVD, and first I tried it. I've done everything that is explain in tutorial. I have not recognized this problem before I installed it. It's very frustrating, everything worked well until I istalled 12.04. I'll try with version 13.10.

---

### Post by markokos01 on 2013-12-16
Will this solve the problem: [http://richxiong89.wordpress.com/2012/11/15/system-freeze-on-ubuntu-12-04-64-bit/](http://richxiong89.wordpress.com/2012/11/15/system-freeze-on-ubuntu-12-04-64-bit/) ?
I tried this, but when comes last step with some when it's writing <Ok> i can't do anything.

---

### Post by markokos01 on 2013-12-16
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1154006](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1154006) This is exacly what happens to me.

---

### Post by jones quest on 2013-12-17
The solution you linked to replaces the kernel with a newer one ([http://richxiong89.wordpress.com/2012/11/15/system-freeze-on-ubuntu-12-04-64-bit/](http://richxiong89.wordpress.com/2012/11/15/system-freeze-on-ubuntu-12-04-64-bit/)). The idea is that a hardware compatibility bug that is causing the freezing is fixed in a more recent linux kernel. If this is true for you, then replacing the kernel could fix your problems. Replacing the kernel is also the suggested in most of the bug tracks similar to this.

Ubuntu 12.04 originally shipped with linux kernel 3.2. In the solution the default kernel is replaced with kernel 3.4. However in the latest release of ubuntu 12.04.3 the kernel has already been backported to 3.8 (specifically because of hardware problems). So the solution above probably wouldn't fix your problem if your using the latest release. 

You can check which kernel you have (even in the live DVD environment) with:
uname -r

You should see:
3.8.0-29-generic (for ubuntu 12.04.3 64bit)

The linux kernel in Ubuntu 13.10 is 3.11, which is the reason why I suggested trying Ubuntu 13.10. A new version of linux kernel typically has better support for new hardware. As your computer is only 6 months old this would probably be the best bet for a working solution. Using a live DVD for an extended period should reveal hardware compatibility problems if they exist. However this doesn't always happen, as the live environment isn't using the hardware's full capabilities (for instance it's not writing to the disk, etc.). Problems can also arise after the installation. For example a kernel update can occasional cause a regression that make a particular system unstable. However this is very rare, and if it does occur, you can always select a previous kernel during boot up, and roll back.

---

### Post by markokos01 on 2013-12-17
Problem fixed with installing Ubuntu 13.10. But only thing I recognized, temperature is going high, it's overheating. But laptop is new, there is no dust anywhere and on Windows 7 I haven't got any problems with high temperature. Do you know how to fix this?

---

### Post by jones quest on 2013-12-17
You can check what is causing temperature increase with lm-sensors and set a higher fan speed with fancontrol. These depend on bios ACPI settings to work though.

[http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

---

### Post by jones quest on 2013-12-17
Without knowing the hadware specs it's difficult to say, but your overheating could  be due to poor power management of the cpu or video card.
[http://askubuntu.com/questions/203960/high-temperature-on-my-laptop-with-radeon-mobility-hd4670](http://askubuntu.com/questions/203960/high-temperature-on-my-laptop-with-radeon-mobility-hd4670)

---

### Post by markokos01 on 2013-12-17
[https://www.dropbox.com/s/ttjbn0p6bf2d4ya/hardware_info.html](https://www.dropbox.com/s/ttjbn0p6bf2d4ya/hardware_info.html)

Maybe this will help. I don't have any problems until installing Ubuntu. With Win7 laptop was cool, but now everything is hot.

---

### Post by markokos01 on 2013-12-17
acpitz-virtual-0
Adapter: Virtual device
temp1:        +75.0°C  (crit = +101.0°C)
temp2:        +74.0°C  (crit = +101.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +70.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +70.0°C  (high = +105.0°C, crit = +105.0°C)


And this will maybe useful. I see here is everything OK, but my laptop is too hot.

---

### Post by jones quest on 2013-12-17
It appears that both windows and linux users have reported heat problems with Acer Aspire 5738.
[http://www.techsupportforum.com/forums/f217/acer-aspire-5738zg-randomly-freezes-626331.html](http://www.techsupportforum.com/forums/f217/acer-aspire-5738zg-randomly-freezes-626331.html)
[http://ubuntuforums.org/showthread.php?t=1854391](http://ubuntuforums.org/showthread.php?t=1854391)
[https://bbs.archlinux.org/viewtopic.php?id=90869](https://bbs.archlinux.org/viewtopic.php?id=90869)

There's even an alert posted on acer's website.
[http://customercare.acer-euro.com/customercare/AcerUpdate.aspx?CID=GB&LID=ENG&IType=JV50](http://customercare.acer-euro.com/customercare/AcerUpdate.aspx?CID=GB&LID=ENG&IType=JV50)

First of I suggest you chech if there above alert conserns your computer. Then download the latest bios update.
You could also try installing the latest proprietary driver for the graphics card (as this might also be part of the problem). And a power management tool for setting the cpu usage lower. Many say TLP is good, thought its not the official repos. [http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

---

### Post by markokos01 on 2013-12-17
Thank you very much. And please, can you check for my second laptop, I have a same problem. After installing Ubuntu 13.10 (previous OS is win7 where was cool) laptop started heating. Here is hardware specifications: [https://www.dropbox.com/s/ttjbn0p6bf2d4ya/hardware_info.html](https://www.dropbox.com/s/ttjbn0p6bf2d4ya/hardware_info.html)

Sensors:

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +60.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +59.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +59.0°C  (high = +87.0°C, crit = +105.0°C)

pkg-temp-0-virtual-0
Adapter: Virtual device
temp1:        +60.0°C  

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +59.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

---

