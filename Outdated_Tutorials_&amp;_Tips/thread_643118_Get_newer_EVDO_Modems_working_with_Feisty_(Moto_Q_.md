---
title: "Get newer EVDO Modems working with Feisty (Moto Q specifically)"
date: 2007-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by bismark on 2007-12-17
So the cdc-acm.ko module in the default Feisty kernel does not support the Motorla Q and quite a few other newer devices, the module loads when a device is connected but gives the following output in syslog.

```
localhost kernel: [10862.541000] usb 5-6.3: new full speed USB device using ehci_hcd and address 11
localhost kernel: [10862.630000] usb 5-6.3: configuration #1 chosen from 1 choice
localhost kernel: [10862.671000] drivers/usb/class/cdc-acm.c: Zero length descriptor references
localhost kernel: [10862.671000]
localhost kernel: [10862.671000] cdc_acm: probe of 5-6.3:1.0 failed with error -22
localhost kernel: [10862.671000] usbcore: registered new interface driver cdc_acm
localhost kernel: [10862.671000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
```

I searched for a quick way to fix it but didn't find any one place on how to do it so I'm writing it up here.

Here are the steps I followed (credits at the end of the HowTo)

**Install the necessary tools:**
```
sudo apt-get install linux-kernel-devel fakeroot build-essential git-core
```

**Download your current kernel headers**
```
sudo apt-get install linux-headers-`uname -r`
```

**Download the gutsy kernel source**
```
cd /usr/src && sudo git clone git://kernel.ubuntu.com/ubuntu/ubuntu-gutsy.git ubuntu-gutsy
```

**Backup your original source files and kernel module**
```
sudo cp /usr/src/linux/drivers/usb/class/cdc-acm.c /usr/src/linux/drivers/usb/class/cdc-acm.c.orig
sudo cp /usr/src/linux/drivers/usb/class/cdc-acm.h /usr/src/linux/drivers/usb/class/cdc-acm.h.orig
sudo cp /usr/src/linux/drivers/usb/class/usblp.c /usr/src/linux/drivers/usb/class/usblp.c.orig
sudo cp /usr/src/linux/include/linux/usb/cdc.h /usr/src/linux/include/linux/usb/cdc.h.orig
sudo cp /lib/modules/`uname -r`/kernel/drivers/usb/class/cdc-acm.ko /lib/modules/`uname -r`/kernel/drivers/usb/class/cdc-acm.ko.orig
```

**Copy the new files from gutsy source**
```
sudo cp /usr/src/ubutu-gutsy/drivers/usb/class/cdc-acm.c /usr/src/linux/drivers/usb/class/cdc-acm.c
sudo cp /usr/src/ubuntu-gutsy/drivers/usb/class/cdc-acm.h /usr/src/linux/drivers/usb/class/cdc-acm.h
sudo cp /usr/src/ubuntu-gutsy/drivers/usb/class/usblp.c /usr/src/linux/drivers/usb/class/usblp.c
sudo cp /usr/src/ubuntu-gutsy/include/linux/usb/cdc.h /usr/src/linux/include/linux/usb/cdc.h
```

**Build the new module**
```
cd /usr/src/linux && sudo make M=/usr/src/linux/drivers/usb/class
```

**Copy the new module and update module dependencies**
```
sudo cp /usr/src/linux/drivers/usb/class/cdc-acm.ko /lib/modules/`uname -r`/kernel/drivers/usb/class/
sudo depmod -a
```

That should do it.  Now if you plug in your device after you've activated it's modem mode you should get something like the following:
```
localhost kernel: [10738.635000] usb 5-6.3: new full speed USB device using ehci_hcd and address 7
localhost kernel: [10738.723000] usb 5-6.3: configuration #1 chosen from 1 choice
localhost kernel: [10738.790000] cdc_acm 5-6.3:1.0: ttyACM0: USB ACM device
localhost kernel: [10738.792000] usbcore: registered new interface driver cdc_acm
localhost kernel: [10738.793000] /usr/src/linux/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
```

**Configure your new usb modem**
For configuring it to actually work I'll refer everyone over to the excellent howto:  [Qusers.com - Topic :: Tethering with Linux (USB & BT)]("http://www.qusers.com/forum/viewtopic.php?t=7941&view=next&sid=8f6a7831cca2c9da82e384d09df78889")

**Credits**
The steps taken to build the download the source and build the kernel module were taken from the following guides:
[KernelCustomBuild - Ubuntu Wiki]("https://wiki.ubuntu.com/KernelCustomBuild")
[KernelGitGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/KernelGitGuide")
[HOWTO Build a Linux kernel module out-of-tree - BeezNest]("http://glasnost.beeznest.org/articles/340")

**Disclaimers**
Standard responsibility disclaimer: I'm not responsible if you screw up your computer, always make backups.

Using your phone as a modem is only "allowed" if you have a tethering plan with your carrier.  Though you can use it without the plan you could get your account canceled.

---

### Post by vdelarenal on 2008-01-30
Hi, have you been able to sync your Moto Q with ubuntu?

---

### Post by MtnCoder on 2008-02-28
Hey...the "Qusers.com - Topic :: Tethering with Linux (USB & BT)" link referred to above is actually here:

[http://www.qusers.com/forum/viewtopic.php?t=11935](http://www.qusers.com/forum/viewtopic.php?t=11935)

Got my Q working on Gutsy. Thanks for the article!

---

### Post by riddlebox on 2008-08-18
Has anyone gotten this to work lately with hardy? I get this when I plug in my Moto Q

[  697.691461] usb 1-2: new full speed USB device using uhci_hcd and address 5
[  697.722323] usb 1-2: configuration #1 chosen from 1 choice
[  697.726431] ipaq 1-2:1.0: PocketPC PDA converter detected
[  697.728558] usb 1-2: PocketPC PDA converter now attached to ttyUSB0
[  706.511211] usb 1-2: USB disconnect, address 5
[  706.511942] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[  706.511979] ipaq 1-2:1.0: device disconnected
[  706.668387] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  706.772310] usb 1-2: configuration #1 chosen from 1 choice
[  707.111911] usbcore: registered new interface driver cdc_ether
[  707.116455] usb 1-2: bad CDC descriptors
[  707.116912] usbcore: registered new interface driver rndis_host

Also I cannot get the qusers.com forum links to come up. Can anyone tell me how to use this phone to tether out?

---

