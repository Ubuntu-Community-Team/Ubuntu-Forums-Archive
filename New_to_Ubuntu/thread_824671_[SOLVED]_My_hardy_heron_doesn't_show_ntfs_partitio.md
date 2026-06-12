---
title: "[SOLVED] My hardy heron doesn't show ntfs partition of vista and the data therein."
date: 2008-06-10
forum: New to Ubuntu
---

### Post by student21 on 2008-06-10
Hi

I'm a newbie to ubuntu.  I've installed ubuntu 8.04(64 bit flavor) using wubi within Vista on HP pavilion dv6833us laptop.

When I go into ubuntu, I don't get the primary partition C drive where vista and my data collection(including music) is there-- under the menu 'places' or in file browser.  I'd like to access the data from ubuntu and if possible the ubuntu data from vista.  Without going into terminal, is it possible to get this access?.  I've read that 8.04 provides full support to ntfs partitions but I don't know why I'm not able to access the drive.  Is it a specific problem with wubi installation?  When I was accessing ubuntu on live cd, it showed primary partition and windows files but not on wubi.

Thanks for the help.

---

### Post by aquavitae on 2008-06-10
It should be possible to get the access, but probably not without using the terminal to set it up - its just much easier to give instructions over a forum as terminal commands that as click-heres.

Just a check of what's on your system and how its set up: can you post the contents of the /etc/mtab file and the output of the terminal command ;) ```
sudo fdisk -l
```
If you don't know where to find the terminal its under applications-accessories.

---

### Post by student21 on 2008-06-10
Hi Aquavitae Thanks for your response.

This is the output from sudo fdisk -l

```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475d475c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28875   231938406    7  HPFS/NTFS
/dev/sda2           28876       30401    12257595    7  HPFS/NTFS


```

contents of /etc/mtab

```

/host/ubuntu/disks/root.disk / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/host/ubuntu/disks/boot /boot none rw,bind 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/zah/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=zah 0 0

```


And the contents of /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```


What do you think has happened in my wubi installation that won't let windows partition in file browser or menu places?  I'd like to clarify that there are 2 ntfs drives one is primary and another is secondary where recovery of vista(pre-installed O.S) files have been loaded.  In my Ubuntu file system I'm able to see the secondary recovery drive.  My problem is I'm not able to see the primary drive where I've a lot of data that I'd like to access from ubuntu.

I think it'd be easy if changes can be done over GUI, won't it be easy than terminal??

---

### Post by aquavitae on 2008-06-11
> **student21 said:**
> 
What do you think has happened in my wubi installation that won't let windows partition in file browser or menu places?  I'd like to clarify that there are 2 ntfs drives one is primary and another is secondary where recovery of vista(pre-installed O.S) files have been loaded.  In my Ubuntu file system I'm able to see the secondary recovery drive.  My problem is I'm not able to see the primary drive where I've a lot of data that I'd like to access from ubuntu.Do you have two physical disks plugged into your computer, or do you mean two partitions on one disk? That's what it looks like from the output of fdisk - one 250Gb disk with two partitions. Do you know which partition you want to mount - the first (probably C:\ in windows) or the second (probably D:\)?

To check if you can mount it, use the command ```
gnome-mount /dev/sda1      *(or /dev/sda2 for the second partition)*
```
That should mount it and show it on the desktop. If that works then we can figure out how to make it permanent.

> 
I think it'd be easy if changes can be done over GUI, won't it be easy than terminal??
Something that often bugs new linux users :)... It is probably more comfortable for you to use the GUI, just because you're used to it, but there are two good reasons to use the terminal: A GUI has not been written for every tool available, and it is often necessary to use them to fix problems. The other is that its just much easier to post a command that you can cut and paste into the terminal, than to try to explain exactly which buttons to click in the GUI, especially as different people may have ther desktops set up differently, or different GUIs installed. Basically the terminal is universal across linux, so (assuming the required tools are installed) most commands should work regardless of your specific setup.

Ok, that was longer that I intended, but hopefully it explains :)

---

### Post by student21 on 2008-06-11
Hi Aquavitae

To clarify, I've only one hard disk that came with the laptop.  No external device has been attached.  What I was referring to were two different partitions on the hard drive c: and d:.  D: is showed under a name HP_Recovery in menu 'places' and a tool 'Computer' that I think is analogous to 'my computer' from windows.  My problem is my C: is not getting displayed and I'm not able to get access.

I worked with

```
gnome-mount /dev/sda1

```
The terminal just returns to prompt.  It doesn't even ask for password like it does for other commands.  I've also tried variants like

```
gnome -mount /dev/sda1

sudo gnome-mount /dev/sda1.
```

On desktop I don't get my c:.  All these commands do nothing on my system.

But I found  a temporary work around from this forum

like:

```
sudo mkdir /media/windows

sudo mount /dev/sda1 /media/windows -t ntfs -o umask=0002,nls=utf8

or even sudo mount /dev/sda1 /media/windows
``` 

which shows the partition inside 'media' folder under 'file system' in 'computer' and inside 'windows' folder.  But how to make it work properly and permanently?.  And why is this happening?  and why gnome-mount didn't display the partition on desktop? I don't know.

---

### Post by sherin on 2008-06-11
you dont you add the same to /etc/fstab ?

---

### Post by aquavitae on 2008-06-11
Just to clarify, it won't show it as "C:\", it will probably show it as something like "80Gb Volume" or a volume name. Also, the command that requires a password is "sudo". It basically gives you temporary root permission in order to run sensitive commands. gnome-mount is similar to mount (which worked for you) except that it requires root permissions (hence the sudo) and a lot of other arguments. But since that works, its easy enough to make it permenant. In a terminal, run ```
sudo gedit /etc/fstab
``` This will open up a file in a text editor with whole lot of text. Add this to the end:
```

/dev/sda1 /media/windows ntfs umask=0002,nls=utf8 0 0

```
Whenever to turn on your computer, the "C drive" will be mounted to /media/windows. If you want to get it working like the other drives (i.e. showing up under places) it will mean figuring out why gnome-mount doesn't work (Ok, I've just had a look at the manual, and I think I gave you the wrong command!), since this is the command that is used by the gui. What happens if you run this:

First, make sure it isn't still mounted
```
sudo umount /dev/sda1
```
Then try gnome-mount with verbose logging (and the correct arguments)
```
gnome-mount -v --device /dev/sda1
```

---

### Post by student21 on 2008-06-11
Hi Aquavitae

Thanks!  And yes the extra information was useful.

I tried

```
gnome-mount -v --device /dev/sda1
```

then a message gets displayed in the next line:

```
gnome-mount 0.8
```


Then it returns to prompt.  Does that give any clue?

---

### Post by aquavitae on 2008-06-11
Just tried it on mine and it seems -v doesn't do what it should, it just gives version information. Try it without the -v and then have a look in the /media folder (terminal command "ls /media") to see if anything new appears. It probably won't be labeled "windows" or anything easy to understand - it will be given the name of the volume label, so probably something like "New Volume".

---

### Post by student21 on 2008-06-12
Hi Aquavitae

I've tried the following code just taking out -v:

```
gnome-mount --device /dev/sda1
```

after that it returns to prompt, then "ls /media" in terminal displays in colour following message:

```
cdrom cdrom0 windows
```

I've manually checked inside filesystem for /media folder, there are no new files.  Windows was the folder created earlier using mkdir command.  Otherwise cdrom and cdrom0 are default in there.  I don't see any change.

---

### Post by aquavitae on 2008-06-12
Ok, I'm a bit stumped... 

Did you make any changes to /etc/fstab? If so, remove them. Then make sure the device is not mounted in any way with the command
```
sudo umount -v /dev/sda1
```
Then make sure you have access to /media/windows
```
sudo chmod a=rwx /media/windows
```
Then try specifying more options to gnome-mount
```
gnome-mount --device /dev/sda1 --mount-point windows --fstype ntfs --text
```
That should mount it to /media/windows
If it doesn't work try it with --fstype ntfs-3g instead of --fstype ntfs. If that also doesn't work, post the output (if any) of 
```
gnome-mount --display-settings --device /dev/sda1
```

---

### Post by student21 on 2008-06-13
Hi Aquavitae

I didn't make any change to /etc/fstab yet. 

when I gave the following command in terminal:

```
sudo umount -v /dev/sda1
```

It returned a message:

```
Could not find /dev/sda1 in mtab
umount: /dev/sda1: not mounted
```

Then I executed the following commands in terminal:

 ```
sudo chmod a=rwx /media/windows

 gnome-mount --device /dev/sda1 --mount-point windows --fstype ntfs --text

There was no change in /media/windows so I executed:

 gnome-mount --device /dev/sda1 --mount-point windows --fstype ntfs-3g --text
```

There was no change in /media/windows.  I checked manually there was no new volume or folder or drive displayed.

Finally I tried 

```
gnome-mount --display-settings --device /dev/sda1
```

For this command, terminal returns this following message:

```
Displaying settings for volume (overrides drive settings)
hal udi:      /org/freedesktop/Hal/devices/volume_uuid_0B13A67147F273EF
There are no settings; you can use --write-settings

```

---

### Post by aquavitae on 2008-06-13
Hmmm...

I think at this stage the easiest will be to add the device directly to fstab (as in a previous post) and just create a link to it under places.

One more test, which probably won't help ;):
```
lshal
```

And another thought; try gnome-mount with "--mount-point windows_c". Its possible that it cannot mount to an existing folder (i.e. windows)

---

### Post by student21 on 2008-06-23
Hi Aquavitae

Sorry for the delayed reply as I wasn't having net access.

This is the output for lshal:

But some pages I think got scrolled up in no time and I think only dos options equivalent like /p/o will help to see them.

```
info.udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_hw_specific_1'  (string)
  linux.device_file = '/dev/snd/hwC0D1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_hw_specific_0'
  access_control.file = '/dev/snd/hwC0D0'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/hwC0D0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  alsa.type = 'hw_specific'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  info.product = 'HDA Intel ALSA hardware specific Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_hw_specific_0'  (string)
  linux.device_file = '/dev/snd/hwC0D0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_oss_pcm_0_0'
  access_control.file = '/dev/dsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  info.product = 'ALC268 Analog OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'ALC268 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_control__1'
  access_control.file = '/dev/snd/controlC0'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  info.product = 'HDA Intel ALSA Control Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_oss_pcm_0'
  access_control.file = '/dev/audio'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  info.product = 'ALC268 Analog OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'ALC268 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_283a'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801H (ICH8 Family) USB2 EHCI Controller #2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_283a'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7'  (string)
  pci.product = '82801H (ICH8 Family) USB2 EHCI Controller #2'  (string)
  pci.product_id = 10298  (0x283a)  (int)
  pci.subsys_product_id = 12492  (0x30cc)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_283a'  (string)
  info.product = 'EHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'  (string)
  info.vendor = 'Linux 2.6.24-18-generic ehci_hcd'  (string)
  linux.device_file = '/dev/bus/usb/006/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb6'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb6'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 4  (0x4)  (int)
  usb_device.product = 'EHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1a.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.vendor = 'Linux 2.6.24-18-generic ehci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb6/6-0:1.0'  (string)
  usb.bus_number = 6  (0x6)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb6/6-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 4  (0x4)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1a.7'  (string)
  usb.speed = 480.0 (480) (double)
  usb.speed_bcd = 294912  (0x48000)  (int)
  usb.vendor = 'Linux 2.6.24-18-generic ehci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 2.0 (2) (double)
  usb.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2835'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801H (ICH8 Family) USB UHCI Controller #5'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2835'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1'  (string)
  pci.product = '82801H (ICH8 Family) USB UHCI Controller #5'  (string)
  pci.product_id = 10293  (0x2835)  (int)
  pci.subsys_product_id = 12492  (0x30cc)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2835'  (string)
  info.product = 'UHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'  (string)
  info.vendor = 'Linux 2.6.24-18-generic uhci_hcd'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = 'UHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1a.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.vendor = 'Linux 2.6.24-18-generic uhci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1a.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Linux 2.6.24-18-generic uhci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2834'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801H (ICH8 Family) USB UHCI Controller #4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2834'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0'  (string)
  pci.product = '82801H (ICH8 Family) USB UHCI Controller #4'  (string)
  pci.product_id = 10292  (0x2834)  (int)
  pci.subsys_product_id = 12492  (0x30cc)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2834'  (string)
  info.product = 'UHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'  (string)
  info.vendor = 'Linux 2.6.24-18-generic uhci_hcd'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = 'UHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1a.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.vendor = 'Linux 2.6.24-18-generic uhci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1a.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Linux 2.6.24-18-generic uhci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2a03'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile GM965/GL960 Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2a03'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.product = 'Mobile GM965/GL960 Integrated Graphics Controller'  (string)
  pci.product_id = 10755  (0x2a03)  (int)
  pci.subsys_product_id = 12492  (0x30cc)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2a02'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile GM965/GL960 Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2a02'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'Mobile GM965/GL960 Integrated Graphics Controller'  (string)
  pci.product_id = 10754  (0x2a02)  (int)
  pci.subsys_product_id = 12492  (0x30cc)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0'
  drm.dri_library = 'i915'  (string)
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2a02'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.device_file = ''  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2a00'
  info.linux.driver = 'agpgart-intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile PM965/GM965/GL960 Memory Controller Hub'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2a00'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = 'Mobile PM965/GM965/GL960 Memory Controller Hub'  (string)
  pci.product_id = 10752  (0x2a00)  (int)
  pci.subsys_product_id = 12492  (0x30cc)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)


Dumped 113 device(s) from the Global Device List.
------------------------------------------------

```

```
gnome-mount --device /dev/sda1 --mount-point windows_c --fstype ntfs --text



 gnome-mount --device /dev/sda1 --mount-point windows_c --fstype ntfs-3g --text

```

didn't yield any result.

Only 

```
sudo gedit /etc/fstab


/dev/sda1 /media/windows ntfs umask=0002,nls=utf8 0 0


```

works for me.  The drive gets displayed inside /media/windows from the start up itself.  Still it doesn't come under 'places'.

What is the underlying problem causing this fault?

And some additional questions:

I've heard usually Linux is very stable.  I tried playing Extreme tux racer and in between I got hanged severely that required hard boot.  Why is linux behaving like windows?  and is there any equivalent to alt+ctrl+del on windows to invoke task manager just to end the hanged process?

Compared to windows vista, the volume output(on speakers) on ubuntu is very low! why is that?  How can I rectify it?

---

### Post by aquavitae on 2008-06-24
lshal tooks like it may give some usefull info, but ther relevant section is nissing. You can pipe the output of a command to a file by using '>'. Try ```
lshal > ~/lshal_output.txt
``` This will create a file lshal_output.txt in your home folder which you can attach to a post.

Your other questions:
Sounds like you're having a bad experience with linux...
Tuxracer shouldn't hang like that. Try running it in a terminal - when it hangs it might show an error message in the terminal. To do that, check the command by editing the menus, and then type it into the terminal. The system monitor can be used to kill processes that have got out of control, but I don't know of a shortcut key to open it. The other option is to press ctrl-alt-F1 to switch to another terminal, and then use an appropriate combination of the following commands:
**top** - shows running processes and their PID. To exit it press 'q' and to kill a process press 'k' followed by the PID.
**killall <name>** - kills all processes with the name <name>. E.g. killall tuxracer.
Also, instead of a hard reboot, ctrl-alt-backspace kills the xserver, effectively logging you out and closing all your open programs. Its safer than rebooting.

I'd guess the low volume is just because its turned down. There is a little speaker icon in the top corner, but otherwise my usual method of making sure everything is turned up properly is to use ```
alsamixer
```. Check all the volume controls, there are some towards the end which look deceptively unimportant.

---

### Post by student21 on 2008-06-25
Hi aquavitae

I've prepared lshal_output.txt but it exceeds attachment limit.  If i stored the file in abiword format, forum says it's invalid file, if I tried to save the file microsoft word document file, still it exceeds attachment limit.  Same is the case with .odt.  How shall I attach that file??

How to run extreme tux racer from terminal?  When I said it hangs severely it crashes and I have no option to select system monitor on screen.  Completely screen goes bizzare with nothing sensible on screen.

I used totem movie player default for a video clip, but for every manual seek it hangs and I need to 'force quit' the greyed out window if its smaller than full screen size and if its full screen size I'm forced to use alt+ctrl+F1 or alt+ctrl+backspace.  Atleast the later logs out to login area of desktop but alt+ctrl+f1 goes to terminal and I don't know how to resume from there to gui.

No my volume output is low even after turning up to 100% in Master volume icon and a small volume icon in the player.  I'd say vista's volume output is comparatively better but still not satisfactory, sometimes I use KM player on windows to maximize volume but i don't know what to use on ubuntu?

Thanks for your patience and help.

---

### Post by aquavitae on 2008-06-26
Text is the smallest format you'll get without compression, so try compressing it.

It sounds like the graphics options for extremetuxracer might be wrong. The first thing I'd do is to have a look at whatever config files there are. Look in your home folder (you'll have to show hidden files) for something likely, e.g. .extremetuxracer.rc. Open up whatever you find and see if there is anything obviously wrong (e.g. resolution set to 640x480 on your 21" wide screen). If you think its necessary, post what you find.  You might also find a log file there which could give info on why its crashing.

Did you try alsamixer - all the settings? It has to be a volume control thats turned down, just need to find it.

---

### Post by student21 on 2008-06-26
Hi Aquavitae

I've tried to upload that file in .zip file.  Let me know if it has rightly got uploaded.  I downloaded .rar using synaptic package manager to do this.  When I use .rar on windows I get an option to make archive where I can set password for compressed file.  I don't find any such thing in ubuntu.  Am I missing something?

When I typed Alsamixer on terminal I'm getting some graphic on terminal screen.  It shows Master, Headphone, PCM, front, frontmic, Line in, mic boost, caller 1, offhook.  I don't get to tune them except master.  Whenever I scroll the mouse the Master graphic bar increases and decreases.  But I can't affect other bar graphs, how can I increase them.  Some other details on graphic are: Head phone 70<>70, PCM 100<>100, Front 81<>81, Other 3 mic parameters 0<>0; in caller 1 and offhook there are letters MM.  So how can I manipulate these settings?

---

### Post by seungp on 2008-06-26
student21


Just ran across your issue. 

Have you checked if you're logging out of your windows installation or are you putting it into suspend/hibernate modes?

I've found that when you put the computer into suspend/hibernate modes, the file system is left in an "unstable" state that ntfs module interprets as being unsafe to mount. 

seungp

---

### Post by aquavitae on 2008-06-27
> **seungp said:**
> student21


Just ran across your issue. 

Have you checked if you're logging out of your windows installation or are you putting it into suspend/hibernate modes?

I've found that when you put the computer into suspend/hibernate modes, the file system is left in an "unstable" state that ntfs module interprets as being unsafe to mount. 

seungp
I've seen that problem before, but this isn't it. In that case, it would bring up a sensible error message, and the mount command wouldn't work either.

Student21:

I have no more ideas. lshal didn't give me any useful information. All I can suggest is that you add the device to fstab and let it automount that way. I prefer doing that anyway because then its always mounted when I want it.

Alsamixer is operated from the keyboard (like most command line apps). IIRC, PgUp and PgDown adjust the volume, arrow keys move left and right. I think spacebar does something too.

---

### Post by Canis familiaris on 2008-06-27
Maybe this thread will help

[http://ubuntuforums.org/showthread.php?t=841228](http://ubuntuforums.org/showthread.php?t=841228)

---

### Post by student21 on 2008-07-02
Hi All

Thanks for your suggestion.

> I've found that when you put the computer into suspend/hibernate modes, the file system is left in an "unstable" state that ntfs module interprets as being unsafe to mount.

When I'm in vista and if I hibernate, when I click power button, it only resumes vista.  I don't know how to boot into ubuntu when vista is in hibernate mode?  Is it possible?

Thanks Aquavitae for all your efforts.  Yes adding that line to fstab is automounting that partition everytime but it doesn't come under places.  what if i decide to move my wubi to a partition installation.  Will I be able to access the data from ubuntu then?

Aquavitae your suggestions about alsamixer were a bit fruitful.  I was able to increase a bit in volume output but still it isn't satisfactory or like I get in vista.  And unfortunately once I kept alsamixer alive and went to watch a clip and Ubuntu crashed severely.

Also when I click suspend from shut down menu for a break, resuming it using mousepad causes it to hang severely which requires a hard boot.

Is there a way to reduce these hangs and crashes in ubuntu?

And in my home folder there's no file named '.extremetuxracer.rc' including hidden files.  I even searched in file browser but it didn't return result.

Also I don't know how can I get webcam chat.  pidgin only gives text mode.  And its very efficient in text mode but there's no video chat support.  So I got kopete but kopete doesn't even show online friends instead it shows all offline.  If you want to post these things in a new thread because it's digressing the title its ok for me, but please let me know the link.

---

### Post by aquavitae on 2008-07-02
> **student21 said:**
> 
When I'm in vista and if I hibernate, when I click power button, it only resumes vista.  I don't know how to boot into ubuntu when vista is in hibernate mode?  Is it possible? I don't think so. I think you have to actually reboot in order to load linux.

> 
Thanks Aquavitae for all your efforts.  Yes adding that line to fstab is automounting that partition everytime but it doesn't come under places.  what if i decide to move my wubi to a partition installation.  Will I be able to access the data from ubuntu then?Possibly. I don't really know much about wubi (I always just install to a new partition, so I've never found a reason to use it) so it could be causing the problem. I can see no reason why you shouldn't be able to see the partition, so it could be wubi just as well as anything else.

> 
Aquavitae your suggestions about alsamixer were a bit fruitful.  I was able to increase a bit in volume output but still it isn't satisfactory or like I get in vista.  And unfortunately once I kept alsamixer alive and went to watch a clip and Ubuntu crashed severely.You don't need to keep alsamixer open - the volume changes are kept when you close it. Ubuntu shouldn't crash because of that, although I suppose it shouldn't crash at all :).

> 
Also when I click suspend from shut down menu for a break, resuming it using mousepad causes it to hang severely which requires a hard boot.There are known problems with the kernel related to suspend/hibernate which the devs are working on at the moment. Hopefully it will be sorted out soon.

> 
Is there a way to reduce these hangs and crashes in ubuntu?
One at a time...

> If you want to post these things in a new thread because it's digressing the title its ok for me, but please let me know the link.It would be better for you to start new threads. Its best to start a new thread for each problem you have in the appropriate forum. That way you get experts in each are helping you. E.g. I know nothing about kopete so I can't help there, and someone who does understand it may not read a thread on NTFS partitions.

---

### Post by student21 on 2008-07-02
Hi Aquavitae



I just made a mistake about alsamixer's audio output.  Volume output is equal to that I get from vista or slightly better than that.  What I wished was, If i can get more output it'd be satisfactory.:)

yes everytime I want to get to ubuntu I click restart from vista to select it from boot menu and the same holds good if I want vista from ubuntu.  

You didn't say anything about '.extremetuxracer.rc'?

And Anurag panda thanks for your suggestions, somehow I did the same thing like creating dir named windows in media and mount that partition to that folder.

---

### Post by student21 on 2008-07-02
....contd


Sometimes keeping all values maximum in alsamixer cause speakers to create glaring sound after the original audio track.  could this be corrected?

---

### Post by stalkingwolf on 2008-07-02
> **student21 said:**
> 


And some additional questions:

I've heard usually Linux is very stable.  I tried playing Extreme tux racer and in between I got hanged severely that required hard boot.  Why is linux behaving like windows?  and **is there any equivalent to alt+ctrl+del** on windows to invoke task manager just to end the hanged process?

Compared to windows vista, the volume output(on speakers) on ubuntu is very low! why is that?  How can I rectify it?

right click on your top panel, click on add to panel, click force quit,
click add .  this will put the force quit icon in your panel.  Then simply
click the icon and click the offending window.


doesnt wubi install ubuntu inside the windows system like a VM?

---

### Post by student21 on 2008-07-03
Hi Stalkingwolf thanks for that tip.  I've created an icon on the top panel to force quit some application.  But what I mentioned in the particular post to which you've replied is severe crash/hang where I don't get to access desktop or any other tool from menu.  So I doubt it'd be helpful during such situations.

And Aquavitae

I've overlooked something where c: i.e primary partition is automounted.  It's in /host in filesystem.  Fortunately I happened to read this tip from a user 'ago' somewhere on this forum.  But still I've one doubt-- can I make a link to this partition from the menu 'places' and from desktop so that I can directly get into this folder?  If I can do that I can concentrate on other doubts and questions.

and I don't understand the following answer:  You mean I should use one application at a time to avoid hangs and crashes or do you mean something else?

> Quote:
Is there a way to reduce these hangs and crashes in ubuntu?
One at a time...

---

### Post by suplilumas on 2008-07-03
if still you have auto mount problem try this. i solve problem right now with this.  
do you have two folder /media/sda1 and /media/sda1 if no cerate it with 
```

sudo mkdir /media/sda1
sudo mkdir /media/sda2

```
then open fstab with command
```

sudo gedit /etc/fstab

```
copy this two line save and exit. after restart you must see drive icon on your desktop and in side places. i hope this will help you.
```

/dev/sda1  /media/sda1     ntfs         rw,auto,user,exec,umask=000    0  0
/dev/sda2  /media/sda2     ntfs         rw,auto,user,exec,umask=000    0  0

```

---

### Post by aquavitae on 2008-07-03
> **student21 said:**
> Hi Stalkingwolf thanks for that tip.  I've created an icon on the top panel to force quit some application.  But what I mentioned in the particular post to which you've replied is severe crash/hang where I don't get to access desktop or any other tool from menu.  So I doubt it'd be helpful during such situations.

Can't remember if this has already been posted in this thread: you can use 'killall <appname>' to kill an app. When a program hangs, press Ctrl-Alt-F1 to switch to a different terminal, log in, and use killall. Then press Ctrl-Alt-F7 to go back to the gui. Also, instead of a hard reboot, Ctrl-Alt-Backspace will kill the xserver, basically killing all your running apps and logging you out. If it hangs to the stage that your keyboard doesn't even respond (e.g. the numlock light doesn't go on/off when pressing the key), then you'll have to do a hard reboot.

> 
I've overlooked something where c: i.e primary partition is automounted.  It's in /host in filesystem.  Fortunately I happened to read this tip from a user 'ago' somewhere on this forum.  But still I've one doubt-- can I make a link to this partition from the menu 'places' and from desktop so that I can directly get into this folder?  If I can do that I can concentrate on other doubts and questions.

The /host must be particular to wubi. Actually, now that I  think about it, it makes sense. It needs to mount /host/ubuntu/disks/root.disk to /, so therefore it first needs to know where /host is. If you convert to a separate installation you should be able to get it in places as you want. Otherwise I'd suggest to just add it as a bookmark. You can do this by simply dragging /host in nautilus into places.

> 
and I don't understand the following answer:  You mean I should use one application at a time to avoid hangs and crashes or do you mean something else?Sorry - i just meant that usually each crash is caused by something different, so we just need to work through them. There isn't a miracle fix which will get rid of them all in one go.

Extremetuxracer is a bit out of my area - if a game doesn't run for me with very little tweaking I usually just couldn't be bothered and try something else. I'd suggest making a post under the gaming forum.

---

### Post by howlingmadhowie on 2008-07-03
ubuntu should only crash when the kernel goes awol, and that shouldn't happen. i wonder about the wubi install. maybe the ntfs-3g driver still has problems every now and then reading from the disk. the other possibility would be that there's a piece of hardware on the computer which requires a buggy driver.

---

### Post by aquavitae on 2008-07-03
> **howlingmadhowie said:**
> ubuntu should only crash when the kernel goes awol, and that shouldn't happen. i wonder about the wubi install. maybe the ntfs-3g driver still has problems every now and then reading from the disk. the other possibility would be that there's a piece of hardware on the computer which requires a buggy driver.Bugs happen. A complete system crash probably stems from the kernel or kernel modules, but when a program hangs it can sometimes take up so much of the resources (e.g. a memory leak within an endless loop), that it causes the rest of the system to freeze too. I doubt nfts-3g is any more buggy than any other drivers though.

---

### Post by student21 on 2008-07-03
Hi Aquavitae 

> Otherwise I'd suggest to just add it as a bookmark. You can do this by simply dragging /host in nautilus into places.


Is nautilus the file browser??  Ok I did drag the host to the menu places but it created a folder on the panel just near those internet tools like firefox and other mail tools.  if i click this folder icon it just opens /host in filebrowser.  But there's no addition under places.  Also inside nautilus, I tried to drag the /host on the left panel into places.  It just started process to copy all those files but it wasn't clear where it's trying to copy.  Is this what you wanted me to do or is there any other way to create a shortcut link to /host from desktop and from under places?

Ctrl-Alt-F1 goes to some blank dark screen and there's no terminal to see or type anything.  Fortunately I pressed Ctrl-Alt-F7 to return to GUI. Am I missing something here?

Also shall I mark this thread solved?  How to mark that?

---

### Post by aquavitae on 2008-07-04
Yes, nautilus is the file browser. If you drag it to the menu at the top of the screen, you are actually just draging it to the panel so you get a link on the panel. You do need to drag it the left under places, but make sure you drag it to the bottom part where there is a blank area, otherwise it will try to copy /host into whichever 'place' you are over when you let go.

Each Ctrl+Alt+F_key goes to a new terminal. On some systems Ctrl-Alt-F1 is assigned to an error log or something. I can't remember how ubuntu is set up (I'm not at it right now), but if Ctrl-Alt-F1 doesn't work, try F2 or F3. It should take you to a login prompt.

You can mark the thread as solved from thread tools at the top.

---

### Post by student21 on 2008-07-04
Hi Aquavitae

I tried dragging /host in nautilus to the bottom area of the left.  It gets added under places but along with Home folder, Desktop, Music, Documents, Videos, Pictures above the separator.  I wanted to add it along with computer, Cd/Dvd creator, Dvd drive, Hp_Recovery(d drive) i.e second region of the menu and upper part of the left panel in nautilus.  But in the left of nautilus the above said region is cramped for space and the last place is Trash in nautilus though it doesn't come under original menu 'places' and if I drag host there it says it can't move /host to trash and if it can delete /host.  Is there a way to drag to my desired area?

Ctrl-Alt-F2 takes to login prompt.  But if I have to give Killall <appname> there, is it ok if I give ```
killall totem
``` to kill the hanged process of totem movie player or should I look for some technical name there?

---

### Post by aquavitae on 2008-07-04
I don't know of a way to get /host into the area you want. It will probably be somewhere in a configuration file, but I don't know where. I'll have a look and see if I can find anything.

Most of the time, the app name is the same as the technical name, so yes, killall totem would work. In addition, these commands may be useful:
```

ps -e          => List all the processes
ps -e | less   => List all the processes and pipe it to a scrolling view for easy viewing
man ps         => Show the ps man page, i.e. the manual.

```

---

### Post by ZiF on 2008-08-08
I have the same problem, though I use openSUSE 10.3, but that' how I've solved it.

# sudo su
# hal-find-by-property --key block.device --value /dev/sda1
That gave me UDI of my /dev/sda1 device

# hal-set-property --udi <my UDI, whatever the previous command printed to the output> --key volume.ignore --bool false
or
# hal-set-property --udi `hal-find-by-property --key block.device --value /dev/sda1` --key volume.ignore --bool false

# halmount /dev/sda1 -t ntfs-3g -o umask=0222

The problem was, that for some reasons my /dev/sda1 partition had volume.ignore flag set to TRUE at hal-daemon.

What I did to add it to automount on boot is I have added that script to my /etc/init.d/xdm rc-script. I'm not sure if it's the same in Ubuntu, but you can try.

---

### Post by student21 on 2008-08-14
Hi Zif

Eventually I found out that--that partition shows up in /host inside filesystem.  Though I did create a directory named windows and added a line in fstab to mount the drive inside that directory, from wubi I can access the primary partition in the above said folder.  

Thanks for your information:)

---

