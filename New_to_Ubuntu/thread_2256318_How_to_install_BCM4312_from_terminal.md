---
title: "How to install BCM4312 from terminal?"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by remmas-sido on 2014-12-11
[SIZE=4]Hi guys
I was wondering about the method I should use for installing BCM4312 driver directly from terminal because when I open Dash and type Additional Drivers the download and the install of the driver never finish.
Thank You
[/SIZE]

---

### Post by amanchesterman on 2014-12-11
I have a similar wireless card on a laptop. The easiest and most reliable method I have found to install the driver is to start Synaptic package manager (you can install that if you haven't got it already) and get the package 'firmware-b43-installer'. Just type 'b43' in the Synaptic search bar and it will find it for you; it installs it with all necessary dependencies.
There is probably a way of installing the same package from the terminal but I don't know what it is.

---

### Post by westie457 on 2014-12-11
@ remmis-sido welcome.

With an ethernet cable plugged in, ignore any errors and warnings run the following one at a time in the terminal.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter
sudo modprobe -rfv b43
sudo modprobe b43
```
unplug the cable and try the wireless.

If nothing appears leave the cable unplugged and reboot.
It should now be working.

Thank you.

---

