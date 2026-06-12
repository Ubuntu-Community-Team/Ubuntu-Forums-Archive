---
title: "How to mount USB device based on ID"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by vangelists on 2012-09-07
Hello,

I have a USB flash drive that won't mount and won't show up at "ls -l /dev/sd*". However, I am able to see it using the command "lsusb".

Is it possible to mount it just by knowing the ID of the device lsusb gives?

P.S.: I'm not able to see the flash drive anywhere else, e.g. in GParted.

Thanks, in advance!

---

### Post by Bashing-om on 2012-09-07
vangelists ;

   Hi ! Welcome to the forum.

Background stuff: The device should "just work" Ubuntu should recognize the usb device upon insertion.
Ok so why is it not ?

1. Is there a entry in the media directory with the device inserted?
2. What file system is the device formatted to?
3. Does the device work in any other computer, if so, what operating system?
4. Is your usb flash drive usb 3 // inserted in a usb 2 port ?
Be advised ubuntu is very smart and will work with Lots of file system types / the default/preferred for linux only. is ext4 / .
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by vangelists on 2012-09-07
To be accurate, it's not a regular USB, but a USB dongle. It's a key for a professional software I use in Windows. Couple days ago, while cleaning my computer, I accidentally broke it --still works, but I'm afraid it's subject of time for it to fail completely. The company of the software won't replace it unless I pay $200... So, I just want to copy it to another USB drive in order to use it.

I have to notice that the software is bought and absolutely legal, I'm not trying to make an illegal copy of it, I just work with it since 2004 and need it for my job.

Consequently, I have no idea about what file system it is formatted to and my only hopes are now on Linux, due to their wide compatibility...

---

### Post by Epodx64 on 2012-09-07
Does it show up anywhere like /dev/sdb just unable to mount? If that's the case you could try something like "dd if=/dev/sdb@@@ of=/dev/sdb2!!!" 

/dev/sdb@@@ would be your broken device /dev/sdwhatever
and /dev/sdb2!!! would be a new usb device with enough space to copy your files (i'd format the new device as Fat32) It might work. Also your device could also be "locked" if it wasn't properly unmounted from the last computer it was on. i.e. if you just pulled it out without "safely ejecting" it. If that's the case try to use it on the last computer it was used with and properly eject it and it will unlock it.

---

### Post by steeldriver on 2012-09-07
Are you sure it's even a drive as such? it could be almost any hardware

You can probably find a little bit more about the device using udevadm - I'm only just taking baby steps with udevadm myself but I think the syntax should be something like

 ```
udevadm info --query=all --name=/dev/bus/usb/005/002
```or the short form

```
 udevadm info -q all -n /dev/bus/usb/005/002
```where obviously you should replace the last 2 numbers with the 'Bus' and 'Device' numbers for your device, from lsusb

If there's a udev rule that is recognizing it as a block device then I think there would be DEVLINKS entry telling you the /dev/whatever symlink

---

### Post by vangelists on 2012-09-07
> **Epodx64 said:**
> Does it show up anywhere like /dev/sdb just unable to mount?

As I said in my first message, "won't show up at "ls -l /dev/sd*", so I think this answers your question. If I'm wrong, correct me. I'm a newbie in Linux.

> **Epodx64 said:**
> Also your device could also be "locked" if it wasn't properly unmounted from the last computer it was on. i.e. if you just pulled it out without "safely ejecting" it. If that's the case try to use it on the last computer it was used with and properly eject it and it will unlock it.

I don't have access to that computer right now, but can this be possible? If yes, should I "safely eject" it? However, last time I took it off was after turning off the computer by pressing "Shutdown" in Windows (XP).

---

### Post by vangelists on 2012-09-07
> **steeldriver said:**
> Are you sure it's even a drive as such? it could be almost any hardware

Using the command you gave me:

```
udevadm info -q all -n /dev/bus/usb/005/006
```...the output is this:

```
P: /devices/pci0000:00/0000:00:1d.0/usb5/5-1
N: bus/usb/005/006
S: char/189:517
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb5/5-1
E: MAJOR=189
E: MINOR=517
E: DEVNAME=/dev/bus/usb/005/006
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=925/2345/100
E: TYPE=0/0/0
E: BUSNUM=005
E: DEVNUM=006
E: SUBSYSTEM=usb
E: ID_VENDOR=MONARCH
E: ID_VENDOR_ENC=MONARCH\x20\x20\x20\x20\x20\x20
E: ID_VENDOR_ID=0925
E: ID_MODEL=USB_Security_Dongle&#784;00000
E: ID_MODEL_ENC=USB\x20Security\x20Dongle&#784;00000
E: ID_MODEL_ID=2345
E: ID_REVISION=0100
E: ID_SERIAL=MONARCH_USB_Security_Dongle&#784;00000_000001&#808;
E: ID_SERIAL_SHORT=000001&#808;
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030100:
E: DEVLINKS=/dev/char/189:517

```As I understand, it is a USB drive.

---

