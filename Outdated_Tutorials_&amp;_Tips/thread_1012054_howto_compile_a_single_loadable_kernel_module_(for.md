---
title: "howto: compile a single loadable kernel module (for the sitecom WL-168v1 004)"
date: 2008-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by martinbaselier on 2008-12-15
Since it took me quite some time, to find out how to compile a single loadable kernel module (lkm), I decided to share my knowledge with others. 

I'm gonna show you how to do it with a real life example. 

I happen to own a wireless usb-stick, which has a supported chipset, but is not supported in the current stable kernel (2.6.27-9-generic)
My wireless stick is a sitecom WL-168 v1 004, which happens to have the realtek 8187B-chipset.

Linux actually showed me this :)

```
# lsusb
...
Bus 001 Device 006: ID 0df6:0028 Sitecom Europe B.V. 
...
# lsub -vd 0df6:0028
  ...
  iManufacturer           1 Manufacturer_Realtek
  iProduct                2 RTL8187B_WLAN_Adapter
  ...
```
explanation : -d shows only information for the specified device, and -v is for verbose output, so you can get the extra information you'll need.  


First you'll need the latest kernel headers and the kernel source.
```
# sudo apt-get install linux-source linux-headers-`uname -r`
```

Then we need to unpack the source code.
```
# cd /usr/src
# tar -xvjf linux-source-2.6.27.tar.bz2
```

Let's find the source of the module and go to the directory. 
```
# find | grep rtl8187
./linux-headers-2.6.27-9-generic/include/config/rtl8187.h
./linux-source-2.6.27/drivers/net/wireless/rtl8187_rtl8225.h
./linux-source-2.6.27/drivers/net/wireless/rtl8187_rtl8225.c
./linux-source-2.6.27/drivers/net/wireless/rtl8187.h
./linux-source-2.6.27/drivers/net/wireless/rtl8187_dev.c
# cd linux-source-2.6.27/drivers/net/wireless/
```

Now you want to check the makefile to find the information about the files we'll need. 
```
s# cat Makefile | grep 8187
rtl8187-objs		:= rtl8187_dev.o rtl8187_rtl8225.o
obj-$(CONFIG_RTL8187)	+= rtl8187.o
```
So now we know the files which we need are rtl8187_dev.c and rtl8187_rtl8225.c and of course the corresponding .h file(s).
*FYI: the makefile in this folder is not standalone, but is meant to be used by /usr/src/linux-source-2.6.27/Makefile*

Since I only want to compile one module and not mess up the makefile in the directory I'm in, I will create a new directory 
in my home folder for testing and compiling and copy all the necessary files to it. 
```
# mkdir ~/rtl8187
# cp rtl8187* ~/rtl8187
# cd ~/rtl8187
```

We're gonna create our own makefile to build the module. 
Use you're favorite editor to edit the file. 
I'm running xubuntu, so mine is mousepad. 
```
#mousepad Makefile
```

This is what's going to be in it: 

```
obj-m := rtl8187.o 
# this is the object, we're gonna make (actually rtl8187.ko) 
# normally make would look for rtl8187.c to compile it.
# since it needs different files for input, we need to tell it:
rtl8187-objs := rtl8187_dev.o rtl8187_rtl8225.o
# make knows to compile these it needs rtl8187_dev.c and rtl8187_rtl8225.c

 
# then we need a few basic rules for cleaning and compiling. 
all:
	$(MAKE) -C /lib/modules/`uname -r`/build M=`pwd` modules

clean:
	$(MAKE) -C /lib/modules/`uname -r`/build M=`pwd` clean
	$(RM) Module.markers modules.order
# -C tells it to switch to the specified directory 
# uname -r gives the current kernel
# -M is the output directory, 
# pwd outputs the current directory
```

Let's test it, since it's the first makefile I ever made.
```
#ls
Makefile   rtl8187_dev.c  rtl8187_rtl8225.c
Makefile~  rtl8187.h      rtl8187_rtl8225.h
#make
error: rtl818x.h: No such file or directory
and a whole lot more errors, oops we're missing a file
# cp /usr/src/linux-headers-2.6.27-9-generic/include/config/rtl818x.h
# make clean
# make
#ls
Makefile        Module.symvers  rtl8187.ko     rtl8187_rtl8225.c
Makefile~       rtl8187_dev.c   rtl8187.mod.c  rtl8187_rtl8225.h
Module.markers  rtl8187_dev.o   rtl8187.mod.o  rtl8187_rtl8225.o
modules.order   rtl8187.h       rtl8187.o      rtl818x.h
#make clean
#ls
Makefile   rtl8187_dev.c  rtl8187_rtl8225.c  rtl818x.h
Makefile~  rtl8187.h      rtl8187_rtl8225.c
```
Everything is working. :)
*FYI: just wanted to add this little trial and error-example above, it took me a whole lot more to create a proper working makefile.*
Now we need to add our device. Let's use my favorite editor. 
```
# mousepad rtl8187_dev.c
```
and add our device. Just open the file and start scrolling down, you will soon see where you need to add the device. 
```
	{USB_DEVICE(0x0df6, 0x0028), .driver_info = DEVICE_RTL8187B},
```
save and exit
```
# make
```
If everything is working fine, you now have rtl8187.ko in your directory.
First let's see where the lkm is located. 
```
#locate rtl8187.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.27-3-rt/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/rtl8187.ko
```
I'm running 2.6.27-9, so that's where I need to copy it to, but lets first make a backup of the original module.
```
# cd /lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless
# sudo mv rtl8187.ko rtl8187.org
# sudo cp ~/rtl8187/rtl8187.ko
```
Finally we can test the module. So plug in the stick and enter the following command (in random order).
```
# sudo modprobe rtl8187
```
Check if your device is up and running.
```
# iwconfig
wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
If all went well, everything should work now. Now it's time to clean up the mess.
```
# cd ~/rtl8187
# make clean
# sudo rm /usr/src/linux-source-2.6.27 -r
```
If it's working and you want it to start automatically, just add it to /etc/modules


For troubleshooting modinfo is quite nice.
It should show:
```
# modinfo rtl8187
filename:       /lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     A1FCBC06E2195A653B7E975
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*
depends:        mac80211,eeprom_93cx6,cfg80211,usbcore
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586
```
Make especially sure your device is in it (v0DF6p0028d in this case)


FYI:
This device will be included in the 2.6.27-10 ubuntu version of the kernel. So I could have just downloaded it
from svn and used that one, or wait till that kernel came as an automatic update, but I prefer a stable 
kernel instead of a testing release and besides I wanted to know how to compile a single kernel module.

---

