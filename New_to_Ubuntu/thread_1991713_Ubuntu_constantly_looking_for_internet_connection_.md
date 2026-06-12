---
title: "Ubuntu constantly looking for internet connection after 12.04 upgrade"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by jennifermq on 2012-05-30
I updated to 12.04 a few days ago and ever since then the connection manager has constantly been looking for an internet connection and saying the network is disconnected. Thing is, my modem has been sending out a steady signal and I've had internet connectivity the whole time. When I click on the connection icon in the top right bar the drop down menu pops down but it won't let me open anything on the menu. I'm sure I just need to do some tweaks in the connection manager but without being able to open it I'm stuck. Does anyone have any ideas what's going on with my crazy connection manager? If I see that damn pinwheel and the black connection box one more time I might slap my computer :mad:

---

### Post by wildmanne39 on 2012-05-30
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jennifermq on 2012-05-31
Sorry for the wait, here you go

quinones@quinones-desktop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux quinones-desktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 athlon i386 GNU/Linux
quinones@quinones-desktop:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0153]
    Kernel driver in use: forcedeth
quinones@quinones-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 005: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 006: ID 046d:0a14 Logitech, Inc. 
Bus 001 Device 009: ID 05dc:c753 Lexar Media, Inc. 
quinones@quinones-desktop:~$ iwconfig
eth7      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

eth0      no wireless extensions.

quinones@quinones-desktop:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
quinones@quinones-desktop:~$ lsmod

---

### Post by wildmanne39 on 2012-05-31
Hi, is your wireless card an internal card? I do not see one.

In usb it shows > motorola BCS, Inc. SurfBoard SB5101 Cable Modem
but that should not be it.

Is this being used in virtualbox or another virtual environment?

Please try again:
```
lsmod
```
There should be a lot of output.
Thanks

---

### Post by idoitprone on 2012-05-31
> **wildmanne39 said:**
> Hi, is your wireless card an internal card? I do not see one.

In usb it shows 
but that should not be it.

Is this being used in virtualbox or another virtual environment?

Please try again:
```
lsmod
```There should be a lot of output.
Thanks
Wildmann its neither since it is a device that is used to be pluged into the houses's cable wires to be converted into internet

The OP is getting internet via usb device

[http://www.motorola.com/Video-Solutions/US-EN/Products-and-Services/Voice-and-Data-Consumer-Premise-Equipment/DOCSIS-Modems-Gateways-and-eMTAs/Cable-Modems/SB5101_US-EN](http://www.motorola.com/Video-Solutions/US-EN/Products-and-Services/Voice-and-Data-Consumer-Premise-Equipment/DOCSIS-Modems-Gateways-and-eMTAs/Cable-Modems/SB5101_US-EN)

I have that ```
motorola BCS, Inc. SurfBoard SB5101 Cable Modem                      

```why are you directly plugging in a cable to internet modem with a usb cable? You realize that you can plug an ethernet cable to a router and you have internet for your whole house?
hmmmm

---

### Post by wildmanne39 on 2012-05-31
Hi, something I missed you said internet connection not wireless, I was on auto pilot.

A lot of times the driver for that ethernet card needs an extra parameter:
```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```
If it is as idoitprone suggests then I would use an ehternet cable instead.
Thanks

---

