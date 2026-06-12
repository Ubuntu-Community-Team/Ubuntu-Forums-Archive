---
title: "install wifi usb driver failed"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by lollol1973 on 2013-05-14
i bought a ProLink WN2001 wireless-N Nano USB Adapter and downloaded the driver file: RTL8188EUS_linux_v4.1.3_5938.20121130
after installed (sudo ./install.sh), still unable to detect the device. please help.

lsusb
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 07b8:8179 AboCom Systems Inc **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by lollol1973 on 2013-05-14
p/s: i using gnome 64bit BackTrack 5 r3

---

### Post by AndyOpie150 on 2013-05-14
I think Backtrack 5 r3 already has the ndiswrapper module set up if I'm not mistaken.
Put the driver in your home folder. If driver is in two folders pull secound folder out of the first one and delete first one. Rename the folder to just Drivers.
Does your driver folder have a LSTINDS.INF file? If yes, I can help.
Open up a command prompt and type in:
```
 
sudo ndiswrapper -i home/<your user name>/Drivers/LSTINDS.INF
sudo modeprobe ndiswrapper
sudo su
echo ndiswrapper >> /etc/modules
exit

```

If I'm mistaken and the ndiswrapper module is not already configured then you will need to open up the synaptic package manager and type in ndiswrapper in the search box. Whatever it already has listed you will not need to install.

List of packages to download and install in order of apperance:
ndiswrapper-common-_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb
libglade2-0_2.6.4-1ubuntu1_i386.deb
python-glade2_2.24.0-3_i386.deb
dkms_2.2.0.3-1ubuntu3_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb

Again: you will not need to download those already installed. Once the ndiswrapper-dkms is installed it will auto compile the ndiswrapper module.
After it compiles the module then run the code.

Note: You will only be able to use WEP security with the ndiswrapper module. Welcome to my world.

---

