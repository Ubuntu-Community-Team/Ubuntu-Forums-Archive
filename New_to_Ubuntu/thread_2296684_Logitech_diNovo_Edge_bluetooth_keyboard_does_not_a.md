---
title: "Logitech diNovo Edge bluetooth keyboard does not awaken computer"
date: 2015-09-28
forum: New to Ubuntu
---

### Post by germ65 on 2015-09-28
The title says it all. Note that once I awaken the computer, for example clicking a USB mouse, then the keyboard is recognized OK after waiting a little bit. 

I have tried the method here:
[http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid]("http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid")
without success.

Any ideas?

---

### Post by dino99 on 2015-09-28
have you set your bios to be able to awake the system via the keyboard ?
then is there some usefull warnings/errors logged (/var/log/dmesg) about that failing event ?
if 'locomo' is installed, does that issue persist ?

---

### Post by kurt18947 on 2015-09-28
I ran into this with a logitech keyboard using one of the tiny universal receivers. I found a tip to add a udev rule specifying the USB identifiers. That works, but mine is a USB device using a propietary receiver, yours is bluetooth so the solution that worked for me may not work for you. I first attempted the fix at the above referenced web site but could not find the files referenced. I was fine up to

[B] /sys/devices/pci0000:00/  

[/B]but[B]

**0000:00:1d.0/usb5/5-0:1.0**. [/B]was nowhere to be found.

I was able to find a page detailing a udev rule enabling power management for keyboards using the logitech unifying receiver. While looking for the page I used I found this which might be more relevant since it's about bluetooth keyboards:

[http://unix.stackexchange.com/questions/144417/making-udev-rule-for-bluetooth-keyboard](http://unix.stackexchange.com/questions/144417/making-udev-rule-for-bluetooth-keyboard)
 though the model is different.

---

### Post by germ65 on 2015-09-29
Dino99, thank you for your reply.

> **dino99 said:**
> have you set your bios to be able to awake the system via the keyboard ?

Sorry, I should have been more specific. I am using a Gigabyte Brix i3. There is no such setting in the BIOS. See this, for a very similar machine:
[https://www.youtube.com/watch?v=Qs6CVncBg6M]("https://www.youtube.com/watch?v=Qs6CVncBg6M")

> **dino99 said:**
> 
then is there some usefull warnings/errors logged (/var/log/dmesg) about that failing event ? 

Nothing that jumps out. Here are some lines that refer to Bluetooth:
```
[    2.232937] usb 1-7: New USB device found, idVendor=13d3, idProduct=3394
[    2.234023] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.234837] usb 1-7: Product: RT Bluetooth Radio
[    2.235585] usb 1-7: Manufacturer: Realtek
[    2.236302] usb 1-7: SerialNumber: 00e04c000001
[    2.236959] random: lvm urandom read with 8 bits of entropy available
[    2.243287] hidraw: raw HID events driver (C) Jiri Kosina

```


> **dino99 said:**
> 
if 'locomo' is installed, does that issue persist ?

You mean lomoco, right? I I tried sudo apt-get lomoco and got E: Invalid operation lomoco.

Also, as I understand, lomoco is for Logitech USB mouse control, not for Logitech Bluetooth keyboards.

---

### Post by germ65 on 2015-09-29
kurt18947, thank you for your reply.

Could you please suggest what such a "udev" rule might be?

---

### Post by kurt18947 on 2015-09-29
> **germ65 said:**
> kurt18947, thank you for your reply.

Could you please suggest what such a "udev" rule might be?

This is the post that I used as a guide.

[http://ubuntuforums.org/showthread.php?t=1968487](http://ubuntuforums.org/showthread.php?t=1968487)

All I did was to copy/paste these two lines into a terminal using an account with sudo privileges, editing the idVendor and idProduct as appropriate.

```
sudo gedit /etc/udev/rules.d/90-keyboardwakeup.rules

```
then pasting into that blank file

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52e" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"

```

Save and restart.

I don't know if this will fix your issue or not but if not, delete the newly created file and no harm no foul. This procedure doesn't add any software or change any other system settings.

---

### Post by germ65 on 2015-09-30
Sadly, this isn't working. I found out that I already have an "udev rule" for my Bluetooth keyboard. 

Here's lsusb:
```
davide@pixie:/etc$ lsusb
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3394 IMC Networks Bluetooth
Bus 001 Device 003: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
Bus 001 Device 002: ID 03ee:6407 Mitsumi 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Then, in /etc/udev/rules.d:
```
davide@pixie:/etc/udev/rules.d$ cat 90-hid-wakeup-enable.rules 
# udev rule for USB wake-up of selected devices
#
# Mitsumi 
SUBSYSTEM=="usb", ATTRS{idVendor}=="03ee", ATTRS{idProduct}=="6407" RUN+="/usr/local/sbin/enable-wakeup $env{DEVPATH}" 
# IMC Networks Bluetooth
SUBSYSTEM=="usb", ATTRS{idVendor}=="13d3", ATTRS{idProduct}=="3394" RUN+="/usr/local/sbin/enable-wakeup $env{DEVPATH}" 

```

Notice the Mitsumi USB mouse, which works perfectly. But the keyboard (Logitech diNovo Edge) does not work. 
The Bluetooth module is a combined WiFi-BT module, and I disable WiFi. Could that be the problem?

---

### Post by kurt18947 on 2015-09-30
> The Bluetooth module is a combined WiFi-BT module, and I disable WiFi. Could that be the problem? 				

Possibly. I sort of have the opposite situation, I want to enable wifi and disable bluetooth. If I blacklist bluetooth it affects the wifi. My experience is very limited with this so my understanding is quite shallow.

---

