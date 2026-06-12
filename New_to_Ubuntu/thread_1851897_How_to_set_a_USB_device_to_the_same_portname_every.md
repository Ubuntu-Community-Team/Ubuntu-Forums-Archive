---
title: "How to set a USB device to the same port/name every time"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by inger on 2011-09-29
:)Hi,
 
I want to connect a device to the same port (or name) every time I plug it in. How can I do it?
I have tried to make a file "10-udev.rules" in /etc/udev/rules.d like this:
```
KERNELS=="usb 3-1", DRIVERSD=="ftdi_sio", SYMLINK+="nameOfDevice", MODE="0666"
```
 
When the usb-device is connected, I got this answer from **dmesg | grep tty**:
```
[403.015383] usb 3-1: FTDI USB Serial Device Converter now connected to ttyUSB0
```
 
The device is connected to different USBs when I disconnect and connect it again.:-( I want to use this converter in a program, and I need to know how to connect this converter.

---

### Post by HermanAB on 2011-09-29
Simple - Give the volume a label.

---

### Post by inger on 2011-09-29
How can I give it a label?
I checked e2label and tune2fs but they are only for hard disks, I think. I have a controller that sends signals to the PC while alarms occures.
How to give it a label, and how to use it?

---

### Post by matt_symes on 2011-09-29
Hi

This is a USB to serial device ? What device exactly are you trying to create a symlink for ?

Have a look at 

```
udevadm info <options>
```

to get extra information about the device and add that info to your udev rules.

Kind regards

---

### Post by inger on 2011-09-29
The device is now attached to ttyUSB0. The result from the udevadm info is following:
 
```
looking at device '/devices/pci0000:00/0000:00:06.0/usb2/2-2/2-2:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""
  looking at parent device '/devices/pci0000:00/0000:00:06.0/usb2/2-2/2-2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ftdi_sio"
    ATTRS{latency_timer}=="1"
    ATTRS{port_number}=="0"
  looking at parent device '/devices/pci0000:00/0000:00:06.0/usb2/2-2/2-2:1.0':
    KERNELS=="2-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{interface}=="TTL232R"
  looking at parent device '/devices/pci0000:00/0000:00:06.0/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 90mA"
    ATTRS{urbnum}=="16"
    ATTRS{idVendor}=="0403"
    ATTRS{idProduct}=="6001"
    ATTRS{bcdDevice}=="0600"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="11"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="FTDI"
    ATTRS{product}=="TTL232R"
    ATTRS{serial}=="FTF0GJJV"
  looking at parent device '/devices/pci0000:00/0000:00:06.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="311"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.38-11-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:06.0"
    ATTRS{authorized_default}=="1"

``` 
 
Which of them is important?

---

### Post by ninjaaron on 2011-09-29
You can change device lables with the program GParted, available in the software center.

From there, you ought to be able to specify rules for mounting in /etc/fstab.  I'm not exacty sure about getting it to the same port ever time, but it will mount with the lable if it has one.

Each disk (or partition) also has a specific  UUID until it is reformatted, and you can specify mounting rules based on that.

to find out the the UUIDs for all of your mounted devices, run this command:

```
sudo blkid
```

---

### Post by inger on 2011-09-29
YES!
Thanks for your help!:)
 
I got help from you and from [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221).
 
Now I got it to work!
I wrote a file 10-udev.rules located in /etc/udev/rules.d. This file contains the most specific items:
```
KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", NAME="flexiblink", MODE="0660"

```
 
thanks!:)

---

### Post by dFlyer on 2011-09-29
> **inger said:**
> How can I give it a label?
I checked e2label and tune2fs but they are only for hard disks, I think. I have a controller that sends signals to the PC while alarms occures.
How to give it a label, and how to use it?

Have you tried disk utility?

---

### Post by matt_symes on 2011-09-29
Hi

> **dFlyer said:**
> Have you tried disk utility?

> **yucww210 said:**
> That's what i think too .:D   

I don't think it was a block device but a character device. A usb to serial converter. You can't set volume labels on these devices as they are not volume devices. I have used these devices myself. This is why i suggested a udev rule based on other values.

Otherwise, for volume devices, your advice is spot on.

@inger; you're welcome.

Kind regards

---

