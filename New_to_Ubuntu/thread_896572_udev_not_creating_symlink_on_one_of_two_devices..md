---
title: "udev not creating symlink on one of two devices."
date: 2008-08-21
forum: New to Ubuntu
---

### Post by schmick on 2008-08-21
Hi!
_I'll try to write this as udev basic usage tutorial, hopefully someone can point out what is going on with my problem also._

I got 2 v4l (video for linux) devices, a webcam and a capture card, so sometimes at boot, _/dev/video0_ and _/dev/video1_ get swapped depending on what is detected first. OK, that is somehow known.

Proposed solution: use udev rules to create a symlink that can be static to parameters of each device such as /dev/webcam and /dev/capture. Sounds neat ehh?.

Well, following instructions, I looked up a unique parameter for each device using

```
udevinfo -a -p $(udevinfo -q path -n /dev/video0)
udevinfo -a -p $(udevinfo -q path -n /dev/video1)

[sample output]
  looking at device '/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:0"
    ATTR{name}=="saa7130_0_ video _Encore ENLTV_"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:00.0':
    KERNELS=="0000:01:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="saa7134"
    ATTRS{vendor}=="0x1131"
    ATTRS{device}=="0x7130"
[so on.......]

```
OK, ATTRS{vendor} and ATTRS{device} sounds quite unique, ATTR{name} looks good also.
So I went out to write my rules.
```
sudo gedit /etc/udev/rules.d/95-perso.rules
```
95 is so it gets executed at last. Udev parses file in ascending order.

```
ATTR{name}=="GSPCA USB Camera", SYMLINK+="video_webcam"
ATTRS{device}=="0x7130", ATTRS{vendor}=="0x1131", SYMLINK+="capture"
```
Save, close and let's test it.

```

sudo udevtest /class/video4linux/video1

[bla bla bla...]
parse_file: reading '/etc/udev/rules.d/95-perso.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-udev-late.rules' as rules file
import_uevent_var: import into environment: 'MAJOR=81'
import_uevent_var: import into environment: 'MINOR=1'
udevtest: looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1' from subsystem 'video4linux'
udev_rules_get_name: add symlink 'video_webcam'
udev_rules_get_name: no node name set, will use kernel name 'video1'
udev_device_event: device '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1' already in database, cleanup
udev_node_add: creating device node '/dev/video1', major=81, minor=1, mode=0660, uid=0, gid=44
udev_node_update_symlinks: update symlink 'video_webcam' of '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/video_webcam'
update_link: found 1 devices with name 'video_webcam'
update_link: found '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1' for 'video_webcam'
update_link: compare (our own) priority of '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1' 0 >= 0
update_link: 'video_webcam' with target 'video1' has the highest priority 0, create it
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'

```
Webcam ok.. look:
[INDENT]update_link: found 1 devices with name 'video_webcam'
update_link: found '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1' for 'video_webcam'
update_link: compare (our own) priority of '/devices/pci0000:00/0000:00:1d.0/usb1/1-2/video4linux/video1' 0 >= 0
update_link: 'video_webcam' with target 'video1' has the highest priority 0, create it[/INDENT]
Neat!

Let's see the capture card.

```
sudo udevtest /class/video4linux/video0

[bla bla bla.....]
parse_file: reading '/etc/udev/rules.d/95-perso.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-udev-late.rules' as rules file
import_uevent_var: import into environment: 'MAJOR=81'
import_uevent_var: import into environment: 'MINOR=0'
udevtest: looking at device '/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/video4linux/video0' from subsystem 'video4linux'
udev_rules_get_name: add symlink 'capture'
udev_rules_get_name: no node name set, will use kernel name 'video0'
udev_db_get_device: found a symlink as db file
udev_device_event: device '/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/video4linux/video0' already in database, cleanup
udev_node_add: creating device node '/dev/video0', major=81, minor=0, mode=0660, uid=0, gid=44
udev_node_update_symlinks: update symlink 'capture' of '/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/video4linux/video0'
udev_db_get_devices_by_name: no index directory '/dev/.udev/names/capture': No such file or directory
update_link: found -1 devices with name 'capture'
update_link: no reference left, remove 'capture'
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'

```

What?!?
[INDENT]udev_rules_get_name: add symlink 'capture'
.....
udev_db_get_device: found a symlink as db file  <---me no get it.
.....
udev_db_get_devices_by_name: no index directory '/dev/.udev/names/capture': No such file or directory
update_link: found -1 devices with name 'capture'
**update_link: no reference left, remove 'capture'**[/INDENT]

hmmmmm.. what was different this time?

Any idea ppl?

---

### Post by lucho64 on 2008-09-02
I've found (the hard way) that udev seems happier when you use one of the top descriptors in your rule. By that I mean that you should probably add say the kernel tag so that you rules look like:
```

ATTR{name}=="GSPCA USB Camera", SYMLINK+="video_webcam"
KERNEL=="video0", ATTRS{device}=="0x7130", ATTRS{vendor}=="0x1131", SYMLINK+="capture"

```
I think it makes sense, because you want a link to the video4linux device, not to the raw pci device.

---

### Post by schmick on 2008-09-22
hmmm... no can't do that.
The problem is the swapping of video0 and video1, so using the kernel name won't help.
It'll fail if it get's assigned video1.
I see Udev rules match the device, but it fails to create the link.

---

