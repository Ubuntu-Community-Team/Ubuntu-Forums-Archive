---
title: "HOWTO: Connect with Livebox using USB cable"
date: 2007-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by charnooh on 2007-09-06
Here's the way to install Livebox USB driver on ubuntu linux
Checked and working on Ubuntu Feisty Fawn 7.04 x86 with SAGEM livebox F@st 3202 USB

First you have to get the drivers, you should get three files:
[B]adirndis.inf
rndismpk.sys
usb8023k.sys[/B]

You can get them by exctracting them from you driver's .exe or .cab or find them in your **windows\system32\drivers** folder if you have them installed (if not install them on windows and do so :P)

please be aware that the .sys files may be named r**ndismp.sys usb8023.sys** so you'll have to add 'k' to the names

now get **ndiswrapper 1.4**7 here: (**[COLOR="DarkRed"]warning!!![/COLOR] don't use the package repository version, it's old and crappy!!!**)

> [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=515643](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=515643)

you'll have to get the dev tools for ubuntu to compile it. you'll need packages:
**gcc g++ make**
you can download them from the repo:

> sudo apt-get install gcc g++ make

or download them from **packages.ubuntu.com**

now you have to compile it. for it you have to extract the .tar.gz file (using file browser) to a dir, then enter this dir with the terminal and type:

> make
sudo make install

when your ndiswrapper is successfully installed type:
> 
ndiswrapper -v

and you should get
> 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

now go into the directory where your .inf and .sys files are in and install the driver
> 
sudo ndiswrapper -i adirndis.inf
sudo cp *.sys /etc/ndiswrapper/adirndis/
sudo ndiswrapper -m

if everything works fine, plug in your usb (if you haven't done that yet) and type
> 
ndiswrapper -l

and you should get
> 
adirndis : driver installed
         device (1110:6489) present

now time to install the kernel module
> 
sudo modprobe ndiswrapper

it shouldn't prompt, but you can see it installed by typing:
> 
dmesg|grep ndiswrapper

it should prompt
> 
[   72.612000] ndiswrapper version 1.47 loaded (smp=yes)
[   72.668000] usbcore: registered new interface driver ndiswrapper

and if you type
> 
lsmod|grep 'ndiswrapper'

you should get:
> 
ndiswrapper           188252  0 
usbcore               134280  3 ndiswrapper,uhci_hcd

but don't get happy yet :P it's not over.
now you have to load the driver:
> 
sudo -s -H
echo 1 > /sys/bus/usb/1-2/bConfigurationValue

now check it again, the '**dmesg|grep ndiswrapper**' should now prompt
> 
[   72.612000] ndiswrapper version 1.47 loaded (smp=yes)
[   72.668000] usbcore: registered new interface driver ndiswrapper
[ 1445.864000] ndiswrapper: driver adirndis (Analog Devices,08/23/2001,5.1.2600.0) loaded

but your device will not load automatically when connected. To fix that you have to create a file '**/etc/udev/rules.d/25-local.rules**'
> 
sudo gedit /etc/udev/rules.d/z25_local_rules

and paste the following:
> 
BUS==”usb”, SYSFS{idProduct}==”1110”, SYSFS{idVendor}==”6489”, \
PROGRAM="/bin/sh -c 'echo 1 > /sys/%p/device/bConfigurationValue'"

save and close. Note that **1110** and **6489** are the numbers shown by '**ndiswrapper -**l' here '**device (1110:6489) present**' so if it shows different numbers, it means that you own a different model of livebox and thus you should change the numbers of **idProduct** and **idVendor** here: '**SYSFS{idProduct}==”1110”, SYSFS{idVendor}==”6489”**'

now, if you run your **network-admin** (by typing '**sudo network admin**') you should see your device listed. DHCP doesn't seem to work, but if you write a valid IP address within the range (for default, i suppose **192.168.1.24** should be ok) it will work.

For this a big credit goes to **giri** of the **ndiswrapper** team

Have fun, love linux.

**Sos**

---

