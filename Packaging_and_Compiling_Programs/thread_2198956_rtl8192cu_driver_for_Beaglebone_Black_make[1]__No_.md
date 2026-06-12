---
title: "rtl8192cu driver for Beaglebone Black make[1]: *** No rule to make target `module'"
date: 2014-01-11
forum: Packaging and Compiling Programs
---

### Post by y34371forum on 2014-01-11
Hello everyone. I'm new to arm-linux. I want to get the usb wifi work on my BeagleBone Black. I followed the instruction "Quick_Start_Guide_for_Driver_Compilation_and_Installation.pdf" in the document folder, but no success. The error is shown below:

```
root@Probook-Ubuntu:/home/albert/WLAN/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911# make
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -C /home/albert/WLAN/build_out M=/home/albert/WLAN/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory `/home/albert/WLAN/build_out'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/home/albert/WLAN/build_out'
make: *** [modules] Error 2
```

I tried many [SOLVED] solutions but none of these woked for me. 

```
root@Probook-Ubuntu:~# uname -a
Linux Probook-Ubuntu 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
root@Probook-Ubuntu:/usr/src# ls
linux-headers-3.2.0-58          linux-headers-3.8.0-29          linux-headers-3.8.0-34          linux-headers-3.8.0-35
linux-headers-3.2.0-58-generic  linux-headers-3.8.0-29-generic  linux-headers-3.8.0-34-generic  linux-headers-3.8.0-35-generic
```

I added the following code to the Makefile

```

CONFIG_PLATFORM_BBB = y
ifeq ($(CONFIG_PLATFORM_BBB), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
ARCH := arm
CROSS_COMPILE := arm-linux-gnueabihf-
KSRC := /home/albert/WLAN/build_out
endif


```

Can anyone help me? Thanks!

---

### Post by oldos2er on 2014-01-11
Moved to Packaging & Compiling Programs.

---

### Post by varunendra on 2014-01-14
Welcome to the forums y34371forum !

Which wireless chip you need this driver for? I'm not sure if the compiling process is different on ARM platform, but guess the required components are same - the headers and gcc libraries (build-essential).

To show us which wireless chip your dongle has, please post the output of -
```
lsusb
```
while the dongle is plugged in.

---

### Post by y34371forum on 2014-01-15
Thank you for replying. This is the output of lsusb

Bus 001 Device 004: ID 0bda:8176 Realtec Semiconductor Corp.  RTL8188CUS 802.11n WLAN Adapter

I just find out the driver RTL8192CU in ubuntu embedded linux can drive this device. But this shows a very unstable pattern. When I boot my arm, it cannot connect to the wifi. But I can see the device is sending and receiving data from ifconfig.  After around 10 minutes, it automatically connected to wifi. How can I make it connect to wifi right after I boot the arm? Thanks.

---

### Post by varunendra on 2014-01-18
> **y34371forum said:**
> How can I make it connect to wifi right after I boot the arm?

You may try a parameter that is available with the default driver (assuming that is the one that is loading currently) -
```
echo "options rtl8192cu swenc=1" | sudo tee /etc/modprobe.d/rtl8192cu.conf
```
From next boot, the driver will load with parameter "swenc=1". If that doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

**PS:**
I may not be able to respond in a timely fashion, too busy these days. So you may wish to invite other potential helpers to take a look at your wireless report. Just browse the "Networking & Wireless" section of the forums and you'll find many who are much better and regular than me. :)

---

