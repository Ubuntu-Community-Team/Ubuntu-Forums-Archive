---
title: "suspend loses my usb"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by nutpants on 2008-04-28
i have ubuntu 8.04 and when ever i suspend my dell m1210 laptop i lose my usb devices (mouse and keyboard)
and i cannot shut down properly after words
the screen just gets vertical lines across it and may or may not reboot or shutdown after 5mins. 

is there a fix for this?

nutz

---

### Post by nutpants on 2008-04-29
found the answer for myself here

[http://ubuntuforums.org/showthread.php?t=373268](http://ubuntuforums.org/showthread.php?t=373268)

and if oyu dont want to click the link...


 Re: USB devices dead after sleep/hibernate
SOLVED! With some hints from this post (I've deliberately left the 'Google highlighting' in place), I was able to sort the 'USB devices not working after resume from hibernation' problem. It was fixed thus:
Code:

cd /etc/default
sudo cp -p acpi-support acpi-support.bak
sudo gedit acpi-support

Change MODULES="" to MODULES="ehci_hcd"

This works for me. If you have already done a hibernation/resume cycle without editing the 'acpi-support' file and you don't want to restart, simply unload and reload the 'ehci_hcd' module:
Code:

sudo modprobe -r -v ehci_hcd && sudo modprobe -v ehci_hcd

This will bring back USB functionality immediately.

Hope that helps anyone else who is stuck with it!




i lied..
it only worked once, but not since..
any help here?
"lsusb" hangs after suspend

nutz

---

### Post by nutpants on 2008-04-30
ok maybe i have it fixed now

i noticed that all power to the usb ports was gone after suspend ing

so i checked the bios

and there was a option there that stated that if the laptop was on battery the usb ports would lose power to conserve battery power..

so i figured since the laptop bios was doing "USB emulation" that when ubuntu 8.04 went into sleep mode the bios killed the power to the usb ports and when ubuntu came back it was not controlling the usb (because the bios was in "usb emulation mode") so ubuntu never tried to turn the usb ports back on, and since they were off it had no idea they were there..

or i could have been smoking crack and it was all a dream..

either way
my lost usb after suspend is gone
when i turned off the "USB emulation mode" in the bios
and now suspend works great (except the vertical lines during shutdown)
so i should say it works..

nutz

---

