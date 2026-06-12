---
title: "Brightness controls on Ubuntu 13.10 and Dell Latitude 15 3000"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by davekoelmeyer-b on 2014-01-09
Hi Folks, 

I've recently acquired a new Dell Latitude 15 3000 series, and have replaced the bundled Windows 8.1 install with Ubuntu 13.10 (x86) on it. All is working incredibly well, but for the display brightness controls. Neither the hardware function keys or the Brightness slider control under Ubuntu System Settings have any effect on display brightness, even though the OSD registers hardware key presses in the case of the former.

I see from other forum posts and general searches on the web that this is a common problem that seems to afflict Ubuntu 13.10 in particular. I've tried a couple of the common recommended fixes which worked for other people but in my case they do not resolve the issue. Specifically, I attempted both of the workarounds at [http://askubuntu.com/questions/363152/brightness-issue-in-a-lenovo-thinkpad-edge-lr236w5](http://askubuntu.com/questions/363152/brightness-issue-in-a-lenovo-thinkpad-edge-lr236w5) with no change in behaviour. 

Following is some system information I've gleaned from other posts:

```
lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
    Subsystem: Dell Device 0608
    Kernel driver in use: i915
```


```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
99
99
99
/sys/class/backlight/intel_backlight
110
110
937

```


It would be awesome if one of the experts could please give me a hand with resolving this remaining problem if possible :)

Cheers, 
Dave

---

### Post by Toz on 2014-01-09
Hello and welcome to the forums.

Can you give the following a try? It will force the system to use the intel_backlight interface as the main backlight interface.

1. Create the /usr/share/X11/xorg.conf.d/20-intel.conf file with root privlidges (from a terminal window):
```
sudo -i gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```

2. Copy/paste the following code:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

3. Save the file.

4. Log out and back in again to test.



_Note:_ If you have any problems logging back in, simply go to the first virtual console by pressing Ctrl+Alt+F1, login to that console and delete the file you created:
```
sudo rm /usr/share/X11/xorg.conf.d/20-intel.conf
```
...and restart your computer:
```
sudo reboot
```

---

### Post by davekoelmeyer-b on 2014-01-09
Hi Toz, 

Thanks for your help - that did the trick! :)

Cheers,
Dave

---

### Post by davekoelmeyer-b on 2014-01-09
Hi Toz/All, 

Actually there is one small remaining quirk - post-reboot the brightness level is reset to about 1/5th total brightness (this is without the power supply plugged in by the way). The controls will continue to function however. Is there a way of setting the default brightness level or otherwise forcing the last-set brightness level to be remembered through a reboot?

[EDIT] - this appears to be normal behaviour without A/C power (while charging it will default to full brightness), so please ignore my last question - thanks again for your help.

---

