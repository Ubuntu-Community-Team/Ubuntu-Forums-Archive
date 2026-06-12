---
title: "How to :FULL NTFS READ/WRITE with ntfs-3g driver"
date: 2006-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by wedderburn on 2006-07-16
ok first make sure you have you kernel headers installed for you kernel

we're gonna need the latest version of fuse [http://sourceforge.net/project/showf...kage_id=132802](http://sourceforge.net/project/showf...kage_id=132802)
extracted the files to my desktop

removed the old version of fuse via synaptic
```
sudo apt-get remove libfuse2
sudo apt-get remove libfuse-dev 
```

terminal

```
cd ~/Desktop/fuse-2.3.3
./configure --enable-kernel-module
make
sudo make install
```

then i did the ntfs stuff

extract that to my desktop
```
cd ~/Desktop/ntfs-3g-20070714-BETA
./configure
make
sudo make install
```

and its all compiled well enough so we can test it
```
sudo ntfs-3g /dev/hda1 /media/windows1

```
and if it worked you should be able to browse it with 
```
sudo nautilus
```

now we need to load the module at start up
```
sudo gedit /ect/modules
```
add "fuse" to the list

now we have to edit the fstab
```
sudo gedit /etc/fstab 
```
find the line that says ```

/dev/hda1 /media/windows1  ntfs    nls=utf8,umask=0222 0       0
```
replace the part after /media/windows1 with this 
```
/dev/hda1 /media/windows1 ntfs-3g silent,umask=0,locale=hu_HU.utf8 0 0
```

---

### Post by haani on 2006-07-16
the link for downloadin fuse drivers doesnt work!

**EDIT:** heres the workin link!

[http://sourceforge.net/project/showfiles.php?group_id=121684&package_id=132802]("http://sourceforge.net/project/showfiles.php?group_id=121684&package_id=132802")

---

### Post by domino on 2006-07-16
Thanks for the how-to. i asked this at the other forum, but since I'm running dapper, might as well ask here.

How does one cleanly automount external drives? udev can't make up it's mind and sometimes mounts the drive as sda1 or sdb1.

---

### Post by dlai on 2006-07-16
Thank you so very much!!!
By the way domino, I tried answering that exact question once, I'm not sure we solved everything in that thread, but at least you can try some of the things we write about. [How to make static mountpoint for usb drives]("http://ubuntuforums.org/showthread.php?t=91948")

---

### Post by sciyoshi on 2006-07-16
In the howto you say we need fuse 2.3.3, but the latest is 2.5.3, is that what you meant?

---

### Post by glennric on 2006-07-16
Where do you get the ntfs-3g files?

---

### Post by givré on 2006-07-16
Easy HowTo (without compiling) to use this great soft
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by domino on 2006-07-17
> **dlai said:**
> Thank you so very much!!!
By the way domino, I tried answering that exact question once, I'm not sure we solved everything in that thread, but at least you can try some of the things we write about. [How to make static mountpoint for usb drives]("http://ubuntuforums.org/showthread.php?t=91948")
The link you offered does a cleaner job with mounting ext drivers. The only addition step yo have to do is run the **sudo mount -a** command for the ext drive to mount.

My config:

~$ udevinfo -a -p $(udevinfo -q path -n /dev/sda)
```
device '/sys/block/sda' has major:minor 8:0
  looking at class device '/sys/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:0"
    SYSFS{range}=="16"
    SYSFS{removable}=="0"
    SYSFS{size}=="156301487"
    SYSFS{stat}=="     679     5067     5940      596        0        0        0        0        0      592      596"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-2/5-2:1.0/host0/target0:0:0/0:0:0:0':
    BUS=="scsi"
    ID=="0:0:0:0"
    DRIVER=="sd"
    SYSFS{device_blocked}=="0"
    SYSFS{iocounterbits}=="32"
    SYSFS{iodone_cnt}=="0x2ac"
    SYSFS{ioerr_cnt}=="0x0"
    SYSFS{iorequest_cnt}=="0x2ac"
    SYSFS{max_sectors}=="240"
    SYSFS{model}=="A               "
    SYSFS{queue_depth}=="1"
    SYSFS{queue_type}=="none"
    SYSFS{rev}=="3.19"
    SYSFS{scsi_level}=="3"
    SYSFS{state}=="running"
    SYSFS{timeout}=="30"
    SYSFS{type}=="0"
    SYSFS{vendor}=="ST380021"


  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-2/5-2:1.0':
    BUS=="usb"
    ID=="5-2:1.0"
    DRIVER=="usb-storage"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="08"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="50"
    SYSFS{bInterfaceSubClass}=="06"
    SYSFS{bNumEndpoints}=="02"
    SYSFS{modalias}=="usb:v067Bp2507d0100dc00dsc00dp00ic08isc06ip50"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-2':
    BUS=="usb"
    ID=="5-2"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0100"
    SYSFS{bmAttributes}=="c0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="6"
    SYSFS{idProduct}=="2507"
    SYSFS{idVendor}=="067b"
    SYSFS{manufacturer}=="Prolific Technology Inc."
    SYSFS{maxchild}=="0"
    SYSFS{product}=="Mass Storage Device"
    SYSFS{serial}=="0"
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"
```

/etc/udev/rules.d/10-local.rules:

I took **all** the info from "**looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-2'**" and combined them to like this:
```
BUS=="usb", ID=="5-2", DRIVER=="usb", SYSFS{bConfigurationValue}=="1", SYSFS{bDeviceClass}=="00", SYSFS{bDeviceProtocol}=="00", SYSFS{bDeviceSubClass}=="00", SYSFS{bMaxPacketSize0}=="64", SYSFS{bMaxPower}=="100mA", SYSFS{bNumConfigurations}=="1", SYSFS{bNumInterfaces}==" 1", SYSFS{bcdDevice}=="0100", SYSFS{bmAttributes}=="c0", SYSFS{configuration}=="", SYSFS{devnum}=="6", SYSFS{idProduct}=="2507", SYSFS{idVendor}=="067b", SYSFS{manufacturer}=="Prolific Technology Inc.", SYSFS{maxchild}=="0", SYSFS{product}=="Mass Storage Device", SYSFS{serial}=="0", SYSFS{speed}=="480", SYSFS{version}==" 2.00", NAME{all_partitions}=="ST380021"
```

From what i gather, udev and fstab are not related to mounting drives. I'm not so clear where pmount is mixed up in this. The end result is that when you create a directory "external" in the /media directory, then add **/dev/sda1	/media/External	ntfs-3g	silent,umask=0,locale=en_US.utf8 0 0** to your fstab, it can not automount. This is the reason that i have to manually mount usiong the **umount** command.

I'm still in the trial and error stage, so there might be home for me yet. It would be much better to have any external USB drives mount automatically with full access without user intervention.

---

### Post by domino on 2006-07-17
this is my fstab. Notice that the first is External USB rive and will only place this link on the desktop. The other two is still mount but you'll have to browse to the /media directory.

```
/dev/sda1	/media/External	ntfs-3g	silent,umask=0,locale=en_US.utf8 0 0
/dev/hda1	/media/WinXP	ntfs-3g	silent,umask=0,locale=en_US.utf8 0 0
/dev/hdc6	/media/Vista	ntfs-3g	silent,umask=0,locale=en_US.utf8 0 
```

Once thats done, you can browse the /media folder and create bookmark (drag the folder to the left pane in nautilus).

[[IMG]http://img225.imageshack.us/img225/8174/1am4.th.png[/IMG]](http://img225.imageshack.us/my.php?image=1am4.png)

Edit: the erternal drive mounts properly without user intervention if you have the option added in fstab and reboot while the usb device is on. If the ext drive is not on or if not mounted on login, you will need to manually mount that ext drive after the external device is switched on while in gnome or kde.

---

