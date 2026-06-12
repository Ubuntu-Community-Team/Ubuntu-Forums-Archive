---
title: "Fix for TouchPack Touch Screens (Asus Eee Top, and others)"
date: 2010-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by guywithcable on 2010-07-06
[SIZE=4]Introduction[/SIZE]

After researching this problem for days, I finally found a usable fix for TouchPack screens in Ubuntu 10.04.

Before you begin, does your touch screen move the cursor to the top left corner of the screen no matter where you click? If not, then this method might not work for you. If so, then this method should fix it!

The problem is that the screen reports its coordinates using the Z and RX axes, instead of the X and Y axes, which the USB HID driver used by Linux expects. There is a fix already in the driver, but unfortunately it didn't make it into the kernel used by Ubuntu Lucid Lynx. The fix flags the device to use a "multi input quirk" mode. (source: [https://patchwork.kernel.org/patch/77055/](https://patchwork.kernel.org/patch/77055/) )

So, in order to flag the device, we must add an option to the USB HID driver. (source: [https://bugzilla.redhat.com/show_bug.cgi?id=473144](https://bugzilla.redhat.com/show_bug.cgi?id=473144) )

And we can easily do this using a modprobe script. (source: [http://ubuntuforums.org/showthread.php?t=1175001](http://ubuntuforums.org/showthread.php?t=1175001) )

[SIZE=4]Instructions[/SIZE]

Open up a terminal and follow these steps:
```
lsusb
```You should see a line similar to this:
> Bus 001 Device 006: ID **1bfd**:**1688** TouchPack Resistive Touch ScreenThe two numbers in bold after "ID" need to go into the following command:
```
echo "options usbhid quirks=0x**1bfd**:0x**1688**:0x40" | sudo tee /etc/modprobe.d/usbhid.conf
```When that command runs, you will be asked for your password, then you should see the options line repeated back to you.

Now reboot, and your touch screen should work!

[SIZE=4]Supported Devices[/SIZE]

This method was tested on an Asus Eee Top ET1602C, and should work on ET1602, and any other computer with a TouchPack screen.

---

