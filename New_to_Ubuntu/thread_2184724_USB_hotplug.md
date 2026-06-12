---
title: "USB hotplug"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by saddamali111 on 2013-10-30
hi,


     I am new to the linux. I want to create a usb hotplug using udev rules. I have file called 65-automount-rules in /etc/udev/rules.d and i made changes like
```

ACTION=="add", KERNEL=="sda1", RUN+="/bin/somebinaryfile1"
ACTION=="remove",KERNEL=="sda1", RUN+="/bin/somebinaryfile2"

```

so when usb is plugged in i want to run a somebinaryfile1 and when usb in unplugged i want to run somebinaryfile2. is it possible to run a binary file with these changes???


thanks,
Ali

---

### Post by 7spawn on 2013-10-31
I've made new rule in /etc/udev/rules.d/42-usb-sync.rules with these entries:

```

ACTION=="add", ENV{ID_FS_UUID_ENC}=="C821-C90A", KERNEL=="sd[c-z][0-9]", NAME="usb-sync", RUN+="mkdir -p /mnt/%k"
ACTION=="add", ENV{ID_FS_UUID_ENC}=="C821-C90A",   KERNEL=="sd[c-z][0-9]", NAME="usb-sync", RUN+="mount -o uid=1000  /dev/%k /mnt/%k"
ACTION=="remove", ENV{ID_FS_UUID_ENC}=="C821-C90A", KERNEL=="sd[c-z][0-9]", RUN+="rmdir /mnt/%k"

```

Then executed
```
udevadm control --reload-rules
```

But it seems udev is ignoring this rule. It does not do anything, even creating directory.
I've tried to use serial number *ATTRS{serial}=="001478544887BC51C7BA0015"*, but it did not work.

Data for rule i've got from these commands:
```

blkid /dev/sdb1
udevadm info -q all -n /dev/sdbX

```

What am i doing wrong?
**I just need udev to identify my usb-drive with uuid and execute some script\command.**
I think this thread will help both of us [http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)

---

### Post by 7spawn on 2013-10-31
Well, by doing over 999 tries, i've got working example with checking serial number.
Checking uuid with *ENV{ID_FS_UUID}=="C821-C90A"* is not working.
God knows why udev working this, very strange way.
In example, when usb is plugged in then serial number checking works only with *ATTRS{serial}==""*, but not with *ENV{ID_SERIAL_SHORT}*==""
And other way, when usb in unplugged, then works only *ENV* variant.

Also i can execute only my, user's scripts. No any system command like echo or touch, with full path, also does not work.

```

ACTION=="add",    ENV{DEVTYPE}=="usb_device", ATTRS{serial}=="001478544887BC51C7BA0015", SUBSYSTEM=="usb", RUN+="/home/det/test"
ACTION=="remove", ENV{DEVTYPE}=="usb_device", ENV{ID_SERIAL_SHORT}=="001478544887BC51C7BA0015", SUBSYSTEM=="usb", RUN+="/home/det/test2"

```

Another example: while using ```
ENV{ID_MODEL_ID}=="1689"
``` with *ACTION=="add"* - script does not work. But it executed while usb-drive is unplugged. **Why?**

Parameters for ENV can be founded this way: 
```
udevadm monitor --env
```

[B]I am interesting, why udev is working so strange way?
I've looked so many english and russian sources about udev, and many peoples have problems with doing simple things.[/B]

---

