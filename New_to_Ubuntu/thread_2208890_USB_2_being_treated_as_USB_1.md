---
title: "USB 2 being treated as USB 1?"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by Zavation on 2014-03-02
Hi All,

I have a Blue Yeti Microphone and I seem to be having problems when connecting it to my Ubuntu machine. In previous Ubuntu install's I havnt had this issue.

When I plug in my Blue Yeti, I go to sound and it shows as "Microphone 1.1 root hub". Where as in the past its just shown as Blue Yeti, no problem.

When I did: dmesg | tail - It came up with the following results.

```
[ 6002.525618] usb 5-2: new full-speed USB device number 4 using ohci-pci
[ 6002.701597] usb 5-2: New USB device found, idVendor=b58e, idProduct=9e84
[ 6002.701604] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 6002.701609] usb 5-2: Product: Yeti Stereo Microphone
[ 6002.701613] usb 5-2: Manufacturer: Blue Microphones
[ 6002.782258] 3:3:1: cannot get freq at ep 0x82

```

Any suggestions on why it is not showing the full name "Blue Yeti" or why it is not showing the correct port? Here is a screen shot of the sound window, and the terminal showing the output: [http://i.imgur.com/ykd3CwT.png](http://i.imgur.com/ykd3CwT.png)

Thanks, any suggestions would be greatly appreciated!

---

### Post by varunendra on 2014-03-03
> **Zavation said:**
> ```
[ 6002.525618] usb 5-2: new full-speed USB device number 4 **using ohci-pci**

```
It maybe due to miscommunication between the hub and the device, or maybe the other ports were already occupied?

What is the output of -
```
lsusb
```
when it gets detected as a USB 1.1 device? Same across reboots with even different ports?

---

### Post by Vladlenin5000 on 2014-03-03
USB Microphones as well as all the other generic USB audio devices usually don't require USB2.0.
What makes you think it was treated differently, as USB2.0 device, before? It could be the case that now it's more precise in the description where before it used a generic name.

---

### Post by Zavation on 2014-03-03
I get the following when running lsusb:

```
josh@Maelstrom:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 005 Device 006: ID b58e:9e84  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And I'm having issues when trying to get applications to communicate with my Blue Yeti. For example, if I go into Kazam or audacity the Microphone is not listed. Like I said before, normally it just gets listed as Blue Yeti Microphone.

There was a review/guide on OMGUbuntu that shows what It should be like:
[http://www.omgubuntu.co.uk/2011/12/how-to-set-up-blue-yeti-mic-in-ubuntu](http://www.omgubuntu.co.uk/2011/12/how-to-set-up-blue-yeti-mic-in-ubuntu)

I don't really care about the name, its that I can't really use it in applications.

---

### Post by Vladlenin5000 on 2014-03-03
According to bluemic.com the requirements are:
*USB 1.1/2.0; 64 MB RAM (minimum)*
 therefore the device is a USB1.1 device, as expected. This is unrelated and has no bearing with the new problem. Apparently there was a regression at some point in the kernel update - mentioned here: [https://bbs.archlinux.org/viewtopic.php?id=158715](https://bbs.archlinux.org/viewtopic.php?id=158715) - and that's why it isn't no longer supported out-of-the-box, nothing to do with now being mentioned as USB1.1. Hence, the thread's subject is quite misleading.

Your microphone is this one: ```
Bus 005 Device 006: ID b58e:9e84
```
[http://usb-ids.gowdy.us/read/UD/b58e/9e84](http://usb-ids.gowdy.us/read/UD/b58e/9e84)

I hope there's an easy solution.

---

