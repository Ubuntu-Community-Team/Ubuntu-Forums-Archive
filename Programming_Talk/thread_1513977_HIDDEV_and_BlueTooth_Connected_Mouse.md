---
title: "HIDDEV and BlueTooth Connected Mouse"
date: 2010-06-20
forum: Programming Talk
---

### Post by roadkillbunny on 2010-06-20
Hi all,

I just bought myself the Logitech M555b BlueTooth mouse to use with my laptop when I travel. The basic functionality works out of the box on Ubuntu. However, some advanced features do not work.

For example, the mouse has a "hyper-scroll" mouse wheel. This wheel has two modes of scrolling: frictionless and slow. This feature is present in most of the Logitech mice. But it is quite painful for switching between those two modes on Linux. Someone has already written a tool called "[revoco]("http://goron.de/~froese/revoco/")" that makes it easier with the MX Revolution mouse. I have used this tool with my MX Revolution mouse that is connected to my desktop without any problems. My idea is now to try to port this tool to the M555b mouse. 

Here is the problem though. The revoco tool communicates with the mouse via the /dev/hiddevX (or /dev/usb/hiddevX) files. But I cannot find a /dev/hiddevX file for the M555b mouse. All I have are /dev/hidraw0 and /dev/input/mouse2 files

I know this from the following commands
```

kkrizka@sein:~$ dmesg | grep hid
[93926.928978] generic-bluetooth 0005:046D:B009.0001: input,hidraw0: BLUETOOTH HID v4.16 Mouse [Logitech Bluetooth Mouse M555b] on 00:1C:26:D8:DB:90

```

```

kkrizka@sein:~$ cat /proc/bus/input/devices
< trimmed other devices >
I: Bus=0005 Vendor=046d Product=b009 Version=0416
N: Name="Logitech Bluetooth Mouse M555b"
P: Phys=00:1C:26:D8:DB:90
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input11
U: Uniq=00:07:61:FB:93:12
H: Handlers=mouse2 event10 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

```

After a bit of search, it appears that I am missing the hiddev file because I connected the mouse directly via the BlueTooth inside my laptop without using a provided dongle (the M555b doesn't come with one, only the MX Revolution does).
[http://ubuntuforums.org/showpost.php?p=5396512&postcount=30](http://ubuntuforums.org/showpost.php?p=5396512&postcount=30)

Does anyone know how to create a /dev/hiddevX file for a moues connected via BlueTooth?

My understanding is that hiddev and hidraw are similar, but hidraw uses raw HID stream while hiddev parses them into a developer-friendly format.

---

### Post by yatohese on 2011-02-28
I encountered the same problem and am also looking for an answer?
Any progress? Any new information?

---

