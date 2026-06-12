---
title: "[SOLVED] Libusb permissions?!?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-08-26
I am using avrdude and I read it uses libusb to communicate with the AVRISP mkII. I have been running it as root because when I try to run it as a normal user I get

avrdude: usb_open(): cannot read serial number "error sending control message: Operation not permitted"
avrdude: usb_open(): cannot read product name "error sending control message: Operation not permitted"
avrdude: usbdev_open(): error setting configuration 1: could not set config 1: Operation not permitted
avrdude: usbdev_open(): did not find any USB device "usb"

I have not been able to find how to make my user have the permissions to use it.

Any ideas?

Thanks a lot,
Justin

---

### Post by nicedude on 2008-08-26
When things require root access to use such as when they require sudo to work, they are not meant to run via a regular user account but instead require root privileges to run properly. It is very unwise to try and enable your user account to have full root privileges all the time and therefore you should just use programs such as these with sudo type commands for safety's sake. If you ever try to write a script and have problems getting a command to work with sudo from within the script then PM me and I can help with that. But in general when something wants to be started via sudo it is good to start it that way. Don't find a guide or listen to some knucklehead here and just change your login to "ROOT" and start using that as your account, as that has serious security implications and while in that type of login you can break your whole system in 1 second with the wrong command :-). The Ubuntu developers are trying to protect users with the way things are setup not restrict you but just to protect you.

---

### Post by Commander_Bob on 2008-08-27
I know that I should not login as root. What kind of security problems do USB devices pose? I have only had this problem with my AVRISP mkII programmer. All mass storage devices I can read and write to without sudo.

Is it not a larger security problem to give an entire program root privies instead of just allowing it to write to a USB device?

---

### Post by anewguy on 2008-08-27
It's also quite possible that the USB device is getting mounted as owned by root, particularly if this is a somewhat unique device.  Working with hacked CVS one time use cameras I had a similar problem.  The solution was to create another permissions file which mounted the device for world access (I'm the only one on my PC - you could make it mount to a certain group and put yourself in that group).

In order to try to set that up for you to test, please be sure the device is plugged in and then do the following in a terminal window and post the output back here.

(1) lsusb

Hopefully you will see your device listed, though it may just be a blank name.

(2) For that device:

lsusb -v -d xxx:xxx  where the xxx:xxx are the last 2 sets of numbers on the list.

Check what I did here for my non-standard CVS camera:

dave@dave-desktop:~$ lsusb
Bus 004 Device 007: ID 0dca:002b <=== You want these 2 numbers 
Bus 004 Device 004: ID 03f0:7604 Hewlett-Packard Deskjet 3940
Bus 004 Device 003: ID 050d:705c Belkin Components 
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0053 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000
  
dave@dave-desktop:~$ lsusb -v -d 0dca:002b

Bus 004 Device 007: ID 0dca:002b  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0dca 
  idProduct          0x002b 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          3 
    bmAttributes         0xc0
      Self Powered
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)
dave@dave-desktop:~$ 

I suspect we may be able to fix this just as I did for my cameras.  :)

---

### Post by Endolith on 2008-08-27
> **anewguy said:**
> It's also quite possible that the USB device is getting mounted as owned by root

Why would that happen?

> lsusb -v -d xxx:xxx  where the xxx:xxx are the last 2 sets of numbers on the list.

You mean this:

```
lsusb -v -d xxx:xxx  where the xxx:xxx are the last 2 sets of numbers on the list.
```

> cannot read device status, Operation not permitted (1)

I get the same thing for my devices.  If I run with sudo, I can see everything.  I also get this error trying to access them through pyusb, which uses libusb.

---

### Post by Endolith on 2008-08-27
This might be helpful:

[HowTo run an EPSON scanner with libusb and hotplugging](http://www.khk.net/sane/libusb.html)

> You probably cannot access the scanner yet, that is if you are not running your frontend as root user. The problem is that the default permissions for new devices are so that normal users cannot access them.

---

### Post by anewguy on 2008-08-27
Basically, when a device is sort of a non-standard device (this is a little hard for me to explain), in particular not a usb file system, the mount rules in /etc/udev/rules.d/40-basic-permissions.rules apply.  Now, be aware that the syntax changed going from 7.10 to 8.04, and right now I can't recall the pre-8.04 syntax.  To fix my problem, I created a file called 41-cvs-permissions.rules - just be sure the number is above 40 and doesn't conflict with an existing file.  Note that I created this file while running as root, so be sure to match it's permissions to those of the 40-basic-permissions.rules file.

My file contains the following - hopefully you'll now see the correlation of the numbers:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb",  ENV{DEVTYPE}=="usb_device",SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0027", MODE="0666"
SUBSYSTEM=="usb",  ENV{DEVTYPE}=="usb_device",SYSFS{idVendor}=="167b", SYSFS{idProduct}=="0101", MODE="0666"


Please note that the second usb_device is for another set of CVS cameras  have.  The idea is to make it either world accessable as I did with MODE="0666", or to set a group id or other such thing.

If you follow my previous post of the lsusb and this file, you will see I'm dealing with the usb device of major id (vendor) of "0dca" and minor id (product) of "0027".  It just was by coincidence that it was the first in my lsusb list.  These particular devices for me never come up with a name.

If you need more help with this way let me know.  Also, please post back if this solves your problem as it may be of use to others.

Dave  :)

---

### Post by Endolith on 2008-08-27
That worked for me!  Thank you.

---

### Post by anewguy on 2008-08-28
> **nicedude said:**
> When things require root access to use such as when they require sudo to work, they are not meant to run via a regular user account but instead require root privileges to run properly. It is very unwise to try and enable your user account to have full root privileges all the time and therefore you should just use programs such as these with sudo type commands for safety's sake. If you ever try to write a script and have problems getting a command to work with sudo from within the script then PM me and I can help with that. But in general when something wants to be started via sudo it is good to start it that way. Don't find a guide or listen to some knucklehead here and just change your login to "ROOT" and start using that as your account, as that has serious security implications and while in that type of login you can break your whole system in 1 second with the wrong command :-). The Ubuntu developers are trying to protect users with the way things are setup not restrict you but just to protect you.

And then there are actual permissions problems - we need to be sure we sort out the entire problem.

---

### Post by Commander_Bob on 2008-08-28
OK, new hardware same problem.

I just got an EVK1101 (AVR32 bit board) and it has a USB bootloader that I need to use. Doing lsusb it shows up, no problem, but then...
```
justin@justin-desktop:~$ lsusb -v -d 03eb:2ff6

Bus 003 Device 008: ID 03eb:2ff6 Atmel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03eb Atmel Corp.
  idProduct          0x2ff6 
  bcdDevice           10.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           27
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 0f 00 00 ff ff 01 01
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

or

```
justin@justin-desktop:~$ sudo lsusb -v -d 03eb:2ff6

Bus 003 Device 008: ID 03eb:2ff6 Atmel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03eb Atmel Corp.
  idProduct          0x2ff6 
  bcdDevice           10.00
  iManufacturer           1 ATMEL
  iProduct                2 AT32UC3B DFU
  iSerial                 3 1.0.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           27
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 0f 00 00 ff ff 01 01
Device Status:     0x0001
  Self Powered
```

In /etc/udev/rules.d/41-flip.rules I have (I am part of the group "flip")
```
# Atmel flip rules

#add support AT89C5132  AT89C51SND1 AT89C51SND2 ATOCDTARGET
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2fff", GROUP="flip", MODE="0660"

#add support AT89C5130 AT89C5131
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffd", GROUP="flip", MODE="0660"

#add support AT90USB1286 AT90USB1287
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffb", GROUP="flip", MODE="0660"

#add support AT90USB162
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffa", GROUP="flip", MODE="0660"

#add support AT90USB647 AT90USB646
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff9", GROUP="flip", MODE="0660"

#add support AT32UC3A0128 AT32UC3A0256 AT32UC3A0512 AT32UC3A1128 AT32UC3A1256 AT32UC3A1512
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff8", GROUP="flip", MODE="0660"

#add support AT90USB82
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff7", GROUP="flip", MODE="0660"

#add support  AT32UC3B0128 AT32UC3B0256 AT32UC3B064 AT32UC3B1128 AT32UC3B1256 AT32UC3B164
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff6", GROUP="flip", MODE="0660"
```

When I run batchisp I get 
```
justin@justin-desktop:~$ batchisp -device AT32UC3B0256 -hardware usb -operation onfail abort memory FLASH addrange 0x0 0xff read savebuffer /home/justin/Desktop/test hex386
=====================================================
JAVA_HOME = /usr/lib/jvm/java-6-openjdk/jre
=====================================================
LD_LIBRARY_PATH = /home/justin/flip.3.2.1/bin:/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:
=====================================================
PATH = /home/justin/flip.3.2.1/bin:/home/justin/gumstix/gumstix-oe/bitbake/bin:/home/justin/flip.3.2.1/bin:/home/justin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
=====================================================
= start batchisp
=====================================================
Running batchisp 1.2.0 on Thu Aug 28 15:13:41 2008



AT32UC3B0256 - USB - USB/DFU


Device selection....................... PASS 
Hardware selection..................... PASS 
Opening port........................... AtLibUsbDfu: 3EB 2FF6 no device present.
FAIL	Could not open USB device.
ISP done.

=====================================================
= end batchisp
=====================================================
```

The odd thing is that it does not work with sudo either...

Thanks for the help!
Justin

EDIT:
There is a file that came with batchisp and it reads
```
The Linux platform used different systems for device drivers.
Older systems uses hotplug while newer systems uses udev.

For "hotplug" systems:
The files libavrtools and libavrtools.usermap should be placed in /etc/hotplug/usb. The group avrtools should be created, containing the users which are allowed to use the JTAGICE mkII devices.


For "udev" systems:
Make a file called 'flip.rules' in the folder '/etc/udev/rules.d/' with the following content:
---
# Atmel flip rules

#add support AT89C5132  AT89C51SND1 AT89C51SND2 ATOCDTARGET
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2fff", GROUP="flip", MODE="0660"

#add support AT89C5130 AT89C5131
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffd", GROUP="flip", MODE="0660"

#add support AT90USB1286 AT90USB1287
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffb", GROUP="flip", MODE="0660"

#add support AT90USB162
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffa", GROUP="flip", MODE="0660"

#add support AT90USB647 AT90USB646
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff9", GROUP="flip", MODE="0660"

#add support AT32UC3A0128 AT32UC3A0256 AT32UC3A0512 AT32UC3A1128 AT32UC3A1256 AT32UC3A1512
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff8", GROUP="flip", MODE="0660"

#add support AT90USB82
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff7", GROUP="flip", MODE="0660"

#add support  AT32UC3B0128 AT32UC3B0256 AT32UC3B064 AT32UC3B1128 AT32UC3B1256 AT32UC3B164
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff6", GROUP="flip", MODE="0660"

---

Remember to run '/sbin/udevstart' after adding the file.
Also add group 'flip' and add necessary users.


Here is an explanation of how udev and hotplug works:

========================================
Linux specific installation information
by Linus Walleij
covering libusb 0.1.10
========================================

Since libusb is accessing the raw device nodes exported by the kernel in order to identify connected USB busses, functions and such, it needs to find these nodes. During the history of the Linux kernel, the placement and the way of accessing these nodes have changed.

This placement is closely related to hotplugging: i.e. addition and removal of USB functions at runtime.


Most current solution: use udev
===============================

The latest and greatest way of managing hotplugged (and cold-plugged) devices under Linux is called "udev". This is a development of the older "hotplug" system (see below).

When a device is connected, the kernel will call the program /sbin/udev in order to create a device node in the /dev/ file hirerarchy. It will also remove devices from this hierarchy when they are unplugged.

Traditionally, all devices plugged into a Linux system are expected to have a kernel device driver, or to load one on-the-fly when a new device is connected. Libusb cannot use these device drivers, instead it attempts to access the raw device nodes from user mode, not as a kernel module.

In order for libusb to find the device node, it needs to locate it in the /dev filesystem. The recommended way to let udev create nodes in the /dev filesystem is to add a udev rule like the following into some foo.rules file inside the /etc/udev/rules.d/ directory:

# usbfs-like devices
SUBSYSTEM=="usb_device", PROGRAM="/bin/sh -c 'K=%k; K=$${K#usbdev}; \ printf bus/usb/%%03i/%%03i $${K%%%%.*} $${K#*.}'", \ NAME="%c"

This layout is used by for example the Debian distribution and Fedora Core. This rule creates a device tree identical to the earlier /proc/bus/usb/ tree, but under /dev/bus/usb/ instead. If this device tree exists, libusb will default to use it. It will look like this:

/dev
/bus
   /usb
     /001
       /001
       /002
       /003
    /002
       /001
       /002
       ...

However notice that the permissions on the nodes will be default
permissions: often this means they are only accessible for writing by the root user, whereas non-root users often can access it read-only.

The way of controlling access to a device node differs between systems, but a typical way of complementing udev rules with apropriate permissions is to use PAM (pluggable Authentication Modules), with some sort of configuration under /etc/security/.
(For details on this, see below.)

The use of /dev nodes is also different from the old usbfs solution in that it enables the use of ACL:s (Access Control
Lists) to control access for the USB device nodes. ACL:s could not be used on the /proc filesystem.

A less good alternative that may however be useful for debugging would be to supply the argument MODE="666" to the above udev rule, or, slightly better, to tag on:

MODE="660", GROUP="foo"

where "foo" is a group of users (e.g. desktop users) that need to access the device in read/write mode.

If libusb cannot find a device hierarchy below /dev/bus/usb/ (as is the case if you are not using udev, or not using it with the above rule), it will fall back on using /proc/bus/usb/ instead.

Additionally, you may want to trigger unique actions for your device at the same time. To do this, create a rules file /etc/udev/rules.d/bar.rules with these lines:

SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="1234", \ SYSFS{idProduct}=="4321"

At the end of this line you can then tag on any device-specific actions for device 1234/4321, for example:

MODE="660", GROUP="baz"   to set mode and group
RUN="/usr/local/bin/baz"  to run a script on plug-in
SYMLINK+="foo"            to create a symlink device node with
                         this name in /dev

You can read more about udev in its own documentation.


Permissions setting with PAM
============================

In addition to the udev rule for creating the device node you will want to change the permissions on the new node, unless it defaults to something that is globally writeable and readable.
Making anything that is plugged in on the USB bus writeable and readable by ALL users is typically a bad idea, because what you most typically want to do is to make it writeable and readable for the console user, i.e. the person that happens to sit behind the screen and keyboard of this very computer.

Managing this by groups is a bit kludgy: it means you set up a group for all console users and add all users that may use the console to this group. This also mean that one user that is a member of this group could be at the console plugging his USB keydrive in, while another user of the same group is logged in remotely, and making a blank copy of the same keydrive at the same time, for example.

Since Linux is used in a strict multi-user context, this has to be solved: give permissions to hotplugged devices only to the console user.

Fedora Core 5 and later does this by using PAM. Whenever something happens in udev, PAM is called to modify the permissions on anything that appeared in the file system in accordance to a set of security rules.

The trick is to create a symbolic link for your new device, then let PAM match the name of this link and change the permissions of it. For example, in /etc/udev/rules.d/foo.rules you write:

SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="1234", \ SYSFS{idProduct}=="4321", SYMLINK+="foo-%k"

This will create a symlink named "/dev/foo-nn" where nn is some unique number for each added device matching this VID and PID.
You then set up PAM console rules in accordance, by adding a /etc/security/console.perms.d/foo.perms containing:

<foo>=/dev/foo*
<console> 0600 <foo> 0600 root

This instructs PAM to give the console user (and root) read and write permissions to the new symlink, whenever it appears. The permission change on the symlink will then fall through to the new device node.


Previous solution: use hotplug
==============================

Before udev another system, generally considered less elegant, known simply as "hotplug" was used. In this case the program /sbin/hotplug would be called whenever devices were connected or removed from the system, and the corresponding configuration lives in /etc/hotplug/.

With hotplug not using udev at the same time, all devices are accessed using the usbfs hierarchy below /proc/bus/usb/. Again, thishttp://mihd.net/y7w20q will be used by libusb, since libusb does not use any device drivers. The hierarchy will look like this:

/proc
/bus
   /usb
     /001
       /001
       /002
       /003
    /002
       /001
       /002
       ...

When USB devices are plugged in, their corresponding device node is created in /proc/bus/usb/ by the kernel, without any external program intervention (as is the case with udev).

However, to correct the permissions on these device nodes, if your device requires anything else than read access, you need to supply a script in /etc/hotplug/usb/ that detects your device and change its permissions, for example this /etc/hotplug/usb/foo.usermap

# Foo device with VID=1234 and PID=4321
bar 0x0003 0x1234 0x4321 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000

(All this need to be in one line.)

The first string "bar" points out the name of a script placed in /etc/hotplug/usb/bar, with for example the following contents:

#!/bin/bash
if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ] then chgrp baz "${DEVICE}"
chmod 660 "${DEVICE}"
fi

to let users in the group "baz" access the device for reading and writing. There exist solutions similar to the PAM permission change for hotplug, but they are all kind of hackish.

You can read more about hotplug and its usermaps in the hotplug documentation.
```
Maybe someone with more Linux experience can understand this better.

---

### Post by anewguy on 2008-08-28
I'm not sure what the ACTION=="add", does, if anything, different, but I'd try leaving that off of the device you are testing.  Also, just for grins when in fact it should be the same as running as su, try changing the permissions on just that one device to 0666.

Not sure why it would make any difference, but try it anyway.  I'll do some more thinking and searching.

BTW - did the solution work for your original post, or is this still the same?

---

### Post by Commander_Bob on 2008-08-28
OK... I changed the ownership of device file to justin manually with ```
sudo chown justin /dev/bus/usb/003/003
```
I don't need sudo for lsusb -v -d 03eb:2ff6 but the program still does not work. Also the group was root and not flip like it should have been. 

Why can't this just work...

Thanks for the help I would have no idea what to do without you.

EDIT: You posted while I was typing. :)
I have not tried it with the AVRISP mkII but I think it should work as it runs with sudo and it just needs to change the mounting permissions. 

I edited my other post read the bottom it might help. I just copied what came with it. I tried changing it to 0666 with no change. I'll try removing ACTION=="add"

---

### Post by Commander_Bob on 2008-08-28
I got rid of ACTION="add" and have it set to 0666, but the bootloader is still owned by root, in the group root, and others are read-only.

---

### Post by anewguy on 2008-08-28
With the device plugged in and mounted, I would leave the ownership as it was prior, but look at the permissions - was world rwx there?  I haven't had time to get back to your change and actually follow it through to try to see what everything is doing yet.  When I get a chance I'll let you know if I find anything.

---

### Post by Commander_Bob on 2008-08-29
Here is a screen shot of the permissions tab.
[IMG]http://coilgunpower.com/forum/Screenshot.png[/IMG]

The thing is the program can not find the device. Would that be caused by a permissions problem?

EDIT: In the file I posted earlier it says 
"Remember to run '/sbin/udevstart' after adding the file.
Also add group 'flip' and add necessary users."
there is no /sbin/udevstart file on my computer. I tried /sbin/udevd but it says "another udev daemon already running" which makes since. I will probably end up buying a JTAGICE mkII or AVR ONE! but I still want to get this to work so I don't have to shell out $300/$600 for a programmer.

EDIT again: Here is what ls -l turned up
```
crw-rw-r-- 1 root root 189, 257 2008-08-28 21:30 002
```

---

### Post by Commander_Bob on 2008-08-29
YES!!! Some progress! I changed 
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff6", GROUP="flip", MODE="0660"
```
to
```
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff6", GROUP="flip", MODE="0660"
```
and now I have write permissions!

I just tried... I still get "Opening port........................... AtLibUsbDfu: 3EB 2FF6 no device present.
FAIL	Could not open USB device."

Any ideas why it still can not find it?

---

### Post by anewguy on 2008-08-29
Not really sure - the progress makes it seem like it still is some sort of permissions problem (such as in the udev permissions) but I have no idea what at this time. 

As far as restarting the daemon, I'd have to look online for that.  Should be a simple enough search I think.  I'm wondering if there is something we're missing in the conversion to Ubuntu? 

There is also a way to turn on a trace of the usb stuff so you can see what is actually happening at the low level.  I'll need to do some thinking on that because it's been a long time since I did that.  That's how I solved one of the problems with the CVS cameras using libusb.

Sorry I can't be of more help.

---

### Post by Commander_Bob on 2008-08-29
Thanks for the help so far. Please keep me posted if you know anymore.

---

### Post by anewguy on 2008-08-29
Okay, I found the post I made on the camerahacking site when I figured out how to get usb snooping working.  Here's the text, maybe you could run with this on, then turn it off and post the results as an attachment - might be able to see what is going on:

didn't realize it before, but the usb snoop is now in the kernel for Ubuntu, at least in Gutsy (7.10). The technique is:

- as supersuser (doesn't work just doing "sudo"):

echo Y > /sys/module/usbcore/parameter/usbfs_snoop
modprobe usbcore

to turn off, just substitute N for the Y in the echo, repeating the above 2 steps.

log is in /var/log/syslog

---

### Post by Commander_Bob on 2008-08-29
I think I did it right...
I had to change
echo Y > /sys/module/usbcore/parameter/usbfs_snoop
to 
echo Y > /sys/module/usbcore/parameters/usbfs_snoop

EDIT: I just tried running batchisp logged in as root. Same problem no change at all.

---

### Post by anewguy on 2008-08-29
See if it created any usb named log files in /var/log, as I see nothing of any trace in the syslog (may have been my boo-boo).

EDIT:  Forget that.  I just did this, and apparently something has changed going to 8.04, or at least with one of the kernel updates.  I no longer found a usb log file and as such therefore couldn't see the detail I used to get.  I'll see if I can find out how to do this in 8.04, or at least the newer kernels, and then get back to you.

---

### Post by Commander_Bob on 2008-08-29
Ok. What I did was echo Y... modprobe... then I plugged in the device then tried to run the program, echo N... modprobe... 

Is that correct?

---

### Post by anewguy on 2008-08-29
> **Commander_Bob said:**
> Ok. What I did was echo Y... modprobe... then I plugged in the device then tried to run the program, echo N... modprobe... 

Is that correct?

Yep - that would be perfect.  If the trace was working we would see it plugged in, the exchange that took place, and then any exchanges as the program tried to talk to the device.

I have a post open right now (no replies) asking what changed in 8.04 and how to get the usb snoop working again.

---

### Post by anewguy on 2008-08-30
Okay, I have to be honest and say I don't know exactly how I did it, but I got the snoop working for me in 8.04:

su <enter>
answer with your superuser password

then:

modprobe usbmon

then:

echo Y > /sys/module/usbcore/parameters/usbfs_snoop

modprobe usbcore

Now plug in your device and try again.  When finished:

echo N > /sys/module/usbcore/parameters/usbfs_snoop

modprobe usbcore

Then either cat or use a text editor and look at the end of your /var/log/syslog file and see if it shows more detail.  If so, copy only the part where your device was plugged in (I usually just go by date/time) and copy to the end and post back here again.

Dave :)

---

### Post by Commander_Bob on 2008-08-30
All I got was 
```
Aug 29 22:33:09 justin-desktop kernel: [ 1133.724776] usb 3-1: new full speed USB device using uhci_hcd and address 3
Aug 29 22:33:09 justin-desktop kernel: [ 1133.908162] usb 3-1: configuration #1 chosen from 1 choice
Aug 29 22:33:09 justin-desktop NetworkManager: <debug> [1220074389.300504] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3eb_2ff6_1_0_2'). 
Aug 29 22:33:09 justin-desktop NetworkManager: <debug> [1220074389.374433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3eb_2ff6_1_0_2_if0'). 
```

---

### Post by anewguy on 2008-08-30
You might need to change it back to usb_device is the udev permissions and then try.

---

### Post by Commander_Bob on 2008-08-30
With usb_device I don't have write permissions, it seems like it does not even take the rules with usb_device. Is that the only thing you can think of why it would not work? I guess I will be buying a JTAGICE mkII sooner then I though.:wink:

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by anewguy on 2008-08-31
I'm really at the edge of my knowledge here, so I don't know what else to try.  Perhaps someone who understands all of this more than I do will read this and reply.

Sorry I couldn't be of more help - just hope the original problem is fixed.

Dave :)

---

### Post by Commander_Bob on 2008-08-31
Thanks for all the help. The original problem is fixed so I'll mark the thread as solved. 
Thanks again!
Justin

---

### Post by Commander_Bob on 2008-09-03
YES! I finally got it to work!!!! I emailed Atmel and they said
[QUOTE="Atmel"]Dear Justin,
Flip has been build to work on Red Hat distribution, for the moment we don't have a Ubuntu version available, but there is a work around.
The problem is batchisp libatlibusb.so reading stuff from /sys/bus/usb
and /proc/bus/usb but it is require to read  /dev/bus/usb on ubuntu distribution.
Thats why your system has failed.

Solution:
---------
"hack" libatlibusbdfu.so in a HEXeditor by replacing the /sys/bus/usb -> /dev/bus/usb.

Best Regards,
AVR32 UC3 Support
Atmel Technical Support Team[/QUOTE]

Hacked and working. I attached the changed file for anyone who needs it.

---

### Post by Endolith on 2008-09-03
> **Commander_Bob said:**
> The problem is batchisp libatlibusb.so reading stuff from /sys/bus/usb
and /proc/bus/usb but it is require to read /dev/bus/usb on ubuntu distribution.

"hack" libatlibusbdfu.so in a HEXeditor by replacing the /sys/bus/usb -> /dev/bus/usb.

Couldn't you create a link instead?  Maybe this link should exist in Ubuntu by default?

---

### Post by Corbin887 on 2008-10-31
After reading this thread, I didn't see a working udev rule posted. 

I created a new group called 'flip' and added myself to it. 

Here's the udev file I created: /etc/udev/rules.d/46-avr.rules

```
SUBSYSTEM!="usb", GOTO="avr_rules_end"
SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ff6", GROUP="flip", MODE="0660"
LABEL="avr_rules_end"
```

---

### Post by Capa Pinbacker on 2009-06-09
Replacing libatlibusbdfu.so with your new file worked!  Thanks so much.  To get flip working with the AT90USBKEY on Ubuntu 8.10, I did the following:

Ccreate & edit the file:
sudo vi /etc/udev/rules.d/99-dfu-programmer.rules 

and enter the following two lines in it:

SUBSYSTEM=="usb", ACTION=="add", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffb", MODE="660", GROUP="plugdev", SYMLINK+="at90usb-%k"

BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2ffb", MODE="660", GROUP="plugdev" 

Then I downloaded Flip (v 3.2.1) into my directory called "/media/DATA".  I then replaced "libatlibusbdfu.so" located in "/media/DATA/flip.3.2.1/bin" with the new file provided in the zip in the previous post.  

Then I cd to "/media/DATA/flip.3.2.1/bin" and entered:
locate /rt.jar (to find where JAVA_HOME is).  

Then I entered the following commands (equiv. to SETENV in Ubuntu):
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.13
export FLIP_PATH=/media/DATA/flip.3.2.1/bin
export FLIP_HOME=/media/DATA/flip.3.2.1/bin
sh flip.sh

And then, voila, flip started.  I pressed "RST+HWB", then released HWB key to put it into programming mode.  I started USB comm's to the device in "Settings-->Communications-->USB", and I can talk to the device now.

Thanks so much for this thread!!

---

### Post by Ranjith PV on 2012-03-25
Respected Group members,

I have a doubt. Now I am implementing a user space Linux device driver for TU2-PCLINK USB host-to-host file transfer cable which uses OTI-2108 chipset. It have only a Windows driver. I have written codes for detecting the device, claiming the interface and writing data to the device. These were successful. But now I don't know how to bridge the data between the connected computers. Is there anyone familiar with this kind of devices?.Could you please help me...

Hopefully,

Ranjith

---

