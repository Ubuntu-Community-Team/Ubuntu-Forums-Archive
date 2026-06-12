---
title: "issue with smart card reader ACS ACR122U"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by daniel103 on 2014-01-20
hi all,

I'm Daniel and a little beginner in Linux stuff.

I would like to ask you for help.

Today, I've installed a new VM with the OS ubuntu 12.04.3-desktop-i386.

I have a problem with my USB smart card reader/writer, which I'm trying to install there.

It gives me this errors, when I run the following command, any idea how to fix this? thanks:

root@user-virtual-machine:/home/user# **pcscd -a -d -f **
00000000 pcscdaemon.c:231:main() pcscd set to foreground with debug send to stdout
00000160 configfile.l:245:DBGetReaderListDir() Parsing conf directory: /etc/reader.conf.d
00000116 configfile.l:287:DBGetReaderList() Parsing conf file: /etc/reader.conf.d/libccidtwin
00000142 pcscdaemon.c:556:main() pcsc-lite 1.7.4 daemon ready.
00001178 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0001, path: /dev/bus/usb/002/001
00000576 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0001, path: /dev/bus/usb/002/001
00000183 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0E0F, PID: 0x0003, path: /dev/bus/usb/002/002
00000179 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0E0F, PID: 0x0003, path: /dev/bus/usb/002/002
00000176 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0001, path: /dev/bus/usb/002/001
00000179 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0E0F, PID: 0x0002, path: /dev/bus/usb/002/003
00000614 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x072F, PID: 0x2200, path: /dev/bus/usb/002/004
00000095 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x072F, PID: 0x2200, path: /dev/bus/usb/002/004
00000068 hotplug_libudev.c:309:HPAddDevice() Adding USB device: ACS ACR122U PICC Interface
00000084 readerfactory.c:934:RFInitializeReader() Attempting startup of ACS ACR122U PICC Interface 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so
00000213 readerfactory.c:824:RFBindFunctions() Loading IFD Handler 3.0
00000095 ifdhandler.c:1781:init_driver() Driver version: 1.4.5
00000353 ifdhandler.c:1798:init_driver() LogLevel: 0x0003
00000072 ifdhandler.c:1809:init_driver() DriverOptions: 0x0000
00000117 ifdhandler.c:80:IFDHCreateChannelByName() lun: 0, device: usb:072f/2200:libudev:0:/dev/bus/usb/002/004
00000312 ccid_usb.c:245:OpenUSBByName() ifdManufacturerString: Ludovic Rousseau (ludovic.rousseau@free.fr)
[B]00000071 ccid_usb.c:246:OpenUSBByName() ifdProductString: Generic CCID driver
00000062 ccid_usb.c:247:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
00131495 ccid_usb.c:506:OpenUSBByName() Found Vendor/Product: 072F/2200 (ACS ACR122U PICC Interface)
00000173 ccid_usb.c:508:OpenUSBByName() Using USB bus/device: 2/4
00004160 ccid_usb.c:957:get_data_rates() IFD does not support GET_DATA_RATES request: 0
05365488 ccid_usb.c:638:WriteUSB() write failed (2/4): -7 Success
05014544 ccid_usb.c:638:WriteUSB() write failed (2/4): -7 Success
05039759 ccid_usb.c:638:WriteUSB() write failed (2/4): -7 Success
00000029 ifdhandler.c:135:IFDHCreateChannelByName() failed
00000069 readerfactory.c:965:RFInitializeReader() Open Port 0x200000 Failed (usb:072f/2200:libudev:0:/dev/bus/usb/002/004)
00000005 readerfactory.c:275:RFAddReader() ACS ACR122U PICC Interface init failed.
00000005 readerfactory.c:985:RFUnInitializeReader() Attempting shutdown of ACS ACR122U PICC Interface 00 00.
00000004 readerfactory.c:861:RFUnloadReader() Unloading reader driver.
00000048 hotplug_libudev.c:377:HPAddDevice() Failed adding USB device: ACS ACR122U PICC Interface[/B]
00000165 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0E0F, PID: 0x0002, path: /dev/bus/usb/002/003
00000174 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001

---

