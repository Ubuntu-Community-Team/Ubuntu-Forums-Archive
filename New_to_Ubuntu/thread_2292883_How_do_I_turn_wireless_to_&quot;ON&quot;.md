---
title: "How do I turn wireless to &quot;ON&quot;?"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by jrh74 on 2015-08-31
Brand new to Linux.  I have booted Ubuntu 14.04 on a USB Flash drive to my windows laptop (Lenovo yoga pro 2) to use on a trial (live??) basis.  All went well except for getting on line.  When I select the network icon at the top left I get a drop down menu on which only “VPN Connections”, “Enable Networking” and “Edit Connections” are highlighted.  “Wi-Fi Networks”, “Wi-Fi is disabled by hardware switch”, “Enable Wi-Fi” and “Connection information” are dimmed out and not selectable.  So, I selected the settings logo on the left side of the screen and selected “Network” under which, “Wireless” and “Network proxy” are the available choices.  With “Wireless” selected, an on/off toggle is shown in the off position and I am not able to toggle it to “on”.  At the bottom of the same dialog box are buttons labeled “Use as hotspot” and “Connect to a hidden network”.  Selecting “Connect to a hidden network” results only in a quick brighting (flash) of the button.  Can anyone help me move forward from here?  

John

---

### Post by grahammechanical on 2015-08-31
The message "Wi-Fi is disabled by hardware switch" is the clue.

1) The laptop allows you to power off the WiFi adapter by using a keyboard combination. You need to reverse it before loading Ubuntu.
2) Windows will allow you to power off the WiFi adapter and if that happens and Windows is shutdown, then Ubuntu cannot power on the adapter when it loads.

Ubuntu is not detecting a working wireless adapter. That is the situation.

Regards.

---

### Post by jeremy31 on 2015-09-01
Since you are testing, there is only one way to enable ```
sudo modprobe -r ideapad-laptop
``````
sudo rfkill unblock all
```

Post ```
lspci -nnk | grep -iA2 net
``` if it doesn't work

---

