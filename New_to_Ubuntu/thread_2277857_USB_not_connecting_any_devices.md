---
title: "USB not connecting any devices"
date: 2015-05-12
forum: New to Ubuntu
---

### Post by Cheshire_Shroom on 2015-05-12
Hello, new to Ubuntu and linux. I am running 14.04 LTS on an Acer Aspire 5560 with no dual boot. I've been searching the forums for about a week to resovle this issue, but can't seem to figure it out. None of my USB devices are connecting. The ports are giving power, although they don't if a device isn't connected at start up.
My lsusb output is as follows:

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:b002 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 Thank you for the help!

---

### Post by leunam12 on 2015-05-12
Can you use your USB devices if you boot a live session (either from DVD or USB)? If you can then I would test the RAM for errors and the HDD for bad sectors and format and re-install to see if that solves the issue. If you can't connect USB devices on a live session then I don't know how to help you. I will let more experienced users jump in.

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-05-13
Some machines have BIOS options for USB ENABLE/DISABLE. You may check for your PC's BIOS. That might help you!

---

### Post by Cheshire_Shroom on 2015-05-13
I've just finished re-installing, and my BIOS has no configuration settings for USB. Same issue as before.

---

### Post by Vladlenin5000 on 2015-05-14
Acer Aspire 5560 has an AMD APU -> You absolutely need to install AMD proprietary driver. It's mainly for graphics but the APUs are a tightly integrated all-in-one (dirty cheap) solution.

---

### Post by Vladlenin5000 on 2015-05-14
The same goes for ANY Windows version prior to Windows 8 (or perhaps 8.1). 
Try a regular Windows 7 installation (not from the OEM disk, if any, or any other vendor recovery system because either way will most likely carry the required drivers) and you'll face the exact same issue until you install Catalyst.

---

### Post by Cheshire_Shroom on 2015-05-14
Okay, ive started down that rabbit hole to install the amd drivers... and now stuck at the instructions here...
**Installation using RPM**
    For each of these steps you will have to be logged on as the root user.
    
[LIST=1]
[*]       cd to the directory containing the AMD Driver rpm package

[*]       Issue the following command:
        [INDENT]         rpm -Uh --force <package_name>.rpm       [/INDENT]        Note any error messages that may occur while installing (see below)

[*]       Run the fglrxconfig utility to configure the driver

[LIST]
[*]Answer the questions as prompted
[*]When asked to generate an XF86Config file, answer y
[/LIST]
     
[*]       Restart and log into X-Windows

[*]       Run fglrxinfo to verify the driver is installed correctly
[/LIST]
    If fglrxinfo indicates that software rendering is  being used, then you may want to repeat the steps listed above, while  paying careful attention to the following:
    
[LIST]
[*]Any error messages during install (see below)
[*]All answers given during fglrxconfig
[/LIST]
    

all of this means nothing to me, im having to google every single thing, each answer gives more questions....

---

### Post by cariboo on 2015-05-14
I think you best climb out of that rabbit hole, as you are heading for a lot of grief. The firmware you are looking for is in the repositories. When I'm not sure what the name of the package is that I'm looking for I always search [http://packages.ubuntu.com/](http://packages.ubuntu.com/). In this case I did a search for AMD firmware.

[http://packages.ubuntu.com/search?keywords=amd64+&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=amd64+&searchon=names&suite=trusty&section=all)

To install it all you need to do is open a terminal and type:

```
sudo apt-get install amd64-microcode
```

---

### Post by Vladlenin5000 on 2015-05-14
Actually, *fglrx *is more important. The microcode (AMD/Intel) is a new thing, debuted in vivid if I'm not mistaken. I'm pretty much clueless about what it does or doesn't but installing it anyway, along with the usual fglrx driver.

Both can be easily installed in System Settings > Software & Updates. Here's an example for E1-6010 (last year's entry-level APU; current offerings start with R3 graphics) (attachment in Portuguese, I'm sure most of you understand).
Obs.: Both *fglrx* and *fglrx-updates *work as expected, no noticeable improvement with the newer (-updates) though.
The test machine of the screenshot is a HP 255 G3 but before you start saying "oh, that model is Ubuntu Certified", this was bought in a regular store in Spain with Windows 8.1. 
Installing Ubuntu alone (UEFI or legacy), Windows 8.1 alone (UEFI) or dual boot with Windows 8.1/10 (UEFI) or Windows 7* (legacy) couldn't be easier.

* Really slow and non-working USB ports (2.0 and 3.0) without AMD drivers


Why is this so important?
AMD APUs are SoC (System on Chip) -> CPU, GPU and northbridge/soutbridge chipset mashed together in a single chip. Not much different from the ubiquitous ARM (smartphones, tablets, smartTVs, etc.) except it's x86_64. The proprietary AMD drivers for Linux - *fglrx* - provides both graphics and chipset drivers.

---

### Post by Cheshire_Shroom on 2015-05-16
I have installed the AMD microcode, and when I click the radio button for fglrx or fglrx-updates and hit apply, it jumps back to the default. I reboot after every step, still no USB function.

---

### Post by Geoffrey_Arndt on 2015-05-16
It might help if you can attach a thumbnail as Vlad did in post#9 . . . just to confirm you're in the right place and have the right pre-selections.   Also,  as I don't have the ATI graphics,, perhaps someone can post the terminal code to install the fglrx driver as that is the core requirement for your system.   Also, the Terminal often provides specific error codes if install fails.

---

### Post by Cheshire_Shroom on 2015-05-16
screenshot attached. Everytime I click the radio button for either flgrx option and hit "apply changes" there is a load bar then switches back to the first radio button. Since doing these steps, my computer no longer has audio, either through the speakers, or the headphones.

---

### Post by Vladlenin5000 on 2015-05-17
You can try this instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Installing_via_the_command_line](https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Installing_via_the_command_line)
It may not work but at least we'll have some error message.

---

### Post by daktaklakpak5576 on 2015-05-18
> **Cheshire_Shroom said:**
> I have installed the AMD microcode, and when I click the radio button for fglrx or fglrx-updates and hit apply, it jumps back to the default. I reboot after every step, still no USB function.

sorry for your troubles, but you're barking up the wrong tree, fglrx has absolutely nothing to do with usb, fglrx is for AMD APUs or Radeon cards. I just went through three ubuntu installs and even went so far as to compile a custom kernel trying to get usb working right in ubuntu.

```
nyx Downloads # lspci | grep USB
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)

```

Thats my usb devices, yours are probably similar. Do 'sudo lspci' in ubuntu. USB is built into the chipset, whether it's soldered on the motherboard or built into the CPU package really doesn't matter. Wish I could help you get it working but I gave up on it and formatted my ubuntu install, and I've used linux (not ubuntu) for like 14 years. I wish u luck.

---

### Post by Vladlenin5000 on 2015-05-18
Apparently you haven't red the thread as a whole, otherwise you wouldn't be saying > fglrx has absolutely nothing to do with usb, fglrx is for AMD APUs or Radeon cards

You clearly don't know what AMD APUs are. Please read my previous posts where I explained it. Then - hopefully - you'll understand that an APU is everything and there's no "chipset".
The point being USB ports in an AMD APU based system DON'T work OOTB in most Linux distros (and Windows 7) without the AMD drivers. This is way different from your old system.

PS - I just went trough DOZENS of installs in machines running 2014 editions of several APUs and it always been the same. And it certainly isn't because I'm running Linux longer than you.

---

### Post by daktaklakpak5576 on 2015-05-18
> **Vladlenin5000 said:**
> Apparently you haven't red the thread as a whole, otherwise you wouldn't be saying 

You clearly don't know what AMD APUs are. Please read my previous posts where I explained it. Then - hopefully - you'll understand that an APU is everything and there's no "chipset".
The point being USB ports in an AMD APU based system DON'T work OOTB in most Linux distros (and Windows 7) without the AMD drivers. This is way different from your old system.

PS - I just went trough DOZENS of installs in machines running 2014 editions of several APUs and it always been the same. And it certainly isn't because I'm running Linux longer than you.

Sorry but you're wrong on this. Fglrx/AMD Catalyst is just a graphics driver it has absolutely nothing to do with usb. Your favorite distribution may bundle the microcode for AMD processors in with fglrx but that would be the extent of the association. Microcode is probably a good thing to have but it should be able to be installed without fglrx, and that looks like exactly what cariboo suggested. 


An APU isn't "everything" what used to be the northbridge is now fabbed as part of the APU, and what used to be the southbrige was renamed the "Fusion Controller Hub." USB hardware is on the FCH, not the APU.
[IMG]http://notebookschematic.com/wp-content/uploads/2013/01/VAW03_LA-9103P.png[/IMG]

USB support probably does work OOTB in most linux distros besides ubuntu, or at least it should because the support is in the kernel. Whether it works or not in Windows 7 is completely irrelevant.

Shroom you should be able to use dmesg in a terminal to see what's going on with your usb devices. Unplug and plug them back in and do dmesg again and see what it shows.

---

### Post by Cheshire_Shroom on 2015-05-18
Vlad:
Error at step 1 of your link: cp: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory

daktak: lsusb is as follows: Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:b002 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 which is the same as when I started.

all: stop fighting ><

not sure if relevant, but this model of acer laptop has a dual graphics option. it had been an initial barrier to the ubuntu install, not sure how I got around it though.

---

### Post by Cheshire_Shroom on 2015-05-18
Also, the dmseg output was long...

---

### Post by Vladlenin5000 on 2015-05-19
Hybrid graphics with AMD involved and Ubuntu has been a constant pain you know where or so I've been tool... I avoid such hardware like the plague.
Knowing that, one more reason for the AMD drivers. Now, there's a [bug with 14.04 and fglrx]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491") I haven't mentioned before because somehow I was under the impression you were running 15.04.

```
sudo apt-get install xserver-xorg-core
sudo apt-get install libcheese*
```

Then you'll be able to install it.

---

### Post by daktaklakpak5576 on 2015-05-19
> **Cheshire_Shroom said:**
> Also, the dmseg output was long...

yes it is, just pay attention to the usb stuff at the bottom, or

```
dmesg | grep usb
```

If you still have other stuff plugged in your lsusb is not showing much besides hubs.. except for Alcor Micro. Is that some kind of built in card reader? Does it work?

You may or may not want fglrx anyway, up to you.

---

### Post by Cheshire_Shroom on 2015-05-27
Vlad, output from attempt to install xserver-xorg-core. I tried to manually download and install some of the packages this error said were missing, but the first two told me were already installed and updated. tried libclutter-gtk, and libcheese7. both were installed.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

Side note: .... although this STILL isn't working... I feel like I'm learning a lot about ubuntu by it just not working lol this is my only PC at the moment, I really want to get ubuntu to work (especially that it formatted the disk and reverting to windows would involve finding a copy of windows 7), IS this even possible with AMD hybrid graphics?

---

### Post by Cheshire_Shroom on 2015-05-27
daktak, yes it has a built in card reader, not sure if functions, I will try to troubleshoot, although it's function is not critical.

output from dmesg | grep usb

```
[    0.164318] usbcore: registered new interface driver usbfs
[    0.164318] usbcore: registered new interface driver hub
[    0.164318] usbcore: registered new device driver usb
[    0.616268] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.616271] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.616273] usb usb1: Product: EHCI Host Controller
[    0.616274] usb usb1: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    0.616276] usb usb1: SerialNumber: 0000:00:12.2
[    0.628365] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.628368] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.628370] usb usb2: Product: EHCI Host Controller
[    0.628372] usb usb2: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    0.628373] usb usb2: SerialNumber: 0000:00:13.2
[    0.640366] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.640369] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.640371] usb usb3: Product: EHCI Host Controller
[    0.640373] usb usb3: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    0.640374] usb usb3: SerialNumber: 0000:00:16.2
[    0.700337] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.700343] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.700345] usb usb4: Product: OHCI PCI host controller
[    0.700347] usb usb4: Manufacturer: Linux 3.16.0-38-generic ohci_hcd
[    0.700348] usb usb4: SerialNumber: 0000:00:12.0
[    0.760337] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.760342] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.760344] usb usb5: Product: OHCI PCI host controller
[    0.760346] usb usb5: Manufacturer: Linux 3.16.0-38-generic ohci_hcd
[    0.760348] usb usb5: SerialNumber: 0000:00:13.0
[    0.820336] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.820341] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.820343] usb usb6: Product: OHCI PCI host controller
[    0.820345] usb usb6: Manufacturer: Linux 3.16.0-38-generic ohci_hcd
[    0.820346] usb usb6: SerialNumber: 0000:00:16.0
[    0.940116] usb 2-3: new high-speed USB device number 2 using ehci-pci
[    1.859826] usb 2-3: New USB device found, idVendor=058f, idProduct=b002
[    1.859833] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.859837] usb 2-3: Product: 1.3M HD WebCam
[    1.859839] usb 2-3: Manufacturer: AABC1087X
[   14.710684] input: 1.3M HD WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input3
[   14.710949] usbcore: registered new interface driver uvcvideo


```

---

